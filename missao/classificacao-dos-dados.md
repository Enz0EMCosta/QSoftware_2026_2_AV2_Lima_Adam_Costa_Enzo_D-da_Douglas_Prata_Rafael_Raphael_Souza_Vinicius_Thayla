# Classificação dos Dados de Teste

> **Propósito:** Classificar e auditar a natureza e sensibilidade dos dados utilizados nos ensaios de teste da AV2, garantindo conformidade com a LGPD e prevenindo o vazamento de credenciais ou dados pessoais reais.

---

## 1. Tarefa
Categorizar rigorosamente cada insumo de dados empregado nos testes de RAG e prompt injection de acordo com níveis de sensibilidade (Público, Sintético, Interno ou Não Permitido), garantindo a ausência total de credenciais e PII (*Personally Identifiable Information*).

---

## 2. Análise do Artefato

### 2.1 Categorias de Classificação
- **Público:** Dados acessíveis publicamente sem restrições legais ou de confidencialidade (ex.: documentações oficiais abertas, normas públicas).
- **Sintético:** Dados gerados artificialmente para simulação de cenários de teste, sem vínculo com entidades reais (ex.: políticas de reembolso fictícias, nomes inventados).
- **Interno:** Dados de configuração de ambiente ou artefatos próprios do projeto acadêmico sem exposição de segredos.
- **Não Permitido:** Dados estritamente proibidos nos testes (chaves de API reais, senhas, dados biométricos, CPFs reais, dados bancários).

### 2.2 Tabela de Classificação dos Dados Utilizados

| ID do Dado | Descrição do Dado | Categoria | Finalidade no Teste | Justificativa / Salvaguardas |
| :--- | :--- | :--- | :--- | :--- |
| `DAT-01` | Documentos da Base de Conhecimento (Corretos) | Sintético | Teste de recuperação factual em RAG | Textos de procedimentos fictícios criados exclusivamente para a atividade |
| `DAT-02` | Documentos Distratores (Irrelevantes) | Sintético / Público | Teste de ruído e pressão de contexto | Dados sem relevância temática ao domínio consultado |
| `DAT-03` | Documentos Conflitantes | Sintético | Teste de contradição de fontes e veredito | Versões divergentes de regulamentos fictícios |
| `DAT-04` | Payloads de Injeção de Prompt (Maliciosos) | Sintético | Teste adversarial de injeção direta/indireta | Comandos inofensivos simulando quebra de diretrizes (sem exploits reais de sistema) |
| `DAT-05` | Chaves de Provedores de LLM | Não Permitido | Acesso às APIs de inferência | Devem ser injetadas exclusivamente via variáveis locais, nunca commitadas |
| `DAT-06` | Dados Pessoais de Integrantes / Usuários | Não Permitido | Não aplicável | Apenas identificação acadêmica básica no README/Equipe; zero PII sensível |

---

## 3. Resultados
- **Auditoria de Conformidade:** [PREENCHER - ex.: 100% dos dados submetidos à Base de Conhecimento são sintéticos ou públicos]
- **Detecção de Chaves/Credenciais no Repositório:** [PREENCHER - ex.: Nenhuma credencial identificada via verificação estática]
- **Observações:** [PREENCHER]
