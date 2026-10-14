# Matriz de Rastreabilidade Ponta a Ponta

> **Propósito:** Demonstrar o encadeamento rigoroso de rastreabilidade entre Riscos, Requisitos de Qualidade, Prompts, Casos de Teste, Evidências, Falhas Identificadas, Controles e Retestes.

---

## 1. Tarefa
Estruturar a matriz de rastreabilidade bidirecional que conecta as ameaças identificadas até a verificação da eficácia das medidas corretivas adotadas.

---

## 2. Análise do Artefato

### 2.1 Encadeamento Metodológico
$$\text{Risco} \longrightarrow \text{Requisito} \longrightarrow \text{Prompt} \longrightarrow \text{Teste} \longrightarrow \text{Evidência} \longrightarrow \text{Falha} \longrightarrow \text{Controle} \longrightarrow \text{Reteste}$$

### 2.2 Tabela de Rastreabilidade

| Risco | Requisito de Qualidade | Prompt Vinculado | Caso de Teste | Evidência | Falha Associada | Controle Mitigatório | Reteste |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `RSK-INJ-01` | `RQ-SEC-01` (Resistência a Prompt Injection) | `P-CIT-02` | `CT-INJ-01` | `capturas/CT-INJ-01.png` | `FAL-01` | `CTR-01` (Guardrail de Sanitização) | `RET-01` |
| `RSK-INJ-01` | `RQ-SEC-02` (Isolamento de Payload Indireto) | `P-CIT-02` | `CT-INJ-02` | `capturas/CT-INJ-02.png` | `FAL-02` | `CTR-02` (Delimitação Semântica de Chunks) | `RET-02` |
| `RSK-FON-02` | `RQ-CIT-01` (Factualidade e Citações de Fontes) | `P-CIT-02` | `CT-FUNC-01` | `capturas/CT-FUNC-01.png` | N/A | `CTR-03` (Prompt com Citações Obrigatórias) | N/A |
| `RSK-FON-02` | `RQ-CIT-02` (Não-alucinação em Ausência) | `P-CIT-02` | `CT-CTX-01` | `capturas/CT-CTX-01.png` | `FAL-03` | `CTR-04` (Regra Explícita de Recusa) | `RET-03` |
| `RSK-FON-02` | `RQ-CIT-03` (Tratamento de Fontes Conflitantes) | `P-CIT-02` | `CT-CTX-02` | `capturas/CT-CTX-02.png` | `FAL-04` | `CTR-05` (Diretriz de Exposição de Divergências) | [PREENCHER] |
| `RSK-FON-02` | `RQ-EST-01` (Conformidade com JSON Schema) | `P-CIT-02` | `CT-EST-01` | `capturas/CT-EST-01.png` | `FAL-05` | `CTR-06` (Validador de Saída Automatizado) | [PREENCHER] |

---

## 3. Resultados
- **Taxa de Cobertura de Rastreabilidade:** [PREENCHER %]
- **Itens com Ciclo Completo (com Reteste):** [PREENCHER - ex.: X de Y itens]
- **Observações:** [PREENCHER]
