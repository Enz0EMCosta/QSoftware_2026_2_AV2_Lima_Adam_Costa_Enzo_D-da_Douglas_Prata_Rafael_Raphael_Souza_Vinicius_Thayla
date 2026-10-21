
# Testes Funcionais de RAG

> **Propósito:** Detalhar a execução dos testes funcionais básicos de recuperação e síntese de respostas na Base de Conhecimento do Cherry Studio.

---

## 1. Tarefa

Verificar se o mecanismo de RAG recupera adequadamente os chunks corretos e gera respostas factuais alinhadas com a base documental informada.

---

## 2. Análise do Artefato

### 2.1 Casos de Teste Detalhados

- **`CT-FUNC-01`**: Recuperação simples a partir da política vigente (`DOC-01`).
  - **Entrada:** Pergunta sobre o prazo para desistir de uma compra após receber o produto, solicitando a indicação de dias úteis ou corridos e do documento que fundamenta a resposta.
  - **Contexto:** Política de reembolso e devolução v2.0, vigente desde 01/03/2026 (`DOC-01-politica-reembolso-v2.md`).
  - **Saída Observada:** O agente informou que o prazo para desistir da compra é de 7 dias corridos após o recebimento do produto, identificou `DOC-01-politica-reembolso-v2.md` e apresentou uma referência de citação.
  - **Evidência:** `evidencia1`.
  - **Status:** Aprovado.

- **`CT-FUNC-02`**: Recuperação de informações sobre as condições de devolução (`DOC-01`).
  - **Entrada:** Pergunta sobre quem paga o frete da devolução por arrependimento e quais são as condições para enviar o produto.
  - **Contexto:** Política de reembolso e devolução v2.0 (`DOC-01-politica-reembolso-v2.md`).
  - **Saída Observada:** O agente informou que a Cereja Eletro paga o frete da devolução e que o produto deve ser enviado na embalagem original, acompanhado dos acessórios e da nota fiscal. Também apresentou uma referência de citação.
  - **Evidência:** `evidencia2`.
  - **Status:** Aprovado.

- **`CT-FUNC-03`**: Recuperação de informações sobre alteração do endereço de entrega (`DOC-03`).
  - **Entrada:** Pergunta sobre a possibilidade de corrigir o endereço informado incorretamente após a compra, incluindo as condições e o local para realizar a alteração.
  - **Contexto:** FAQ de entrega (`DOC-03-faq-entrega.md`).
  - **Saída Observada:** O agente informou que o endereço pode ser alterado antes da expedição do pedido, por meio da seção “Meus pedidos”.
  - **Evidência:** `evidencia3`.
  - **Status:** Aprovado.

---

## 3. Resultados

- **Taxa de Sucesso dos Testes Funcionais:** 100% (3 de 3 testes aprovados no registro original).
- **Evidências:** `testes/capturas/evidencia1.png`, `testes/capturas/evidencia2.png` e `testes/capturas/evidencia3.png`.
- **Observações:**
  - O `CT-FUNC-01` confirmou a recuperação do prazo de arrependimento de 7 dias corridos e a identificação da política vigente.
  - O `CT-FUNC-02` confirmou a recuperação das condições de devolução, incluindo o pagamento do frete pela Cereja Eletro e a exigência de embalagem original, acessórios e nota fiscal.
  - O `CT-FUNC-03` confirmou a recuperação das regras para alteração do endereço antes da expedição, com indicação da seção “Meus pedidos”.
