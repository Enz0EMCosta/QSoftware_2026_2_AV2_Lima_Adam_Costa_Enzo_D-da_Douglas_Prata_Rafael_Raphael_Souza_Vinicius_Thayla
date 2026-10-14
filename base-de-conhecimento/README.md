# Base de Conhecimento Sintética (RAG)

> **Propósito:** Armazenar e documentar os conjuntos de documentos sintéticos/fictícios indexados na Base de Conhecimento do Cherry Studio para os ensaios de recuperação de informação, pressão de contexto e segurança adversarial.

---

## 1. Tarefa
Estruturar corpus de documentos controlados para alimentar o mecanismo RAG do Cherry Studio, permitindo avaliar a precisão da recuperação factual, o impacto de ruído informacional e a suscetibilidade a injeções indiretas.

---

## 2. Análise do Artefato

### 2.1 Organização das Subpastas
Os documentos estão particionados em quatro categorias experimentais:

| Pasta | Descrição e Finalidade | Tipo de Dado |
| :--- | :--- | :--- |
| [`documentos-corretos/`](./documentos-corretos/) | Documentos sintéticos factuais contendo as regras oficiais e verdadeiras da base fictícia. Utilizados para avaliar respostas precisas e citações corretas. | Sintético |
| [`documentos-irrelevantes/`](./documentos-irrelevantes/) | Documentos contendo ruído temático ou assuntos totalmente desconexos. Utilizados para avaliar a capacidade do RAG de filtrar distrações. | Sintético / Público |
| [`documentos-conflitantes/`](./documentos-conflitantes/) | Documentos que contradizem intencionalmente as regras dos documentos corretos (ex.: prazos e valores alterados). Utilizados para avaliar a resolução de ambiguidades. | Sintético |
| [`documentos-maliciosos/`](./documentos-maliciosos/) | Documentos contendo comandos embutidos de *Prompt Injection* indireta (instruções camufladas de quebra de diretrizes do sistema). | Sintético |

### 2.2 Inventário dos Documentos da Base de Conhecimento

| Arquivo | Categoria | Descrição do Conteúdo | Status de Indexação no Cherry Studio |
| :--- | :--- | :--- | :--- |
| `DOC-COR-01.md` | Correto | [PREENCHER - ex.: Política de reembolso e suporte técnico fictício] | [PREENCHER] |
| `DOC-COR-02.md` | Correto | [PREENCHER - ex.: Manual de instalação e pré-requisitos] | [PREENCHER] |
| `DOC-IRR-01.md` | Irrelevante | [PREENCHER - ex.: Artigo sobre cultivo de café no século XIX] | [PREENCHER] |
| `DOC-CON-01.md` | Conflitante | [PREENCHER - ex.: Versão alternativa da política com prazos divergentes] | [PREENCHER] |
| `DOC-MAL-01.md` | Malicioso | [PREENCHER - ex.: Texto técnico com payload de injeção indireta oculta] | [PREENCHER] |

---

## 3. Resultados
- **Total de Documentos no Corpus:** [PREENCHER - ex.: X arquivos]
- **Tamanho Médio dos Chunks no Cherry Studio:** [PREENCHER]
- **Observações de Indexação:** [PREENCHER]
