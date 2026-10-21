# Declaração de Uso de IA Generativa

> **Propósito:** Registrar de forma ética e transparente o uso de ferramentas de Inteligência Artificial generativa durante a elaboração dos artefatos da AV2, explicitando os prompts, as respostas obtidas e o senso crítico aplicado nas revisões humanas.

---

## 1. Tarefa
Documentar todas as interações com ferramentas de IA generativa (ex.: GitHub Copilot, Gemini, ChatGPT), registrando finalidade, comandos, saídas e a avaliação crítica da equipe sobre o que foi aproveitado, corrigido ou rejeitado.

---

## 2. Análise do Artefato

### 2.1 Tabela de Uso de IA Generativa

| IA generativa | Finalidade | Prompt utilizado | Saída | O que foi aproveitado / corrigido / rejeitado |
| :--- | :--- | :--- | :--- | :--- |
| GitHub Copilot / Antigravity (Equipe) | Criação do esqueleto inicial do repositório da AV2 | "Estruture o esqueleto de diretórios e templates Markdown para a Atividade 2 (Missão Contexto Confiável) cobrindo missão, base de conhecimento, prompts, testes, fontes, ameaças, resultados, melhoria, conclusão e equipe." | Esqueleto estruturado de pastas e arquivos Markdown | **Aproveitado:** Toda a estrutura de pastas e tópicos da AV2.<br>**Corrigido:** Ajuste manual de nomes de arquivos e IDs padronizados.<br>**Rejeitado:** Nenhum. |
| Claude (Raphael, Tópico 4) | Entender o vocabulário do modelo de ameaças | "Explique em no máximo 5 linhas a diferença entre ativo, ameaça, vetor, impacto e controle, usando um exemplo de RAG." | Explicação em 5 linhas: ativo (o que se protege), ameaça (o que pode acontecer), vetor (o caminho do ataque), impacto (o estrago) e controle (a proteção), com o exemplo de um documento da base com ordem escondida. | **Aproveitado:** a resposta, usada para entender o vocabulário do modelo de ameaças. |
| Claude (Raphael, Tópico 4) | Validar a escolha dos riscos | "Estes são os riscos propostos para o fluxo de Base de Conhecimento do Cherry Studio, e que decidi adotar: [R1 a R4]. Diga só se algum não faz sentido para esse fluxo ou se falta um tipo exigido (injeção de instruções e risco de fontes ou saída)." | Os 4 riscos fazem sentido e cobrem injeção de instruções (R1 e R2) e fontes (R3). Observou que o R4 é um risco do aplicativo e não do fluxo da Base de Conhecimento. | **Aproveitado:** a resposta, usada para validar a escolha dos riscos. |
| Claude (Raphael, Tópico 4) | Conferir os fatos sobre o CVE | "Segue o texto sobre o CVE-2026-40501 que adotei a partir do rascunho anterior, feito pela própria IA: [texto sobre o CVE]. Confira em fonte pública e diga só se cada afirmação está correta ou não, com o link da fonte." | Afirmações conferidas no OSV e no repositório oficial: cinco corretas e uma parcial (a comparação com a Base de Conhecimento é interpretação). Ressalva: a v1.9.13 ainda tem o código vulnerável, embora o registro diga "até 1.9.12". | **Aproveitado:** a resposta, usada para conferir os fatos sobre o CVE. |
| ChatGPT (Thayla) | Organização das informações dos testes da AV2, elaboração de ideias de perguntas para os casos de teste e apoio na documentação dos resultados do fluxo RAG no Cherry Studio. | "Me ajude a organizar a matriz de casos de teste do fluxo RAG no Cherry Studio, proponha perguntas para os testes funcionais, de contexto e fontes, metamórficos, adversariais e de saída estruturada, e auxilie na documentação dos resultados esperados, resultados observados e evidências." | Sugestões de perguntas para os 10 casos de teste, organização das informações em tabelas Markdown, padronização dos IDs dos testes e auxílio na descrição das contribuições e evidências. | **Aproveitado:** sugestões de perguntas, organização das informações, estruturação das tabelas e apoio à documentação. **Corrigido:** ajustes nos textos para corresponder aos testes executados com a base de conhecimento desenvolvida pelo grupo e o modelo Gemini Flash Lite. **Rejeitado:** sugestões que não correspondiam aos cenários efetivamente testados. |
| Gemini / Antigravity (Adam Lima, Tópico 7) | Apoio na classificação de falhas, estruturação do plano de melhoria para os 3 achados principais e consolidação dos artefatos de governança do repositório (`melhoria/`, `README.md`, `VIDEO.md` e `contribuicoes.md`). | "Com base nos resultados dos Tópicos 1 a 6 do grupo sobre o fluxo RAG do Cherry Studio, classifique as falhas encontradas por tipo e severidade, selecione os 3 achados mais importantes e monte o plano de melhoria com causa provável, ação, responsável, prioridade, evidência esperada e reteste." | Tabelas estruturadas de falhas (`FAL-01` a `FAL-05`), plano de ação detalhado para os 3 achados de severidade alta (`ACH-01` a `ACH-03`), matriz de reteste (`RET-01` a `RET-03`) e atualização dos metadados de entrega. | **Aproveitado:** estruturação das tabelas de classificação de falhas, plano de melhoria e reteste.<br>**Corrigido:** vinculação estrita aos casos reais executados pela equipe (`AUD-01`, `CT-EST-01` a `04`, `CT-CTX-01` e `CT-INJ-01`/`02`).<br>**Rejeitado:** exemplos genéricos do template que não correspondiam aos resultados observados no Cherry Studio. |

### 2.2 Declaração de Raphael Ferreira Portella Bacelar (Tópico 4)

As três linhas marcadas com "Raphael, Tópico 4" na tabela acima são as mesmas da declaração do relatório. Nos prompts 2 e 3, `[R1 a R4]` são os riscos da tabela de [`../ameacas/modelo-de-ameacas.md`](../ameacas/modelo-de-ameacas.md) e `[texto sobre o CVE]` é o texto da Seção 2.4 desse arquivo.

- **Aproveitado:** as respostas dos três prompts, usadas para entender o vocabulário do modelo de ameaças, validar a escolha dos riscos e conferir os fatos sobre o CVE.
- **Verificações realizadas:** os fatos sobre o CVE foram conferidos em fontes públicas (OSV e repositório oficial do Cherry Studio no GitHub), afirmação por afirmação, pelo prompt 3.
- **Supervisão humana:** a IA foi usada para explicar o vocabulário, validar a escolha dos riscos e conferir fatos.

### 2.3 Declaração de Thayla (202300061840)

O ChatGPT foi utilizado como ferramenta de apoio na organização das informações dos testes da AV2, na elaboração de ideias de perguntas para os casos de teste e na documentação dos resultados do fluxo de Base de Conhecimento (RAG) do Cherry Studio, utilizando a base de conhecimento desenvolvida pelo grupo e o modelo Gemini Flash Lite.

- **Aproveitado:** as sugestões de perguntas para os 10 casos de teste, a organização das informações em tabelas Markdown, a padronização dos IDs dos testes e o auxílio na descrição dos resultados e das evidências.
- **Verificações realizadas:** os resultados esperados e observados foram organizados com base nos registros dos testes executados, abrangendo as categorias funcional, contexto e fontes, metamórfica, adversarial e saída estruturada.
- **Supervisão humana:** a IA foi utilizada como ferramenta de apoio para organizar informações, sugerir perguntas e auxiliar na documentação. A seleção e a adequação dos conteúdos foram realizadas considerando os cenários de teste e os resultados registrados durante a execução no Cherry Studio.
---

### 2.4 Declaração de Adam Guilherme Mendes Lima (Tópico 7)

O Gemini (via Antigravity) foi utilizado como ferramenta de apoio na consolidação das falhas observadas nos Tópicos 1 a 6, na formatação do plano de melhoria para os três principais achados e na organização dos arquivos de governança do repositório (`melhoria/`, `README.md`, `entrega/VIDEO.md` e `equipe/contribuicoes.md`).

- **Aproveitado:** a padronização da tabela de falhas segundo a taxonomia do edital (`rastreabilidade`, `formato`, `segurança`, `dados/contexto`, `confiabilidade`), a estruturação do plano de melhoria com causa provável, ação, prioridade, evidência esperada e reteste, e a revisão da documentação do repositório.
- **Verificações realizadas:** todas as falhas e ações propostas foram confrontadas com as evidências reais produzidas pelo grupo no Cherry Studio (`LAB-P1-CORRETO`, `CT-EST-01` a `CT-EST-04`, `CT-CTX-01` e `CT-INJ-01`/`CT-INJ-02`), descartando falhas hipotéticas do template inicial.
- **Supervisão humana:** a escolha dos três achados prioritários e a validação da coerência com os resultados de cada integrante foram conduzidas integralmente pelo responsável pelo Tópico 7.

---

## 3. Resultados
- **Avaliação Crítica do Grupo:** O uso de ferramentas de IA generativa acelerou a estruturação de tabelas Markdown, a revisão textual e a verificação cruzada de fontes públicas (como o `CVE-2026-40501`), enquanto a execução prática dos ensaios no Cherry Studio 2.0.13, a captura de evidências e o julgamento crítico dos resultados foram conduzidos pela equipe.
- **Conformidade Ética e Acadêmica:** Todas as interações relevantes foram declaradas com indicação de ferramenta, finalidade, prompt e curadoria humana, sem inclusão de dados pessoais reais ou chaves de API.
