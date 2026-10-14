# Testes Metamórficos

> **Propósito:** Registrar os testes metamórficos, avaliando se variações na forma da pergunta (reformulações sintáticas ou traduções de idioma) preservam a equivalência lógica e factual da resposta da IA.

---

## 1. Tarefa
Aplicar transformações nas entradas de teste (relação metamórfica) sem alterar o contexto factual subjacente e verificar se a saída do Cherry Studio mantém consistência semântica e factual.

---

## 2. Análise do Artefato

### 2.1 Relações Metamórficas Definidas
- **RM-01 (Invariância por Paráfrase):** Se $P_1$ e $P_2$ expressam o mesmo significado sob o mesmo contexto $C$, a resposta factual $R(P_1, C)$ deve ser equivalente a $R(P_2, C)$.
- **RM-02 (Invariância por Tradução):** Se a consulta é traduzida para outro idioma mantendo o contexto $C$, a resposta deve preservar as mesmas fontes e fatos nucleares.

### 2.2 Casos de Teste Detalhados
- **`CT-MET-01`**: Paráfrase sintática da consulta de `CT-FUNC-01`.
  - Pergunta Original: [PREENCHER]
  - Pergunta Reformulada: [PREENCHER]
  - Resposta Original vs. Reformulada: [PREENCHER]
- **`CT-MET-02`**: Tradução de consulta para o idioma inglês.
  - Pergunta em Português: [PREENCHER]
  - Pergunta em Inglês: [PREENCHER]
  - Comparação de Consistência: [PREENCHER]

---

## 3. Resultados
- **Violações da Relação Metamórfica:** [PREENCHER - ex.: 0 violações / X incoerências detectadas]
- **Evidências:** `testes/capturas/CT-MET-01.png`, `CT-MET-02.png`
