# Ficha da Missão: Contexto Confiável

> **Propósito:** Registrar o recorte, o ambiente e as limitações da avaliação da Base de Conhecimento (RAG) do Cherry Studio na AV2.

---

## 1. Identificação e escopo

- **Projeto avaliado:** Cherry Studio
- **Repositório oficial:** [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio)
- **Organização responsável:** CherryHQ
- **Licença:** AGPL-3.0 para a Community Edition. O projeto também informa a existência de licença comercial separada para quem necessita de isenção das obrigações da AGPL; verificar os termos aplicáveis antes de redistribuir ou integrar o software.
- **Versão avaliada:** 2.0.13, tag `v2.0.13`
- **Commit avaliado:** [`6e3af1beac02cdc53dd2aba382cb6af7475dc669`](https://github.com/CherryHQ/cherry-studio/commit/6e3af1beac02cdc53dd2aba382cb6af7475dc669)
- **Data de acesso registrada pela equipe:** 17/10/2026
- **Finalidade no recorte:** Consultar documentos cadastrados na Base de Conhecimento e avaliar como o contexto recuperado influencia as respostas do modelo.
- **Usuário do cenário:** Usuário final que pergunta, pelo chat, sobre a política de reembolso de uma empresa fictícia.
- **Fluxo avaliado:** Base de Conhecimento do Cherry Studio, em um fluxo de geração aumentada por recuperação (RAG).
- **Missões da AV2 relacionadas:**
  - **(D) Contexto sob Pressão:** comparar o comportamento com contexto correto, ausente, irrelevante e conflitante.
  - **(B) Defesa contra Prompt Injection:** avaliar instruções adversariais diretas e instruções inseridas em documentos recuperados.

## 2. Configuração do ensaio

- **Aplicativo:** Cherry Studio 2.0.13.
- **Modo de chat observado:** Agent, sem pasta de trabalho vinculada.
- **Provedor de modelo:** Google Gemini.
- **Modelo de linguagem exibido no aplicativo:** `Gemini Flash-Lite Latest`.
- **Identificador/versão interna do modelo:** Não confirmado. O alias `latest` pode apontar para versões diferentes ao longo do tempo.
- **Acesso ao modelo:** API do Google, usando chave de API gratuita. A chave é segredo operacional: não deve ser incluída neste repositório, nos documentos de teste, nas capturas ou nos logs públicos.
- **Modelo de embeddings:** Não identificado/registrado pela equipe. Confirmar no aplicativo e registrar o valor utilizado, ou indicar que a configuração não foi exposta.
- **Recuperação:** A equipe descreve busca por palavras-chave (BM25) e/ou embeddings. O algoritmo efetivamente usado nesta execução e seus parâmetros precisam ser confirmados empiricamente.
- **Ferramentas e integrações no recorte:** MCP e busca na web desativados. O menu do modo Agent também apresenta opções de Base de Conhecimento, MCP, prompts e notas; apenas a Base de Conhecimento integra o recorte.
- **Formatos do corpus versionado:** Documentos planejados em Markdown (`.md`). Confirmar que os arquivos efetivamente carregados no aplicativo correspondem aos arquivos versionados.
- **Corpus versionado:** cinco documentos sintéticos, listados em [`../base-de-conhecimento/README.md`](../base-de-conhecimento/README.md). O DOC-06 (README oficial do Cherry Studio) está planejado, mas não foi incluído. A presença dos arquivos no repositório não comprova sua indexação no aplicativo; registrar a lista carregada e evidências de recuperação.

## 3. Fluxo avaliado

1. O usuário envia uma pergunta pelo chat.
2. O Cherry Studio aplica as instruções do assistente/prompt de sistema.
3. A Base de Conhecimento recupera trechos (*chunks*) dos documentos previamente cadastrados e indexados.
4. A pergunta e os trechos recuperados são reunidos no contexto enviado ao modelo. Este é o principal limite de confiança: documentos externos podem conter texto que se parece com instruções.
5. A solicitação é enviada pela internet à API do Gemini.
6. MCP e busca na web permanecem desativados durante o ensaio.
7. A resposta é exibida ao usuário com as referências disponibilizadas pelo aplicativo.
8. O histórico da conversa permanece no aplicativo; capturas e logs de execução são mantidos pela equipe como evidências, sem incluir credenciais.

Os prompts principais são as três variantes documentadas em [`../prompts/`](../prompts/): direto (P1), estruturado (P2) e com poucos exemplos (P3). Os testes devem registrar qual variante foi usada em cada execução.

## 4. Limitações

1. O corpus versionado é pequeno (cinco documentos sintéticos); os resultados não se generalizam para bases reais. O DOC-06 público ainda não está incluído.
2. O Gemini Flash-Lite é acessado por cota gratuita, sujeito a limites de uso e a variação entre execuções.
3. O alias `latest` pode mudar sem que o nome exibido mude, reduzindo a reprodutibilidade.
4. A documentação consultada não esclarece suficientemente como as referências são exibidas nem os parâmetros de divisão em *chunks*; esses comportamentos precisam ser registrados por observação.
5. A equipe avalia o comportamento observável e não audita internamente o código do mecanismo de recuperação.
6. Os resultados dependem da versão do Cherry Studio instalada.
7. No Cherry Studio 2.0.13, o ensaio usa o modo Agent sem pasta de trabalho vinculada; o menu de entrada oferece Base de Conhecimento, MCP, prompts e notas.
8. Respostas do próprio modelo sobre a sua versão ou ambiente de execução não são evidência verificável.
9. O modelo de embeddings, o sistema operacional do ambiente de teste e os parâmetros de recuperação/chunking não estão registrados neste artefato.

## 5. Resultado do mapeamento

O recorte e o fluxo de confiança foram definidos. A configuração informada pela equipe é Gemini Flash-Lite Latest, com MCP e busca na web desativados. O corpus previsto para os ensaios contém os cinco documentos sintéticos listados em `../base-de-conhecimento/`; o DOC-06 público não será considerado nesta versão do escopo. Para tornar o ensaio reproduzível, ainda é necessário registrar o modelo de embeddings (ou confirmar que não foi configurado), os parâmetros observados e quais documentos foram efetivamente indexados, com evidências de recuperação.
