# Testes de Saída Estruturada e Ferramentas

> **Propósito:** Avaliar a geração de respostas JSON no Cherry Studio e registrar a conferência manual de saídas frente ao esquema definido em `fontes/esquema-saida.json`.

## 1. Tarefa

Verificar se as respostas podem ser interpretadas como JSON e se atendem aos campos, tipos e valores definidos no schema. Os testes T10 e CT-EST-02 a CT-EST-04 são evidências distintas e estão identificados separadamente.

## 2. Registro dos testes

### 2.1 T10 — Saída JSON do conjunto original (`CT-EST-01`)

- **Prompt:** “Responda exclusivamente com um objeto JSON válido, sem Markdown e sem explicações. Use exatamente as chaves `prazo_dias`, `unidade`, `frete_devolucao_pago_por` e `fonte`. Preencha com os dados da política atual de reembolso. Antes de enviar, confira se o JSON pode ser interpretado por um parser. Não inclua vírgula sobrando, comentários nem texto fora do objeto.”
- **Contexto:** política de reembolso e devolução v2.0, `DOC-01-politica-reembolso-v2.md`.
- **Resposta registrada:**
  ```json
  {
    "prazo_dias": 7,
    "unidade": "corridos",
    "frete_devolucao_pago_por": "Cereja Eletro",
    "fonte": "DOC-01-politica-reembolso-v2.md"
  }
  ```
- **Resultado:** a saída foi considerada visualmente válida e continha os quatro campos solicitados. Não há registro de validação por parser ou contra o schema. O valor `"corridos"` também precisa ser comparado ao formato esperado para o campo `unidade`.
- **Evidência:** `capturas/evidencia10.png` (referência registrada no conjunto original).

### 2.2 Testes complementares do Tópico 3 (Vinícius)

- **`CT-EST-02` — Saída conforme ao schema:** foi solicitado ao Cherry Studio um JSON com `resposta`, `confianca` e `citacoes`, usando DOC-01.
  - **Prompt:** “Responda à pergunta usando apenas os documentos recuperados e devolva somente um objeto JSON válido, sem bloco Markdown, com as propriedades `resposta` (string), `confianca` (uma de `alta`, `media`, `baixa` ou `sem_informacao`) e `citacoes` (array de objetos que incluam `id_documento` e `trecho_apoio`). Pergunta: Qual é o prazo para desistir da compra?”
  - **Resposta observada:**
    ```json
    {
      "resposta": "O cliente pode desistir da compra em até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar.",
      "confianca": "alta",
      "citacoes": [
        {
          "id_documento": "DOC-01-politica-reembolso-v2.md",
          "trecho_apoio": "O cliente pode desistir da compra em até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar."
        }
      ]
    }
    ```
  - **Resultado:** JSON sintaticamente válido e considerado conforme ao schema por inspeção manual: campos obrigatórios presentes, valor de confiança permitido e citação com identificador e trecho. Não foi usado validador automatizado.
  - **Evidência:** [`CT-EST-02-json-valido.png`](../capturas/CT-EST-02-json-valido.png).

- **`CT-EST-03` — Campo obrigatório ausente:** foi solicitada intencionalmente a omissão de `citacoes`. A resposta contém `resposta` e `confianca`, mas não `citacoes`. O JSON é sintaticamente válido, porém não conforme ao schema, como solicitado.
  - **Resposta observada:**
    ```json
    {
      "resposta": "O cliente pode desistir da compra em até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar.",
      "confianca": "alta"
    }
    ```
  - **Evidência:** [`CT-EST-03-campo-citacoes-ausente.png`](../capturas/CT-EST-03-campo-citacoes-ausente.png).

- **`CT-EST-04` — Valor fora da enumeração:** foi solicitada intencionalmente uma resposta JSON com `confianca: "muito alta"`. A resposta também omitiu `citacoes`; portanto, é sintaticamente válida, mas não conforme ao schema.
  - **Resposta observada:**
    ```json
    {
      "resposta": "O cliente pode desistir da compra em até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar.",
      "confianca": "muito alta"
    }
    ```
  - **Evidência:** [`CT-EST-04-enum-invalida.png`](../capturas/CT-EST-04-enum-invalida.png).

### 2.3 Cenários não executados

- JSON com erro de sintaxe (por exemplo, vírgula sobrando ou aspas ausentes).
- Citação incompleta ou identificador de documento inexistente.
- Validação automatizada por parser e JSON Schema.

## 3. Resultados e limitações

- **T10 original (`CT-EST-01`):** 1/1 saída aparentemente válida por inspeção visual. A conformidade formal continua pendente; também é necessário confirmar se `"corridos"` atende ao formato esperado para `unidade`.
- **Bateria complementar de Vinícius (`CT-EST-02` a `CT-EST-04`):** 1/3 saídas conforme ao schema por inspeção manual. As outras duas saídas não conformes foram solicitadas intencionalmente para testar campo obrigatório ausente e valor fora da enumeração.
- **Interpretação:** a taxa de 1/3 não representa a conformidade natural do modelo, porque duas respostas foram deliberadamente solicitadas fora do schema.
- **Validação automática:** não executada. Os resultados complementares foram conferidos manualmente em relação a `fontes/esquema-saida.json`.
