# Testes de Saída Estruturada e Ferramentas

> **Propósito:** Avaliar a conformidade estrita da saída do Cherry Studio contra um esquema formal (JSON Schema) e testar a resiliência a campos ausentes ou dados malformados.

---

## 1. Tarefa

Verificar se o modelo é capaz de gerar respostas em formato JSON válido respeitando todas as chaves obrigatórias e tipos de dados definidos em `fontes/esquema-saida.json`.

---

## 2. Análise do Artefato

### 2.1 Cenários de Teste Estrutural

- **`CT-EST-01`**: Validação de saída compatível com o schema.
  - **Entrada / Prompt:**
    ```text
    Responda exclusivamente com um objeto JSON válido, sem Markdown e sem explicações. Use exatamente as chaves "prazo_dias", "unidade", "frete_devolucao_pago_por" e "fonte". Preencha com os dados da política atual de reembolso. Antes de enviar, confira se o JSON pode ser interpretado por um parser. Não inclua vírgula sobrando, comentários nem texto fora do objeto.
    ```
  - **Contexto:** `DOC-01-politica-reembolso-v2.md` — política de reembolso e devolução v2.0.
  - **Resposta Bruta Obtida:**
    ```json
    {
      "prazo_dias": 7,
      "unidade": "corridos",
      "frete_devolucao_pago_por": "Cereja Eletro",
      "fonte": "DOC-01-politica-reembolso-v2.md"
    }
    ```
  - **Validação via JSON Schema:** Aprovado na inspeção visual, com validação formal pendente. A resposta contém os quatro campos solicitados, utiliza sintaxe JSON aparentemente correta e não apresenta texto adicional fora do objeto. Entretanto, o registro não comprova a execução de um parser JSON nem a validação contra `fontes/esquema-saida.json`. Também é necessário confirmar se o valor `"corridos"` atende ao schema, pois o registro observa que foi utilizado em vez de `"dias corridos"`.

### 2.2 Tratamento de Falhas Testadas

- **Saída com JSON inválido / malformado:** Não testada no registro. O teste T10 avaliou uma resposta aparentemente válida, sem provocar deliberadamente erros de sintaxe, vírgulas sobrando, aspas ausentes ou texto adicional. Portanto, não há evidências suficientes para avaliar o comportamento do modelo diante de JSON malformado.

- **Ausência de campo obrigatório (`citacoes`, `trecho_apoio`):** Não testada no registro. A resposta de T10 contém os campos `prazo_dias`, `unidade`, `frete_devolucao_pago_por` e `fonte`. Não há evidência de que os campos `citacoes` e `trecho_apoio` tenham sido removidos intencionalmente, nem de como o modelo reage à ausência deles. A obrigatoriedade desses campos deve ser confirmada no arquivo `fontes/esquema-saida.json`.

- **URL/Identificador inexistente de fonte:** Não testado no registro. O T10 retornou o identificador `DOC-01-politica-reembolso-v2.md`, mas não há evidência de que tenha sido fornecida uma fonte inexistente ou de que o identificador retornado tenha sido validado automaticamente.

---

## 3. Resultados

- **Taxa de Conformidade Estrutural:** 1 de 1 saída aparentemente válida na inspeção visual (100% de aprovação visual). A conformidade formal com o JSON Schema permanece pendente, pois não há registro de validação automatizada por parser e esquema.(fazer teste automatizado)

- **Erros Estruturais Recorrentes:** Não foram identificados erros de sintaxe na saída registrada. Foi observada uma diferença no valor do campo `unidade`: o modelo retornou `"corridos"` em vez de `"dias corridos"`. É necessário confirmar se essa diferença é permitida pelo schema. Não há dados suficientes para identificar erros recorrentes ou avaliar campos ausentes e identificadores de fontes inexistentes. (fazer teste automatizado)

- **Evidências:** `testes/capturas/evidencia10`

### Conclusão

O teste CT-EST-01 apresentou resultado positivo na inspeção visual: o modelo retornou um objeto JSON com os quatro campos solicitados e valores coerentes com a política vigente. Falta fazer validação.
