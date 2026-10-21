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
| [PREENCHER ex: GitHub Copilot / Antigravity] | Criação do esqueleto inicial do repositório da AV2 | "[PREENCHER TEXTO DO PROMPT]" | Esqueleto estruturado de pastas e arquivos Markdown | **Aproveitado:** Toda a estrutura de pastas e tópicos da AV2.<br>**Corrigido:** Ajuste manual de nomes de arquivos e IDs padronizados.<br>**Rejeitado:** Nenhum. |
| Claude (Raphael, Tópico 4) | Entender o vocabulário do modelo de ameaças | "Explique em no máximo 5 linhas a diferença entre ativo, ameaça, vetor, impacto e controle, usando um exemplo de RAG." | Explicação em 5 linhas: ativo (o que se protege), ameaça (o que pode acontecer), vetor (o caminho do ataque), impacto (o estrago) e controle (a proteção), com o exemplo de um documento da base com ordem escondida. | **Aproveitado:** a resposta, usada para entender o vocabulário do modelo de ameaças. |
| Claude (Raphael, Tópico 4) | Validar a escolha dos riscos | "Estes são os riscos propostos para o fluxo de Base de Conhecimento do Cherry Studio, e que decidi adotar: [R1 a R4]. Diga só se algum não faz sentido para esse fluxo ou se falta um tipo exigido (injeção de instruções e risco de fontes ou saída)." | Os 4 riscos fazem sentido e cobrem injeção de instruções (R1 e R2) e fontes (R3). Observou que o R4 é um risco do aplicativo e não do fluxo da Base de Conhecimento. | **Aproveitado:** a resposta, usada para validar a escolha dos riscos. |
| Claude (Raphael, Tópico 4) | Conferir os fatos sobre o CVE | "Segue o texto sobre o CVE-2026-40501 que adotei a partir do rascunho anterior, feito pela própria IA: [texto sobre o CVE]. Confira em fonte pública e diga só se cada afirmação está correta ou não, com o link da fonte." | Afirmações conferidas no OSV e no repositório oficial: cinco corretas e uma parcial (a comparação com a Base de Conhecimento é interpretação). Ressalva: a v1.9.13 ainda tem o código vulnerável, embora o registro diga "até 1.9.12". | **Aproveitado:** a resposta, usada para conferir os fatos sobre o CVE. |
| [PREENCHER] | [PREENCHER] | "[PREENCHER]" | [PREENCHER] | [PREENCHER] |
| [PREENCHER] | [PREENCHER] | "[PREENCHER]" | [PREENCHER] | [PREENCHER] |

### 2.2 Declaração de Raphael Ferreira Portella Bacelar (Tópico 4)

As três linhas marcadas com "Raphael, Tópico 4" na tabela acima são as mesmas da declaração do relatório. Nos prompts 2 e 3, `[R1 a R4]` são os riscos da tabela de [`../ameacas/modelo-de-ameacas.md`](../ameacas/modelo-de-ameacas.md) e `[texto sobre o CVE]` é o texto da Seção 2.4 desse arquivo.

- **Aproveitado:** as respostas dos três prompts, usadas para entender o vocabulário do modelo de ameaças, validar a escolha dos riscos e conferir os fatos sobre o CVE.
- **Verificações realizadas:** os fatos sobre o CVE foram conferidos em fontes públicas (OSV e repositório oficial do Cherry Studio no GitHub), afirmação por afirmação, pelo prompt 3.
- **Supervisão humana:** a IA foi usada para explicar o vocabulário, validar a escolha dos riscos e conferir fatos.

---

## 3. Resultados
- **Avaliação Crítica do Grupo:** [PREENCHER - Destacar como a IA acelerou tarefas mecânicas enquanto a validação conceitual e os testes no software foram 100% conduzidos pelos integrantes]
- **Conformidade Ética e Acadêmica:** [PREENCHER]
