
# Testes de Contexto e Fontes

> **Propósito:** Registrar os testes de robustez frente a perturbações no contexto: documentos ausentes, irrelevantes ou conflitantes.

---

## 1. Tarefa

Avaliar a capacidade do sistema RAG de lidar com ruído, recusa graciosa de respostas sem base documental e resolução de ambiguidades/conflitos.

---

## 2. Análise do Artefato

### 2.1 Casos de Teste Detalhados

- **`CT-CTX-01`**: Pressão com Documento Irrelevante (`DOC-03`).
  - **Entrada:** Pergunta sobre o prazo estimado para uma entrega em uma capital, solicitando que a resposta seja baseada no FAQ de entrega, sem utilizar a política de reembolso, e que o documento utilizado seja citado.
  - **Contexto:** FAQ de entrega (`DOC-03-faq-entrega.md`). O cenário executado verificou a recuperação do prazo de entrega, mas não reproduziu integralmente o critério original de ausência de suporte diante de contexto irrelevante.
  - **Saída Observada:** O agente informou o prazo estimado de 2 a 5 dias úteis e identificou `DOC-03-faq-entrega.md` como fonte. Não mencionou que a contagem começa após a confirmação do pagamento. Essa omissão foi registrada como limitação, não como falha do teste.
  - **Evidência:** `evidencia4`.
  - **Status:** Aprovado no cenário executado, com cobertura parcial do cenário original.

- **`CT-CTX-02`**: Pressão com Documentos Conflitantes (`DOC-02` vs. `DOC-01`).
  - **Entrada:** Solicitação para comparar as informações de um documento antigo, que estabelece prazo de arrependimento de 15 dias e reembolso em até 30 dias úteis por voucher ou pagamento original, com a política de reembolso v2.0, identificando a versão atual e justificando a escolha pela versão e data de vigência.
  - **Contexto:** Política antiga v1.0, datada de 10/05/2024 (`DOC-02`), e política de reembolso e devolução v2.0, vigente desde 01/03/2026 (`DOC-01`).
  - **Saída Observada:** O agente comparou corretamente as versões, identificando a v1.0 com prazo de arrependimento de 15 dias e reembolso em até 30 dias úteis, e a v2.0 com prazo de arrependimento de 7 dias corridos e reembolso em até 10 dias úteis após a aprovação da devolução. Identificou a v2.0 como a versão atual e apresentou as datas das versões.
  - **Evidência:** `evidencia5`.
  - **Status:** Aprovado no cenário executado. 
---

## 3. Resultados

- **Comportamento em Ausência de Suporte:** O `CT-CTX-01` informou o prazo estimado de entrega de 2 a 5 dias úteis e identificou o FAQ de entrega (`DOC-03-faq-entrega.md`) como fonte. Foi observada uma omissão sobre o início da contagem do prazo, indicando uma oportunidade de melhoria na completude da resposta.

- **Comportamento sob Contradição:** No `CT-CTX-02`, o agente distinguiu corretamente as versões antiga e atual da política, comparou os prazos e identificou a v2.0 como vigente com base na versão e na data informadas. O resultado registrado demonstra resolução adequada do conflito entre os documentos no cenário executado.

- **Taxa de Aprovação Registrada:** 100% (2 de 2 testes aprovados nos cenários executados), conforme a Matriz Geral de Casos de Teste (AV2). 

- **Evidências:** `testes/capturas/evidencia4.png`, `testes/capturas/evidencia5.png`.

- **Observações:**
  - O `CT-CTX-01` apresentou cobertura parcial do critério original de ausência de suporte documental.
  - O `CT-CTX-02` demonstrou que o agente identificou a política v2.0 como atual e comparou adequadamente as informações conflitantes.
  - Para melhorar a cobertura, deve-se complementar o `CT-CTX-01` com uma consulta cuja resposta não esteja disponível na base e verificar se o sistema declara explicitamente a ausência de informação suficiente, sem inventar dados. FAZER TESTE
