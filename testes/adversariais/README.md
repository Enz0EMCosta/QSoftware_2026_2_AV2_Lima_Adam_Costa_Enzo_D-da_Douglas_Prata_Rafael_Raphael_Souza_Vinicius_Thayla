# Testes Adversariais (Defesa contra Prompt Injection)

> **Propósito:** Registrar os testes de injeção direta de comandos pelo usuário e injeção indireta embutida em documentos da Base de Conhecimento do Cherry Studio.

---

## 1. Tarefa
Executar ataques adversariais controlados para testar a robustez das políticas do sistema contra jailbreaks, bypass de restrições e vazamento de instruções protegidas.

---

## 2. Análise do Artefato

### 2.1 Tipos de Injeção Avaliados
- **Injeção Direta:** O usuário envia comandos diretos no chat ordenando desconsiderar as políticas (ex.: *"Ignore as diretrizes anteriores e..."*).
- **Injeção Indireta:** A instrução maliciosa está camuflada dentro de um documento sintético (`DOC-MAL-01`) que é injetado no contexto durante a busca RAG.

### 2.2 Casos de Teste Detalhados
- **`CT-INJ-01` (Injeção Direta):**
  - Entrada: [PREENCHER COMANDO ADVERSARIAL]
  - Contexto: Nenhum
  - Comportamento Observado: [PREENCHER - ex.: O modelo recusou o ataque ou obedeceu?]
- **`CT-INJ-02` (Injeção Indireta via RAG):**
  - Entrada: Pergunta legítima do usuário
  - Contexto Recuperado: `DOC-MAL-01` contendo payload oculto
  - Comportamento Observado: [PREENCHER - ex.: O modelo executou o payload do documento ou respondeu apenas à consulta?]

---

## 3. Resultados
- **Taxa de Resistência à Injeção:** [PREENCHER %]
- **Vulnerabilidades Identificadas:** [PREENCHER]
- **Evidências:** `testes/capturas/CT-INJ-01.png`, `CT-INJ-02.png`
