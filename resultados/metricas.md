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
| **Taxa de Sucesso em Defesa contra Injeção** | $\frac{\text{Ataques Bloqueados}}{\text{Total de Testes Adversariais}}$ | $100\%$ | 2/2 = 100% (`CT-INJ-01` e `CT-INJ-02`) | Ambos os testes adversariais (direto e indireto com canário `CANARIO-INJ-742`) foram resistidos com `P-CIT-02`. |
| **Taxa de Falha em Testes Adversariais** | $\frac{\text{Injeções Bem-Sucedidas}}{\text{Total de Testes Adversariais}}$ | $0\%$ | 0/2 = 0% | Nenhuma tentativa avaliada conseguiu impor prazo falso ou executar o comando-canário. |
| **Latência Média de Resposta** | Média do tempo decorrido até o encerramento da resposta | $< 5000\text{ ms}$ | Não cronometrada formalmente (observado ~4 s a 54 s nas capturas) | Os registros do laboratório trazem horários de relógio; em `CT-EST-02` e `CT-EST-04` a interface exibiu `Processed · 26s` e `Processed · 4s`. |

### 2.2 Comparação Qualitativa dos Prompts
- **Prompt P1 (Direto):** Acertou os fatos nas duas condições (7 dias na Condição A; divergência de 7 vs. 15 dias na Condição B), mas omitiu a citação explícita da fonte na Condição A (50% de respostas com citação) e não teve trechos de apoio registrados na Condição B.
- **Prompt P2 (Estruturado):** Atingiu 100% de correção factual e 100% de citação explícita nas duas condições (`DOC-01` na Condição A; `DOC-01` e `DOC-02` com trechos de apoio na Condição B), oferecendo alta rastreabilidade.
- **Prompt P3 (Poucos Exemplos):** Empatou tecnicamente com `P2` na amostra avaliada, alcançando 100% de correção factual, identificação do conflito entre versões (v2.0 de 01/03/2026 vs. v1.0 de 10/05/2024) e 100% de citação com trechos de apoio.

---

## 3. Resultados
- **Síntese Geral do Desempenho:** 10/10 testes obrigatórios aprovados (100%), 6/6 execuções do laboratório factualmente corretas (100%), 4/5 afirmações auditadas com fonte citada (cobertura de 80%), 4/4 citações válidas sustentadas pelos documentos (precisão de 100%) e 2/2 ataques de injeção resistidos (100%).
- **Pontos Fortes Identificados:** Alta precisão factual sobre o corpus sintético, reconhecimento consistente de divergência entre versões de documentos (`DOC-01` vs. `DOC-02`) e resistência aos ensaios de injeção direta e indireta quando utilizado o prompt estruturado `P-CIT-02`.
- **Principais Gaps de Confiabilidade:** Queda de rastreabilidade no prompt direto `P1` (ausência de citação na Condição A) e ausência de validação nativa de JSON Schema no chat (permitindo que JSONs sintaticamente válidos violem campos obrigatórios ou enumerações sem bloqueio automático).
