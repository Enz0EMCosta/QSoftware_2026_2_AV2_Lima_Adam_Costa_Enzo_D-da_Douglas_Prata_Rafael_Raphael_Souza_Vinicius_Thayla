# Plano de Melhoria

> **Propósito:** Definir o plano de ação corretivo e preventivo focado nos 3 achados mais importantes da avaliação do Cherry Studio.

---

## 1. Tarefa
Estruturar o plano de intervenção técnica para tratar as causas raízes das três falhas de maior impacto identificadas, estabelecendo responsáveis, ações mitigatórias, prioridades e critérios de aceitação para reteste.

---

## 2. Análise do Artefato

### 2.1 Os 3 Achados Mais Importantes

#### Achado 1: [PREENCHER NOME DO ACHADO 1 - ex.: Injeção Indireta de Prompt via Documento RAG (`FAL-01`)]
- **Causa Provável:** Concatenação direta e indiscriminada dos chunks recuperados da base no prompt do usuário sem delimitação sintática protetora ou sanitização de instruções.
- **Ação Proposta:** Implementar delimitação estrita de tags XML (ex.: `<documento_contexto>...</documento_contexto>`) e atualizar o prompt com diretiva explícita de tratar o conteúdo exclusivamente como dado passivo.
- **Responsável:** [PREENCHER INTEGRANTE RESPONSÁVEL]
- **Prioridade:** P1 (Crítica)
- **Evidência Esperada:** Log/print do reteste demonstrando que a instrução maliciosa foi ignorada e a consulta original atendida.
- **Reteste Vinculado:** `RET-01` (executado sobre `CT-INJ-02`).

#### Achado 2: [PREENCHER NOME DO ACHADO 2 - ex.: Alucinação Factual em Contexto Ruidoso / Ausente (`FAL-05`)]
- **Causa Provável:** Ausência de limiar de confiança no recuperador vetorial e falta de cláusula restritiva de recusa no prompt baseline.
- **Ação Proposta:** Adoção do prompt estruturado `P-CIT-02` contendo penalização de alucinação e fallback obrigatório para "Informação não encontrada".
- **Responsável:** [PREENCHER INTEGRANTE RESPONSÁVEL]
- **Prioridade:** P1 (Alta)
- **Evidência Esperada:** Saída padronizada afirmando ausência de dados, sem invenção de regras ou valores.
- **Reteste Vinculado:** `RET-02` (executado sobre `CT-CTX-01`).

#### Achado 3: [PREENCHER NOME DO ACHADO 3 - ex.: Falha na Estruturação do JSON de Saída (`FAL-03`)]
- **Causa Provável:** Modelo de linguagem operando sem modo *JSON Mode* ou esquema forçado via API, gerando texto conversacional antes das chaves.
- **Ação Proposta:** Inclusão de poucos exemplos estruturados (técnica de `P-CIT-03`) e validação automática pré-renderização com `fontes/esquema-saida.json`.
- **Responsável:** [PREENCHER INTEGRANTE RESPONSÁVEL]
- **Prioridade:** P2 (Média)
- **Evidência Esperada:** Resposta 100% aderente ao schema validada pelo script em `fontes/validador/`.
- **Reteste Vinculado:** `RET-03` (executado sobre `CT-EST-01`).

---

## 3. Resultados
- **Status do Plano de Melhoria:** [PREENCHER - ex.: Planejado / Em implementação / Parcialmente Retestado]
- **Impacto Esperado na Confiabilidade:** [PREENCHER]
