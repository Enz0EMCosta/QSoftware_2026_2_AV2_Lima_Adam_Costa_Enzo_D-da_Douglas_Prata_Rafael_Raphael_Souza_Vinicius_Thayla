# Auditoria de Citações e Factualidade

> **Propósito:** Auditar a correspondência entre afirmações geradas pela IA e os trechos de apoio dos documentos da Base de Conhecimento, classificando o veredito factual e calculando a cobertura de citações.

---

## 1. Tarefa
Auditar de 3 a 5 afirmações extraídas de respostas do Cherry Studio, confrontando cada alegação contra a fonte indicada e o respectivo trecho documental recuperado, a fim de verificar se a citação é sustentada, parcial ou não sustentada (alucinação).

---

## 2. Análise do Artefato

### 2.1 Critérios de Avaliação do Veredito
- **Sustentada:** O trecho citado contém evidência textual direta e suficiente para embasar integralmente a afirmação gerada.
- **Parcial:** O trecho citado aborda o tema, mas a IA extrapolou ou omitiu condições relevantes. Também se classifica como parcial, para fins de rastreabilidade, uma afirmação factualmente confirmada no corpus cuja resposta não indicou fonte; registrar que a conferência factual foi feita separadamente.
- **Não Sustentada (Alucinação):** A fonte indicada não menciona a afirmação ou contradiz diretamente o texto gerado.

### 2.2 Tabela de Auditoria de Afirmações

| ID | Afirmação Gerada pela IA | Fonte Indicada | Trecho de Apoio Documental | Veredito (Sustentada / Parcial / Não Sustentada) | Justificativa |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `AUD-01` | Com apenas a política vigente, o prazo para desistir é de até 7 dias corridos após o recebimento, sem precisar justificar (resposta P1, Condição A). | Nenhuma fonte citada na resposta; conferência independente em [`DOC-01`](../base-de-conhecimento/documentos-corretos/DOC-01-politica-reembolso-v2.md). | “O cliente pode desistir da compra em até **7 (sete) dias corridos** a partir do recebimento do produto, sem precisar justificar.” | Parcial | O conteúdo factual corresponde ao DOC-01, mas como a resposta não citou fonte, o leitor não consegue verificar a afirmação a partir da resposta. |
| `AUD-02` | Com apenas a política vigente, o prazo é de até 7 dias corridos após o recebimento, sem precisar justificar (resposta P2, Condição A). | `DOC-01-politica-reembolso-v2.md` | “O cliente pode desistir da compra em até **7 (sete) dias corridos** a partir do recebimento do produto, sem precisar justificar.” | Sustentada | A fonte citada existe no corpus e o trecho confirma o prazo, o marco inicial e a ausência de justificativa. |
| `AUD-03` | Com apenas a política vigente, o prazo é de até 7 dias corridos após o recebimento, sem necessidade de justificativa (resposta P3, Condição A). | `DOC-01-politica-reembolso-v2.md` | “O cliente pode desistir da compra em até **7 (sete) dias corridos** a partir do recebimento do produto, sem precisar justificar.” | Sustentada | A paráfrase preserva o prazo e as condições registradas na fonte citada. |
| `AUD-04` | A versão 2.0, vigente desde 01/03/2026, prevê prazo de 7 dias corridos para desistência após o recebimento (resposta P1, Condição B). | `DOC-01-politica-reembolso-v2.md` | “Versão 2.0 — vigente desde 01/03/2026” e “O cliente pode desistir da compra em até **7 (sete) dias corridos** a partir do recebimento do produto”. | Sustentada | O cabeçalho e a seção de direito de arrependimento confirmam a versão, a data e o prazo; a resposta identificou a fonte. |
| `AUD-05` | A versão 1.0, publicada em 10/05/2024, previa prazo de 15 dias corridos para desistência após o recebimento (resposta P1, Condição B). | `DOC-02-politica-reembolso-v1-desatualizada.md` | “Versão 1.0 — publicada em 10/05/2024” e “O cliente pode desistir da compra em até **15 (quinze) dias corridos** a partir do recebimento do produto.” | Sustentada | O cabeçalho e a seção de direito de arrependimento confirmam a data e o prazo da versão antiga; a resposta identificou a fonte. |

---

## 3. Resultados

### 3.1 Cálculo da Cobertura e Precisão de Citações
- **Amostra:** 5 afirmações de 4 respostas do laboratório de prompts: P1/P2/P3 na Condição A e P1 na Condição B.
- **Total de Afirmações Auditadas ($N$):** 5
- **Afirmações Sustentadas ($S$):** 4
- **Afirmações Parciais ($P$):** 1
- **Afirmações Não Sustentadas ($NS$):** 0
- **Taxa de Cobertura de Citações:**
  $$\text{Cobertura} = \frac{\text{Afirmações com Fonte Citada}}{\text{Total de Afirmações Relevantes}} = \frac{4}{5} = 80\%$$
- **Precisão Factual das Citações:**
  $$\text{Precisão das citações válidas} = \frac{\text{Afirmações citadas e sustentadas}}{\text{Afirmações com fonte citada}} \times 100 = \frac{4}{4} \times 100 = 100\%$$
- **Aderência factual total da amostra:** as 5 afirmações correspondem aos documentos consultados (100%); a primeira foi classificada como parcial por não trazer citação na resposta.
- **Discussão dos achados:** as respostas examinadas distinguiram corretamente a política vigente (7 dias) da versão antiga (15 dias). A única falha de rastreabilidade nesta amostra foi a resposta P1 com apenas DOC-01, que apresentou o fato correto sem indicar sua fonte. As demais afirmações auditadas citaram documentos existentes e compatíveis com os trechos. A amostra é pequena e foi selecionada entre as respostas fornecidas no laboratório; não representa todas as respostas possíveis do sistema. Trechos foram conferidos nos arquivos do corpus, não em uma exportação independente dos chunks recuperados.
