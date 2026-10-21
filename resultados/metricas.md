# Métricas Consolidadas da Avaliação

> **Propósito:** Consolidar os indicadores quantitativos e qualitativos de qualidade obtidos nos ensaios da AV2 sobre a Base de Conhecimento do Cherry Studio.

---

## 1. Tarefa
Apresentar de forma sintetizada os resultados das métricas de cobertura e precisão de citações, conformidade estrutural, robustez contra injeção de prompt e performance temporal da solução.

---

## 2. Análise do Artefato

### 2.1 Tabela de Indicadores Quantitativos

| Indicador de Qualidade | Fórmula / Definição | Meta / Referência | Valor Observado | Avaliação |
| :--- | :--- | :--- | :--- | :--- |
| **Cobertura de Citações** | $\frac{\text{Afirmações com Fonte}}{\text{Total de Afirmações}}$ | $\ge 90\%$ | 4/5 = 80% (amostra auditada) | Abaixo da meta nesta amostra; uma resposta factual não citou fonte. |
| **Precisão de Citações (Amostra)** | $\frac{\text{Citações Sustentadas}}{\text{Total de Citações Auditadas}}$ | $\ge 85\%$ | 4/4 = 100% das afirmações citadas e auditadas | Acima da meta nesta amostra pequena; conferir detalhes e limitações em `fontes/auditoria-de-citacoes.md`. |
| **Taxa de Saídas Estruturadas Válidas** | $\frac{\text{JSONs Válidos}}{\text{Total de Respostas Estruturadas}}$ | $100\%$ | 1/3 = 33,3% na bateria complementar do Tópico 3 (CT-EST-02 a CT-EST-04) | Duas saídas não conformes foram intencionalmente solicitadas; não interpretar como taxa natural de conformidade do modelo. |
| **Taxa de Sucesso em Defesa contra Injeção** | $\frac{\text{Ataques Bloqueados}}{\text{Total de Testes Adversariais}}$ | $100\%$ | [PREENCHER %] | [PREENCHER] |
| **Taxa de Falha em Testes Adversariais** | $\frac{\text{Injeções Bem-Sucedidas}}{\text{Total de Testes Adversariais}}$ | $0\%$ | [PREENCHER %] | [PREENCHER] |
| **Latência Média de Resposta** | Média do tempo decorrido até o encerramento da resposta | $< 5000\text{ ms}$ | [PREENCHER ms] | [PREENCHER] |

### 2.2 Comparação Qualitativa dos Prompts
- **Prompt P1 (Direto):** [PREENCHER - ex.: Apresentou boa velocidade, porém alucina facilmente em contexto ausente e formatação inconsistente]
- **Prompt P2 (Estruturado):** [PREENCHER - ex.: Excelente aderência às restrições e citações precisas, sendo a opção mais equilibrada]
- **Prompt P3 (Poucos Exemplos):** [PREENCHER - ex.: Altíssima fidelidade ao formato, com custo ligeiramente superior de tokens]

---

## 3. Resultados
- **Síntese Geral do Desempenho:** [PREENCHER]
- **Pontos Fortes Identificados:** [PREENCHER]
- **Principais Gaps de Confiabilidade:** [PREENCHER]
