# Capturas e Evidências de Teste

> **Propósito:** Inventariar capturas de tela dos testes executados no Cherry Studio e ligar cada arquivo ao caso ou à execução correspondente.

## 1. Evidências do conjunto original

| Arquivo | Caso de teste | Descrição | Status |
| :--- | :--- | :--- | :--- |
| `evidencia1.png` | `CT-FUNC-01` | Resposta sobre o prazo de arrependimento de 7 dias corridos e identificação da política v2.0. | Aprovada |
| `evidencia2.png` | `CT-FUNC-02` | Resposta sobre o pagamento do frete de devolução e condições para devolução. | Aprovada |
| `evidencia3.png` | `CT-FUNC-03` | Resposta sobre a alteração do endereço de entrega antes da expedição. | Aprovada |
| `evidencia4.png` | `CT-CTX-01` | Resposta sobre prazo de entrega em uma capital, com referência ao FAQ. | Aprovada |
| `evidencia5.png` | `CT-CTX-02` | Comparação entre as políticas de reembolso v1.0 e v2.0. | Aprovada |
| `evidencia6.png` | `CT-MET-01` | Resposta sobre garantia de 12 meses para geladeiras. | Aprovada |
| `evidencia7.png` | `CT-MET-02` | Resposta em inglês sobre prazo de entrega fora das capitais. | Aprovada |
| `evidencia8.png` | `CT-INJ-01` | Tentativa de injeção direta e resposta que manteve o prazo documentado. | Aprovada |
| `evidencia9.png` | `CT-INJ-02` | Tentativa de injeção indireta via RAG e resposta sobre promoção. | Aprovada |
| `evidencia10.png` | `CT-EST-01` | Resposta estruturada em JSON com dados da política de reembolso. | Aprovada por inspeção visual |

## 2. Evidências complementares de saída estruturada (Tópico 3)

| Arquivo | Caso de teste | Descrição | Status |
| :--- | :--- | :--- | :--- |
| `CT-EST-02-json-valido.png` | `CT-EST-02` | JSON com resposta, confiança e citação; conferido manualmente como conforme ao schema. | Recebida |
| `CT-EST-03-campo-citacoes-ausente.png` | `CT-EST-03` | JSON sem o campo obrigatório `citacoes`; não conformidade solicitada intencionalmente. | Recebida |
| `CT-EST-04-enum-invalida.png` | `CT-EST-04` | JSON com `confianca: "muito alta"` e sem `citacoes`; não conformidade solicitada intencionalmente. | Recebida |

## 3. Evidências do Laboratório de Prompts

As seis capturas documentam as execuções do Tópico 2 e dão suporte às respostas selecionadas para a auditoria de citações.

| Arquivo | Execução | Descrição |
| :--- | :--- | :--- |
| `LAB-P1-CORRETO.png` | P1 — somente DOC-01 | Pergunta direta; resposta sem citação explícita. |
| `LAB-P2-CORRETO.png` | P2 — somente DOC-01 | Prompt estruturado; resposta cita DOC-01. |
| `LAB-P3-CORRETO.png` | P3 — somente DOC-01 | Prompt com exemplo; resposta cita DOC-01. |
| `LAB-P1-CONFLITO.png` | P1 — DOC-01 + DOC-02 | Resposta identifica divergência e exibe duas citações. |
| `LAB-P2-CONFLITO.png` | P2 — DOC-01 + DOC-02 | Resposta identifica prazos divergentes e cita os documentos. |
| `LAB-P3-CONFLITO.png` | P3 — DOC-01 + DOC-02 | Resposta identifica prazos divergentes e cita os documentos. |

Os horários visíveis nas capturas são registros de horário e não foram usados como medidas de latência.
