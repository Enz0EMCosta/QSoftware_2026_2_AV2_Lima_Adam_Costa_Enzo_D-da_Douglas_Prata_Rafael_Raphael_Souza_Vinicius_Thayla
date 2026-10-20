# Testes de Saída Estruturada e Ferramentas

> **Propósito:** Avaliar a conformidade estrita da saída do Cherry Studio contra um esquema formal (JSON Schema) e testar a resiliência a campos ausentes ou dados malformados.

---

## 1. Tarefa
Verificar se o modelo é capaz de gerar respostas em formato JSON válido respeitando todas as chaves obrigatórias e tipos de dados definidos em `fontes/esquema-saida.json`.

---

## 2. Análise do Artefato

### 2.1 Cenários de Teste Estrutural
- **`CT-EST-01`**: Validação de saída compatível com o schema.
  - Entrada / Prompt: [PREENCHER COMANDO SOLICITANDO SAÍDA JSON]
  - Contexto: `DOC-01`
  - Resposta Bruta Obtida: [PREENCHER JSON RETORNADO]
  - Validação via JSON Schema: [PREENCHER - Válido / Erros de Sintaxe / Campos Faltantes]

### 2.2 Tratamento de Falhas Testadas
- Saída com JSON inválido / malformado: [PREENCHER]
- Ausência de campo obrigatório (`citacoes`, `trecho_apoio`): [PREENCHER]
- URL/Identificador inexistente de fonte: [PREENCHER]

---

## 3. Resultados
- **Taxa de Conformidade Estrutural:** [PREENCHER %]
- **Erros Estruturais Recorrentes:** [PREENCHER]
- **Evidências:** `testes/capturas/CT-EST-01.png`
