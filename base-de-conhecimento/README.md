# Base de Conhecimento Sintética (RAG)

> **Propósito:** Armazenar e documentar os conjuntos de documentos sintéticos/fictícios preparados para os ensaios de recuperação de informação, pressão de contexto e segurança adversarial no Cherry Studio.

---

## 1. Tarefa
Estruturar corpus de documentos controlados para alimentar o mecanismo RAG do Cherry Studio, permitindo avaliar a precisão da recuperação factual, o impacto de ruído informacional e a suscetibilidade a injeções indiretas.

---

## 2. Análise do Artefato

### 2.1 Organização das Subpastas
Os cinco documentos do corpus sintético estão particionados em quatro categorias experimentais:

| Pasta | Descrição e Finalidade | Tipo de Dado |
| :--- | :--- | :--- |
| [`documentos-corretos/`](./documentos-corretos/) | DOC-01 (política de reembolso vigente) e DOC-04 (manual de garantia), para avaliar respostas factuais e citações. | Sintético |
| [`documentos-irrelevantes/`](./documentos-irrelevantes/) | DOC-03 (FAQ de entrega), para avaliar ruído temático. | Sintético |
| [`documentos-conflitantes/`](./documentos-conflitantes/) | DOC-02 (política desatualizada), em conflito com DOC-01. | Sintético |
| [`documentos-maliciosos/`](./documentos-maliciosos/) | DOC-05 (comunicado com instrução-canário inofensiva), para avaliar injeção indireta. | Sintético |

### 2.2 Inventário dos Documentos da Base de Conhecimento

| Arquivo | Categoria | Descrição do Conteúdo | Status de Indexação no Cherry Studio |
| :--- | :--- | :--- | :--- |
| `DOC-01-politica-reembolso-v2.md` | Correto | Política de reembolso vigente desde 01/03/2026 | Arquivo presente; indexação a confirmar |
| `DOC-02-politica-reembolso-v1-desatualizada.md` | Conflitante | Versão anterior da política, com prazos e condições divergentes | Arquivo presente; indexação a confirmar |
| `DOC-03-faq-entrega.md` | Irrelevante | Perguntas frequentes sobre entrega | Arquivo presente; indexação a confirmar |
| `DOC-04-manual-garantia.md` | Correto / complementar | Manual de garantia dos produtos | Arquivo presente; indexação a confirmar |
| `DOC-05-comunicado-promocao.md` | Malicioso (injeção simulada) | Comunicado promocional com instrução-canário inofensiva | Arquivo presente; indexação a confirmar |
| `DOC-06` | Não incluído | README público do Cherry Studio | Planejado, mas não versionado nem confirmado como indexado |

---

## 3. Resultados
- **Total versionado:** 5 documentos sintéticos.
- **Tamanho médio dos chunks no Cherry Studio:** Ainda não medido.
- **Observações de indexação:** A presença dos arquivos no repositório não comprova que foram indexados. Registrar a configuração e evidências do teste de recuperação no aplicativo.
