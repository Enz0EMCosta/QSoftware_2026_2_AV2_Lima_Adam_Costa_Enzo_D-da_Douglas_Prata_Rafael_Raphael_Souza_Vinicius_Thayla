# Classificação dos Dados de Teste

> **Propósito:** Identificar a natureza e a sensibilidade dos dados do ensaio de RAG, evitando o envio de dados reais ou segredos ao provedor externo.

---

## 1. Categorias

- **Público:** conteúdo publicado abertamente e usado conforme os termos aplicáveis.
- **Sintético:** conteúdo inventado para a atividade, sem representar pessoas, empresas, políticas ou credenciais reais.
- **Interno:** artefatos de trabalho da equipe que não são públicos por padrão. A classificação como interno não autoriza inserir segredos neles.
- **Não permitido no corpus ou nas evidências compartilhadas:** dados pessoais reais desnecessários, dados sensíveis, informações confidenciais e credenciais válidas.

## 2. Inventário e classificação

| ID | Dado / documento | Categoria | Uso no ensaio | Salvaguarda / situação |
| :--- | :--- | :--- | :--- | :--- |
| `DOC-01` | [`../base-de-conhecimento/documentos-corretos/DOC-01-politica-reembolso-v2.md`](../base-de-conhecimento/documentos-corretos/DOC-01-politica-reembolso-v2.md) | Sintético | Política de reembolso vigente | Arquivo versionado; indexação no Cherry Studio ainda a confirmar. |
| `DOC-02` | [`../base-de-conhecimento/documentos-conflitantes/DOC-02-politica-reembolso-v1-desatualizada.md`](../base-de-conhecimento/documentos-conflitantes/DOC-02-politica-reembolso-v1-desatualizada.md) | Sintético | Política desatualizada para teste de conflito | Arquivo versionado; indexação no Cherry Studio ainda a confirmar. |
| `DOC-03` | [`../base-de-conhecimento/documentos-irrelevantes/DOC-03-faq-entrega.md`](../base-de-conhecimento/documentos-irrelevantes/DOC-03-faq-entrega.md) | Sintético | Ruído temático | Arquivo versionado; indexação no Cherry Studio ainda a confirmar. |
| `DOC-04` | [`../base-de-conhecimento/documentos-corretos/DOC-04-manual-garantia.md`](../base-de-conhecimento/documentos-corretos/DOC-04-manual-garantia.md) | Sintético | Documento complementar sobre garantia | Arquivo versionado; indexação no Cherry Studio ainda a confirmar. |
| `DOC-05` | [`../base-de-conhecimento/documentos-maliciosos/DOC-05-comunicado-promocao.md`](../base-de-conhecimento/documentos-maliciosos/DOC-05-comunicado-promocao.md) | Sintético | Injeção indireta simulada por instrução-canário inofensiva | Arquivo versionado; indexação no Cherry Studio ainda a confirmar. |
| `DOC-06` | README oficial do Cherry Studio | Público, planejado | Documento público de referência | Não incluído no corpus versionado; registrar URL/data e confirmar antes de incluir ou remover do escopo. |
| Prompts P1, P2 e P3 | Perguntas e instruções de teste documentadas no repositório | Interno (artefato acadêmico) | Comparação de estratégias de prompt | Não inserir informações pessoais ou credenciais nos prompts. |
| Perguntas, respostas, referências e capturas das execuções | Evidências produzidas durante os testes | Interno até publicação | Auditoria e cálculo de métricas | Usar somente os documentos fictícios/públicos; revisar e remover segredos antes de compartilhar. |
| Chave da API do Google | Credencial para acessar o Gemini | Não permitido no corpus, nos commits e nas evidências públicas | Autenticação local no provedor | Manter fora do repositório e dos arquivos de teste; não registrar o valor em capturas ou logs. |
| Dados reais de pacientes, usuários ou empresas; senhas, tokens e chaves válidas | Dados pessoais, confidenciais ou credenciais | Não permitido | Nenhum | Não coletar, cadastrar na Base de Conhecimento, enviar ao provedor ou incluir em evidências. |
| Identificação acadêmica dos integrantes | Nome e, quando exigido, matrícula na documentação da disciplina | Pessoal administrativo; não é dado do corpus | Identificação/autoria do trabalho | Restringir ao material de entrega exigido; nunca reutilizar como conteúdo de teste ou enviar à Base de Conhecimento. |

## 3. Resultado da classificação

O repositório contém cinco documentos sintéticos. O DOC-06 público aparece no planejamento, mas não foi incluído; alinhar o escopo e as referências a essa decisão. A classificação dos arquivos versionados não comprova que eles foram indexados no Cherry Studio: registrar o inventário realmente carregado e as evidências de recuperação.

A equipe ainda deve registrar o resultado de uma verificação de credenciais no repositório e nas evidências. Não afirmar que uma varredura foi executada enquanto não houver evidência desse procedimento.
