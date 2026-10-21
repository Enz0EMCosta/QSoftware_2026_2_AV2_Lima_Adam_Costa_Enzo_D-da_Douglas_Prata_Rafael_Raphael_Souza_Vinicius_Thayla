# Plano de Melhoria

> **Propósito:** Definir o plano de ação corretivo e preventivo focado nos 3 achados mais importantes da avaliação do Cherry Studio.

---

## 1. Tarefa
Estruturar o plano de intervenção técnica para tratar as causas raízes das três falhas de maior impacto identificadas, estabelecendo responsáveis, ações mitigatórias, prioridades e critérios de aceitação para reteste.

---

## 2. Análise do Artefato

### 2.1 Os 3 Achados Mais Importantes

A partir das cinco falhas e fragilidades catalogadas em [`falhas-classificadas.md`](./falhas-classificadas.md), foram selecionados os **três achados de severidade alta** (`FAL-01`, `FAL-02` e `FAL-03`) para compor o plano prioritário de melhoria do fluxo de Base de Conhecimento (RAG) no Cherry Studio:

| ID | Achado Priorizado | Causa Provável | Ação de Melhoria | Responsável | Prioridade | Evidência Esperada | Reteste Vinculado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `ACH-01` | **Quebra de rastreabilidade por ausência de citação em pergunta direta (`FAL-01`)** | O prompt direto (`P1`) não exige citação explícita e o prompt de sistema padrão do assistente no Cherry Studio não impõe a obrigatoriedade de identificar o arquivo (`id_documento`) e o trecho literal de apoio em toda resposta baseada no RAG. | Incorporar as regras de citação obrigatória de `P2`/`P3` diretamente no **Prompt de Sistema** fixo do assistente no Cherry Studio, exigindo sempre o formato `Fonte: <id_documento>` + trecho de apoio, mesmo quando o usuário enviar uma pergunta curta e direta (`P1`). | Rafael Prata | **P1 (Alta)** | Captura de tela de nova execução da pergunta direta (`P1`) na Condição A (`DOC-01`) exibindo explicitamente `Fonte: DOC-01-politica-reembolso-v2.md` e elevando a cobertura de citações de 80% para 100%. | `RET-01` (sobre `LAB-P1-CORRETO` / `AUD-01`) |
| `ACH-02` | **Saídas JSON sintaticamente válidas que violam o Schema sem bloqueio (`FAL-02`)** | O fluxo de chat do Cherry Studio apenas exibe o texto gerado pelo LLM sem aplicar validação estrutural pós-geração contra o JSON Schema (`fontes/esquema-saida.json`), permitindo a passagem de objetos sem o campo obrigatório `citacoes` (`CT-EST-03`) ou com valores fora do enum de `confianca` (`CT-EST-04`). | Implementar e executar a camada de validação automatizada em Python (`fontes/validador/`) com `jsonschema.validate()` sobre as saídas JSON antes de seu consumo, combinada a instruções rígidas de schema e exemplos (*few-shot*, `P3`) para rejeitar automaticamente respostas com campos ausentes ou enums inválidos. | Vinicius Souza | **P1 (Alta)** | Log de execução do validador aprovando `CT-EST-02` (`[SUCESSO]`) e barrando explicitamente as saídas não conformes `CT-EST-03` e `CT-EST-04` (`[ERRO DE VALIDAÇÃO]`), mais padronização do campo `unidade` em `CT-EST-01`. | `RET-02` (sobre `CT-EST-01` a `CT-EST-04`) |
| `ACH-03` | **Exposição da fronteira de confiança do RAG a documentos contaminados (`FAL-03`)** | Os *chunks* recuperados da Base de Conhecimento são concatenados ao prompt na Etapa 4 do fluxo sem delimitação estrutural nativa entre dado passivo e instrução de comando, enquanto o documento malicioso `DOC-05-comunicado-promocao.md` (contendo a ordem `CANARIO-INJ-742`) permanece indexado na base ativa. | (1) Isolar os trechos recuperados com delimitadores explícitos (ex.: `<contexto_nao_confiavel>...</contexto_nao_confiavel>`) e cláusula de bloqueio no prompt de sistema tratando todo documento como dado passivo; (2) Realizar higienização do índice removendo ou colocando em quarentena documentos contaminados (`DOC-05`); e (3) Ampliar o teste de proteção de instruções internas (`CT-INJ-01`) em base vazia. | Raphael Portella e Thayla Figueiredo | **P1 (Alta)** | Registro de higienização da base de conhecimento (remoção de `DOC-05` do índice produtivo) e evidência de reteste de `CT-INJ-01` e `CT-INJ-02` confirmando que comandos injetados jamais alteram o comportamento do sistema nem vazam o prompt interno. | `RET-03` (sobre `CT-INJ-01` e `CT-INJ-02`) |

---

### 2.2 Detalhamento Técnico dos Planos de Ação

#### Achado 1: Quebra de Rastreabilidade por Ausência de Citação em Pergunta Direta (`FAL-01`)
- **Causa Provável:** No Laboratório de Prompts (Tópico 2) e na Auditoria de Fontes (Tópico 3, `AUD-01`), observou-se que os prompts `P2` (estruturado) e `P3` (*few-shot*) alcançaram 100% de citação porque continham a regra explícita na mensagem do usuário, ao passo que a pergunta direta (`P1`: *"Qual é o prazo para desistir da compra?"*) respondeu o fato correto (7 dias corridos), mas omitiu a fonte na Condição A, derrubando a cobertura de citações para 80% (4/5).
- **Ação Proposta:** Transferir a responsabilidade de exigir citações da mensagem do usuário para o **Prompt de Sistema** do Agente no Cherry Studio, tornando obrigatório informar o identificador do documento (`DOC-XX`) e o trecho literal de apoio em qualquer resposta, além de declarar `"Não encontrei informação suficiente nos documentos da base"` quando não houver lastro documental (mitigando também `FAL-04` e `FAL-05`).
- **Responsável:** Rafael Prata (laboratório de prompts).
- **Prioridade:** P1 (Alta).
- **Evidência Esperada:** Resposta do modelo à pergunta crua `P1` trazendo a citação `DOC-01-politica-reembolso-v2.md` e o trecho correspondente sem necessidade de o usuário pedir a fonte no prompt da conversa.
- **Reteste Vinculado:** `RET-01` (reexecução de `P1` na Condição A e verificação em `AUD-01`).

#### Achado 2: Saídas JSON Sintaticamente Válidas que Violam o Schema sem Bloqueio (`FAL-02`)
- **Causa Provável:** Os testes `CT-EST-03` e `CT-EST-04` demonstraram que um modelo de linguagem pode produzir um JSON 100% válido sintaticamente (aceito por `json.loads`), mas que viola regras de negócio críticas do contrato (`fontes/esquema-saida.json`), como omitir o array obrigatório `citacoes` ou preencher `"confianca": "muito alta"` fora da enumeração `["alta", "media", "baixa", "sem_informacao"]`. Como o Cherry Studio funciona como interface de chat e não valida JSON Schema nativamente, a inspeção ocorreu apenas de forma manual.
- **Ação Proposta:** Adotar validação automatizada pós-geração por meio do script validador (`fontes/validador/README.md`) baseado em `jsonschema`, rejeitando qualquer resposta estruturada que viole campos obrigatórios (`resposta`, `confianca`, `citacoes`) ou tipos enumerados, e padronizar no prompt estruturado os domínios exatos esperados (incluindo o formato de `unidade` em `CT-EST-01`).
- **Responsável:** Vinicius Souza (auditoria e saída estruturada).
- **Prioridade:** P1 (Alta).
- **Evidência Esperada:** Saída do validador acusando aprovação em `CT-EST-02` e bloqueio imediato das violações intencionais `CT-EST-03` e `CT-EST-04`, impedindo o uso de JSON fora do contrato.
- **Reteste Vinculado:** `RET-02` (validação sobre `CT-EST-01` a `CT-EST-04`).

#### Achado 3: Exposição da Fronteira de Confiança do RAG a Documentos Contaminados (`FAL-03`)
- **Causa Provável:** Conforme identificado na Etapa 4 do Fluxo de Dados (Tópico 1) e no risco `R1`/`RSK-INJ-01` do Modelo de Ameaças (Tópico 4), a Base de Conhecimento insere trechos de documentos externos diretamente no contexto do modelo sem distinção nativa entre dado e comando. Embora o Gemini Flash-Lite tenha resistido ao canário `CANARIO-INJ-742` em `CT-INJ-02` quando guiado pelo prompt estruturado `P-CIT-02`, manter documentos não sanitizados na base e depender exclusivamente do prompt da sessão representa um risco alto de segurança.
- **Ação Proposta:** Aplicar defesa em profundidade: (1) configurar no prompt de sistema do assistente o encapsulamento semântico do contexto recuperado e a diretriz imutável de jamais executar ordens oriundas de documentos da base ou revelar instruções internas; (2) instituir curadoria/remoção do documento contaminado (`DOC-05-comunicado-promocao.md`) do índice após a detecção; e (3) manter o Cherry Studio atualizado na versão `v2.0.13` ou superior para preservar a mitigação da `CVE-2026-40501` (`R4`/`RSK-SEC-03`).
- **Responsável:** Raphael Portella e Thayla Figueiredo.
- **Prioridade:** P1 (Alta).
- **Evidência Esperada:** Confirmação da neutralização do payload indireto mesmo sob consulta simples, remoção do documento malicioso do índice ativo e não vazamento de instruções de sistema em `CT-INJ-01`.
- **Reteste Vinculado:** `RET-03` (reavaliação de `CT-INJ-01` e `CT-INJ-02`).

---

## 3. Resultados
- **Status do Plano de Melhoria:** Estruturado e vinculado aos achados empíricos dos Tópicos 1 a 6 (`ACH-01`, `ACH-02` e `ACH-03`).
- **Impacto Esperado na Confiabilidade:** Elevação da cobertura de citações para 100% mesmo em perguntas diretas (`P1`), bloqueio de 100% das saídas JSON fora do schema antes do consumo por sistemas externos e redução da superfície de ataque de injeção direta e indireta no fluxo RAG.
