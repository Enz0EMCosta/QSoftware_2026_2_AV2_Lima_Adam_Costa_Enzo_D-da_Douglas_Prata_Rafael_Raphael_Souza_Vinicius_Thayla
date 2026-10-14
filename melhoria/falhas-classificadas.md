# Classificação de Falhas

> **Propósito:** Registrar e categorizar as não-conformidades e anomalias detectadas durante a execução dos testes no Cherry Studio.

---

## 1. Tarefa
Catalogar todas as falhas encontradas de acordo com a taxonomia padronizada de tipos (dados/contexto, prompt, factualidade, rastreabilidade, formato, segurança, confiabilidade, usabilidade) e níveis de severidade (baixa, média, alta, crítica).

---

## 2. Análise do Artefato

### 2.1 Taxonomia de Falhas
- **Tipos de Falha:**
  - `dados/contexto`: Problemas na recuperação, chunking ou ruído no corpus RAG.
  - `prompt`: Instruções ambíguas ou incapazes de guiar o modelo adequadamente.
  - `factualidade`: Alucinação, extrapolação indevida ou invenção de fatos.
  - `rastreabilidade`: Ausência de indicação precisa de fontes ou trechos de apoio.
  - `formato`: Quebra de sintaxe JSON ou não conformidade com schema.
  - `segurança`: Vulnerabilidade a prompt injection ou vazamento de diretrizes.
  - `confiabilidade`: Respostas não-determinísticas ou falhas intermitentes.
  - `usabilidade`: Respostas truncadas, confusas ou de difícil interpretação.

- **Níveis de Severidade:**
  - `Crítica`: Impede o funcionamento seguro da aplicação ou expõe vulnerabilidade grave imediata.
  - `Alta`: Compromete a veracidade dos dados ou quebra de fluxo essencial sem contorno óbvio.
  - `Média`: Desvio relevante que afeta a precisão ou formato, contornável manualmente.
  - `Baixa`: Inconsistência cosmética ou de baixa relevância operacional.

### 2.2 Tabela de Falhas Catalogadas

| ID da Falha | Descrição Detalhada da Ocorrência | Tipo de Falha | Severidade | Caso de Teste de Origem | Impacto Observado |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `FAL-01` | [PREENCHER - ex.: Modelo acata comando malicioso em documento do RAG] | segurança | Crítica | `CT-INJ-02` | [PREENCHER] |
| `FAL-02` | [PREENCHER - ex.: Citação de página e trecho que não existem no documento] | factualidade | Alta | `CT-FUNC-01` | [PREENCHER] |
| `FAL-03` | [PREENCHER - ex.: Resposta gerada com JSON sem delimitadores corretos] | formato | Média | `CT-EST-01` | [PREENCHER] |
| `FAL-04` | [PREENCHER - ex.: Modelo não sinaliza contradição entre documentos conflitantes] | dados/contexto | Média | `CT-CTX-02` | [PREENCHER] |
| `FAL-05` | [PREENCHER - ex.: Alucinação de resposta ao receber documento irrelevante] | factualidade | Alta | `CT-CTX-01` | [PREENCHER] |

---

## 3. Resultados
- **Total de Falhas Detectadas:** [PREENCHER]
- **Distribuição por Severidade:**
  - Crítica: [PREENCHER] | Alta: [PREENCHER] | Média: [PREENCHER] | Baixa: [PREENCHER]
- **Tipo Mais Recorrente:** [PREENCHER]
