# Modelo de Ameaças e Análise de Riscos

> **Propósito:** Mapear ativos, ameaças, vetores de ataque, impactos potenciais e controles mitigatórios no fluxo de Base de Conhecimento e inferência do Cherry Studio.

---

## 1. Tarefa
Elaborar a modelagem de ameaças para o recorte avaliado (RAG e integridade de contexto), detalhando no mínimo 3 riscos críticos (com obrigatoriedade de injeção de instruções e de integridade de fontes/dados), correlacionando com achados prévios (como a CVE-2026-40501 da AV1).

---

## 2. Análise do Artefato

### 2.1 Metodologia de Análise de Risco
- **Identificação do Ativo:** Componente de software, dados ou processo a ser protegido.
- **Ameaça:** Cenário adverso de violação de segurança ou integridade.
- **Vetor de Ataque:** Canal ou mecanismo pelo qual a ameaça é explorada.
- **Impacto:** Consequência sobre confidencialidade, integridade ou disponibilidade.
- **Controle Mitigatório:** Salvaguarda técnica aplicada para mitigar o risco.

### 2.2 Tabela do Modelo de Ameaças

| ID do Risco | Ativo em Risco | Ameaça Identificada | Vetor de Ataque | Impacto Potencial | Controle Mitigatório Proposto |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `RSK-INJ-01` | Prompt do Sistema e Diretrizes da Aplicação | Injeção Indireta de Prompt (*Indirect Prompt Injection*) via RAG | Documento malicioso sintético indexado na Base de Conhecimento contendo instruções adversariais ocultas | Quebra de guardrails, indução do modelo a emitir respostas inadequadas ou executar ações indevidas | Separação explícita entre dados recuperados e instruções; sanitização de texto antes da injeção no prompt; uso de prompt defensivo (`P-CIT-02`) |
| `RSK-FON-02` | Integridade das Fontes e Citações | Alucinação Factual e Citação Fraudulenta / Inexistente | Recuperação de chunks ruidosos/conflitantes associada a modelo de baixa aderência ao contexto | Desinformação do usuário, perda de confiabilidade nas decisões e risco de compliance | Validação obrigatória com JSON Schema (`fontes/esquema-saida.json`) e verificação automática de correspondência textual |
| `RSK-SEC-03` | Armazenamento Local e Chaves de API (Ref. CVE-2026-40501) | Exposição de Credenciais ou Dados Sensíveis em Logs / Histórico Local | Acesso indevido a arquivos locais do Electron ou injeção de scripts no renderizador | Comprometimento de chaves de provedores de LLM e vazamento de documentos privados | Criptografia em repouso das chaves, isolamento de contexto no Electron (*contextIsolation*) e limpeza de logs sensíveis |

---

## 3. Resultados
- **Priorização dos Riscos:**
  1. `RSK-INJ-01` — [PREENCHER SEVERIDADE: Alta / Crítica]
  2. `RSK-FON-02` — [PREENCHER SEVERIDADE: Média / Alta]
  3. `RSK-SEC-03` — [PREENCHER SEVERIDADE: Alta]
- **Eficácia dos Controles Avaliados:** [PREENCHER]
- **Recomendações Arquiteturais:** [PREENCHER]
