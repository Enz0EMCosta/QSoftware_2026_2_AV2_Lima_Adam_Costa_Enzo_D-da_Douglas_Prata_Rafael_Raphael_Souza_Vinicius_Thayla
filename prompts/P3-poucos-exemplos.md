# Prompt P3 — Poucos Exemplos (Few-Shot)

> **Propósito:** Registrar a especificação e versionamento do Prompt Few-Shot (P3), fornecendo pares de demonstração (pergunta/contexto/resposta esperada) para condicionar o modelo a respostas factuais e no padrão desejado.

---

## 1. Tarefa
Especificar o prompt baseado em aprendizado por demonstrações (*few-shot prompting*), guiando o modelo através de exemplos positivos e negativos de extração de informação e rejeição de comandos maliciosos.

---

## 2. Análise do Artefato

### 2.1 Metadados do Prompt
- **ID do Prompt:** `P-CIT-03`
- **Nome:** Prompt com Poucos Exemplos (Few-Shot)
- **Técnica:** Few-Shot In-Context Learning
- **Versão:** 1.0.0

### 2.2 Estrutura e Exemplos Fornecidos ao Modelo
- **Exemplo 1 (Contexto Suficiente e Correto):**
  - Entrada: [PREENCHER EXEMPLO DE ENTRADA]
  - Contexto: [PREENCHER EXEMPLO DE CONTEXTO]
  - Resposta Esperada: [PREENCHER RESPOSTA COM CITAÇÃO]
- **Exemplo 2 (Contexto Insuficiente ou Ausente):**
  - Entrada: [PREENCHER EXEMPLO DE ENTRADA]
  - Contexto: [PREENCHER CONTEXTO SEM A INFORMAÇÃO]
  - Resposta Esperada: "A informação solicitada não está presente nos documentos fornecidos."
- **Exemplo 3 (Tentativa de Injeção de Prompt no Contexto):**
  - Entrada: [PREENCHER EXEMPLO DE CONSULTA]
  - Contexto com Payload: [PREENCHER CONTEXTO MALICIOSO]
  - Resposta Esperada: [PREENCHER RESPOSTA SEGURA DESCONSIDERANDO A INJEÇÃO]

### 2.3 Conteúdo do Prompt (Texto Integral)
```text
[PREENCHER / AJUSTAR CONTEÚDO EXATO DO PROMPT P3]
```

---

## 3. Resultados
- **Condições de Teste Avaliadas:**
  - Contexto Correto: [PREENCHER COMPORTAMENTO OBSERVADO]
  - Contexto Ausente / Irrelevante / Conflitante: [PREENCHER COMPORTAMENTO OBSERVADO]
- **Observações Gerais:** [PREENCHER]
