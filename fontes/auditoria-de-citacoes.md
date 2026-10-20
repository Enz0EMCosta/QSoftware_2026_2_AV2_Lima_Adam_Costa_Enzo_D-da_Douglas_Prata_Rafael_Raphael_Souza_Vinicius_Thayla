# Auditoria de Citações e Factualidade

> **Propósito:** Auditar a correspondência entre afirmações geradas pela IA e os trechos de apoio dos documentos da Base de Conhecimento, classificando o veredito factual e calculando a cobertura de citações.

---

## 1. Tarefa
Auditar de 3 a 5 afirmações extraídas de respostas do Cherry Studio, confrontando cada alegação contra a fonte indicada e o respectivo trecho documental recuperado, a fim de verificar se a citação é sustentada, parcial ou não sustentada (alucinação).

---

## 2. Análise do Artefato

### 2.1 Critérios de Avaliação do Veredito
- **Sustentada:** O trecho citado contém evidência textual direta e suficiente para embasar integralmente a afirmação gerada.
- **Parcial:** O trecho citado aborda o tema, mas a IA extrapolou ou omitiu condições relevantes.
- **Não Sustentada (Alucinação):** A fonte indicada não menciona a afirmação ou contradiz diretamente o texto gerado.

### 2.2 Tabela de Auditoria de Afirmações

| ID | Afirmação Gerada pela IA | Fonte Indicada | Trecho de Apoio Documental | Veredito (Sustentada / Parcial / Não Sustentada) | Justificativa |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `AUD-01` | [PREENCHER AFIRMAÇÃO 1] | `DOC-01` | "[PREENCHER TRECHO EXATO EXTRAÍDO]" | [PREENCHER] | [PREENCHER] |
| `AUD-02` | [PREENCHER AFIRMAÇÃO 2] | `DOC-01` | "[PREENCHER TRECHO EXATO EXTRAÍDO]" | [PREENCHER] | [PREENCHER] |
| `AUD-03` | [PREENCHER AFIRMAÇÃO 3] | `DOC-04` | "[PREENCHER TRECHO EXATO EXTRAÍDO]" | [PREENCHER] | [PREENCHER] |
| `AUD-04` | [PREENCHER AFIRMAÇÃO 4] | [PREENCHER] | "[PREENCHER TRECHO EXATO EXTRAÍDO]" | [PREENCHER] | [PREENCHER] |
| `AUD-05` | [PREENCHER AFIRMAÇÃO 5] | [PREENCHER] | "[PREENCHER TRECHO EXATO EXTRAÍDO]" | [PREENCHER] | [PREENCHER] |

---

## 3. Resultados

### 3.1 Cálculo da Cobertura e Precisão de Citações
- **Total de Afirmações Auditadas ($N$):** [PREENCHER]
- **Afirmações Sustentadas ($S$):** [PREENCHER]
- **Afirmações Parciais ($P$):** [PREENCHER]
- **Afirmações Não Sustentadas ($NS$):** [PREENCHER]
- **Taxa de Cobertura de Citações:**
  $$\text{Cobertura} = \frac{\text{Afirmações com Fonte Citada}}{\text{Total de Afirmações Relevantes}} = \text{[PREENCHER \%]}$$
- **Precisão Factual das Citações:**
  $$\text{Precisão} = \frac{S}{N} \times 100 = \text{[PREENCHER \%]}$$
- **Discussão dos Achados:** [PREENCHER]
