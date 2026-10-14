# Ficha da Missão: Contexto Confiável

> **Propósito:** Registrar as especificações técnicas, escopo, versão de software e arquitetura avaliada na AV2 para o fluxo de Base de Conhecimento (RAG) do Cherry Studio.

---

## 1. Tarefa
Atualizar e aprofundar a ficha técnica formulada na AV1, delimitando o recorte avaliado especificamente sobre o mecanismo de Base de Conhecimento (RAG) do Cherry Studio, seus provedores de modelo, integrações e restrições operacionais.

---

## 2. Análise do Artefato

### 2.1 Identificação do Projeto e Recorte
- **Projeto Avaliado:** Cherry Studio
- **Repositório Oficial:** [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio)
- **Versão / Commit Avaliado:** [PREENCHER COMMIT / VERSÃO - ex.: v0.8.x / commit abc1234]
- **Finalidade da Aplicação:** Cliente desktop multi-provedor de LLM com suporte a chat multimodal e Base de Conhecimento local/remota (RAG).
- **Usuários-Alvo:** Desenvolvedores, pesquisadores e usuários gerais que necessitam de consultas a documentos locais via modelos de linguagem com privacidade configurável.

### 2.2 Provedores e Modelos em Teste
- **Provedor Principal:** [PREENCHER PROVEDOR - ex.: Ollama / OpenAI / Google Gemini]
- **Modelo de Linguagem (LLM):** [PREENCHER MODELO - ex.: Llama 3 / GPT-4o-mini / Gemini 1.5 Flash]
- **Modelo de Embeddings / Motor de Busca:** [PREENCHER MOTOR RAG / EMBEDDING MODEL]

### 2.3 Fluxo Avaliado
- **Módulo:** Base de Conhecimento (Knowledge Base / RAG).
- **Missões da AV2:**
  - **(D) Contexto sob Pressão:** Comportamento frente a documentos ausentes, irrelevantes e conflitantes.
  - **(B) Defesa contra Prompt Injection:** Resistência a instruções adversariais diretas e indiretas (enxertadas no corpus de documentos).

### 2.4 Fontes de Dados e Ferramentas
- **Formatos de Entrada Suportados:** [PREENCHER - ex.: Markdown (.md), PDF (.pdf), Texto plano (.txt)]
- **Ferramentas / Integrações Ativas:** [PREENCHER - ex.: Busca vetorial interna, extratores de texto, chamadas a APIs de terceiros]
- **Limitações Conhecidas:** [PREENCHER - ex.: Janela de contexto finita, chunking truncado, ausência de sanitização pré-recuperação]

---

## 3. Resultados
- **Status do Mapeamento do Recorte:** [PREENCHER - ex.: Concluído / Em validação]
- **Ambiente de Teste Padronizado:** [PREENCHER ESPECIFICAÇÕES DO AMBIENTE LOCAL / OS / MEMÓRIA]
- **Observações Operacionais:** [PREENCHER]
