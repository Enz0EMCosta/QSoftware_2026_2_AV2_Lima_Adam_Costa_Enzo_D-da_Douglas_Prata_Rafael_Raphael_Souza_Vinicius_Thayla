# AV2 — Missão Contexto Confiável (Cherry Studio)

> **Disciplina:** Qualidade de Software — 2026.2 — UFS  
> **Equipe 04:** Adam Lima, Enzo Costa, Douglas D-da, Rafael Prata, Raphael, Vinicius Souza, Thayla  
> **Aplicação Avaliada:** [Cherry Studio](https://github.com/CherryHQ/cherry-studio) (Cliente Desktop Electron + React + TypeScript para LLMs/RAG)

---

## 1. Resumo do Projeto
Este repositório contém os artefatos de avaliação de qualidade de software desenvolvidos na Atividade 2 (AV2). Dando continuidade à AV1, o foco desta avaliação é a **Missão Contexto Confiável**, aplicando testes rigorosos sobre o fluxo de **Base de Conhecimento (RAG)** do Cherry Studio, com foco em robustez sob pressão de contexto e segurança contra injeção de instruções (*prompt injection*).

## 2. Missões Escolhidas
- **(D) Contexto sob Pressão:** Avaliação do comportamento da IA e do mecanismo de recuperação frente a documentos ruidosos, irrelevantes, ausentes e conflitantes.
- **(B) Defesa contra Prompt Injection:** Avaliação da resistência contra injeção direta de prompts e injeção indireta oculta em documentos indexados no RAG.

---

## 3. Vídeo da atividade
- **URL da Apresentação Gravada:** [PREENCHER URL]
- **Duração:** [PREENCHER DURAÇÃO - máx. 20 min]
- **Data da Gravação:** [PREENCHER DATA]
- **Participantes:** Adam Lima, Enzo Costa, Douglas D-da, Rafael Prata, Raphael, Vinicius Souza, Thayla

---

## 4. Índice das Pastas e Estrutura do Repositório

```text
.
├── README.md                                  <- Resumo, índice, integrantes e link do vídeo
├── missao/                                    <- Definição do escopo, fluxo e dados
│   ├── ficha-da-missao.md                     <- Ficha técnica da missão e recorte avaliado
│   ├── fluxo-de-dados.md                      <- Fluxograma detalhado da requisição e RAG
│   └── classificacao-dos-dados.md             <- Matriz de classificação de sensibilidade dos dados
├── base-de-conhecimento/                      <- Corpus sintético organizado para os ensaios de RAG
│   ├── README.md                              <- Explicação dos conjuntos de documentos
│   ├── documentos-corretos/                   <- DOC-01 (política vigente) e DOC-04 (garantia)
│   ├── documentos-irrelevantes/                <- DOC-03 (FAQ de entrega)
│   ├── documentos-conflitantes/                <- DOC-02 (política desatualizada)
│   └── documentos-maliciosos/                  <- DOC-05 (injeção indireta com canário inofensivo)
├── prompts/                                   <- Prompts versionados e experimento comparativo
│   ├── P1-direto.md                           <- Prompt direto de instrução simples
│   ├── P2-estruturado.md                      <- Prompt com objetivo, contexto, restrições e formato
│   ├── P3-poucos-exemplos.md                  <- Prompt com técnica Few-Shot (exemplos guiados)
│   └── comparacao.md                          <- Análise comparativa e benchmark dos prompts
├── testes/                                    <- Casos de teste e detalhamento das execuções
│   ├── casos-de-teste.md                      <- Matriz geral de casos de teste estruturada
│   ├── casos-de-teste.csv                     <- Planilha de casos de teste em formato CSV
│   ├── funcionais/                            <- Detalhamento dos testes funcionais de RAG
│   ├── contexto/                              <- Detalhamento dos testes de pressão de contexto
│   ├── metamorficos/                          <- Detalhamento dos testes metamórficos
│   ├── adversariais/                          <- Testes de injeção direta e indireta
│   ├── saida-estruturada/                     <- Testes de conformidade e falhas de formato
│   └── capturas/                              <- Evidências, prints e logs de execução
├── fontes/                                    <- Verificação de factualidade e validação de saída
│   ├── auditoria-de-citacoes.md               <- Auditoria de afirmações vs. trecho de apoio
│   ├── esquema-saida.json                     <- JSON Schema formal esperado para as respostas
│   └── validador/                             <- Scripts/testes de validação estrutural do schema
├── ameacas/                                   <- Modelagem de riscos e segurança
│   └── modelo-de-ameacas.md                   <- Análise de ameaças (ativos, vetores, impactos, controles)
├── resultados/                                <- Métricas consolidadas e rastreabilidade
│   ├── metricas.md                            <- Cobertura de citações, precisão, taxa de injeção, latência
│   └── rastreabilidade.md                     <- Matriz de Rastreabilidade ponta a ponta
├── melhoria/                                  <- Registro de bugs e plano de ação corretiva
│   ├── falhas-classificadas.md                <- Catálogo de falhas classificadas por tipo e severidade
│   ├── plano-de-melhoria.md                   <- Plano para os 3 achados principais
│   └── reteste.md                             <- Evidências e resultados de reteste
├── conclusao/                                 <- Fechamento da avaliação técnica
│   ├── discussao.md                           <- Discussão crítica dos resultados
│   └── limitacoes.md                          <- Limitações metodológicas da avaliação
├── equipe/                                    <- Governança da equipe e transparência
│   ├── contribuicoes.md                       <- Tabela de contribuição individual de cada membro
│   └── uso-de-ia.md                           <- Registro do uso de IA generativa no trabalho
└── entrega/                                   <- Artefatos finais de entrega
    ├── relatorio-tecnico.pdf                  <- Relatório técnico final consolidado
    ├── apresentacao.pdf                       <- Slides da apresentação
    └── VIDEO.md                               <- Metadados e links do vídeo da apresentação
```

---

## 5. Integrantes da Equipe
- Adam Lima
- Enzo Costa
- Douglas D-da
- Rafael Prata
- Raphael
- Vinicius Souza
- Thayla