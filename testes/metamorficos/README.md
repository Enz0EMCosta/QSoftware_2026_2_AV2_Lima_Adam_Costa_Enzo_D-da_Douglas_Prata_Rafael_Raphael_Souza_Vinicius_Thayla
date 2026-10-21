# Testes Metamórficos

> **Propósito:** Registrar os testes metamórficos, avaliando se variações na forma da pergunta (reformulações sintáticas ou traduções de idioma) preservam a equivalência lógica e factual da resposta da IA.

---

## 1. Tarefa

Aplicar transformações nas entradas de teste (relação metamórfica) sem alterar o contexto factual subjacente e verificar se a saída do Cherry Studio mantém consistência semântica e factual.

---

## 2. Análise do Artefato

### 2.1 Relações Metamórficas Definidas

- **RM-01 (Invariância por Paráfrase):** Se P1 e P2 expressam o mesmo significado sob o mesmo contexto C, a resposta factual R(P1, C) deve ser equivalente a R(P2, C).

- **RM-02 (Invariância por Tradução):** Se a consulta é traduzida para outro idioma mantendo o contexto C, a resposta deve preservar as mesmas fontes e fatos nucleares.

### 2.2 Casos de Teste Detalhados

- **CT-MET-01: Paráfrase sintática da consulta**
  - **Pergunta Original:** Qual é o prazo de garantia de uma geladeira comprada na Cereja Eletro e quais tipos de problemas essa garantia cobre?
  - **Pergunta Reformulada:** "Se eu comprar uma geladeira, por quanto tempo ela terá garantia? O que essa garantia cobre?"
  - **Contexto:** Manual de garantia v1.2, vigente desde 01/03/2026.
  - **Resposta Original vs. Reformulada:** O registro informa que o agente respondeu com garantia total de 12 meses, composta por 90 dias legais mais 9 meses contratuais, e cobertura para defeitos de fabricação que impeçam o uso normal. Teste aprovado.
  - **Resultado:** Aprovado.
  - **Evidência:** `evidencia6`.

- **CT-MET-02: Tradução da consulta para o idioma inglês**
  - **Pergunta em Português:** De acordo com o FAQ de entrega, qual é o prazo de entrega para cidades fora das capitais e quando começa a contagem?
  - **Pergunta em Inglês:** "According to the delivery FAQ, how long does delivery take to cities outside the capitals, and when does the countdown start?"
  - **Contexto:** FAQ de entrega, `DOC-03-faq-entrega.md`.
  - **Comparação de Consistência:** O agente respondeu em inglês, informando prazo de entrega de 5 a 12 dias úteis e que a contagem começa após a confirmação do pagamento. Os fatos principais foram preservados na mudança de idioma, conforme o resultado observado no registro.
  - **Resultado:** Aprovado.
  - **Evidência:** `evidencia7`.

### Observação sobre a correspondência dos testes

O registro original identifica o teste de paráfrase como T6, sobre garantia de uma geladeira, e o teste de tradução como T7, sobre prazo de entrega. 

---

## 3. Resultados

- **Violações da Relação Metamórfica:** Nenhuma inconsistência factual foi relatada nos resultados observados dos dois cenários.
- 
- **Resumo dos Resultados:**
  - CT-MET-01: resposta factual correta no registro pra ambos os casos.
  - CT-MET-02: resposta em inglês preservou o prazo de 5 a 12 dias úteis e o início da contagem após a confirmação do pagamento.
  - Status geral: resultados positivos nos cenários executados.

- **Evidências:** `testes/capturas/videncia6.png` e `testes/capturas/evidencia7.png`.

### Conclusão

Os testes metamórficos registrados indicam que o Cherry Studio preservou os fatos ao responder à pergunta sobre garantia de uma geladeira e ao receber uma consulta em inglês sobre prazos de entrega. No teste de tradução, foram mantidos o prazo de 5 a 12 dias úteis e a confirmação do pagamento como início da contagem. No teste de paráfrase, também foi respondido corretamente.
