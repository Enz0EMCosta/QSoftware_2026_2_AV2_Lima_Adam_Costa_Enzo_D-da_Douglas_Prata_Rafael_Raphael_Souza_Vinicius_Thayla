# Comparação e Avaliação dos Prompts

> **Propósito:** Comparar P1 (Direto), P2 (Estruturado) e P3 (Few-Shot) com a mesma pergunta em contexto correto e conflitante, registrando as seis execuções sem antecipar resultados.

---

## 1. Tarefa
Executar seis ensaios no Cherry Studio: cada prompt deve ser testado uma vez com a base contendo somente o documento vigente `DOC-01` e uma vez com a base contendo `DOC-01` e a versão antiga `DOC-02`. Manter o modelo, a pergunta e as demais configurações constantes. Comparar suporte factual, tratamento do conflito, citações e concisão. Preencher os resultados somente depois de executar os ensaios.

---

## 2. Protocolo do experimento

### 2.1 Pergunta e condições

- **Pergunta única:** “Qual é o prazo para desistir da compra?”
- **Condição A — contexto correto:** selecionar uma Base de Conhecimento contendo somente `DOC-01` (política vigente). Resposta de referência: 7 dias corridos a partir do recebimento.
- **Condição B — contexto conflitante:** selecionar uma Base de Conhecimento contendo `DOC-01` e `DOC-02`. `DOC-01` informa 7 dias corridos e vigência desde 01/03/2026; `DOC-02` informa 15 dias corridos e publicação em 10/05/2024. O resultado ideal identifica a divergência, cita as duas versões e deixa claro que DOC-01 é a versão mais recente no corpus.
- **Controle:** usar a mesma versão/modelo do Gemini, modo de chat, configuração de recuperação, pergunta e idioma em todas as execuções. Alterar somente o prompt e a condição da base. Registrar alterações ou falhas de recuperação observadas; a presença de um documento na base não garante que ele foi recuperado.
- **Evidência:** salvar a resposta completa e, quando disponível, os trechos/fontes recuperados e a latência. Não incluir chave de API em capturas ou registros.

### 2.2 Matriz comparativa experimental

| Execução | Prompt | Condição / base selecionada | Fontes/trechos recuperados | Resposta observada (colar integralmente) | Avaliação factual e citação | Conflito tratado? | Latência / horário informado | Evidência |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `P-CIT-01` (P1) | A — somente `DOC-01` | Fonte não informada na resposta enviada | O prazo para desistir da compra é de até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar. | Factualmente correta; não apresentou citação explícita. | Não se aplica | Não informado | Resposta copiada pelo integrante |
| 2 | `P-CIT-02` (P2) | A — somente `DOC-01` | `DOC-01-politica-reembolso-v2.md` (fonte citada pelo modelo) | O prazo para desistir da compra é de até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar. Fonte: `DOC-01-politica-reembolso-v2.md` | Factualmente correta e com fonte identificada. | Não se aplica | 12:08 (latência não informada) | Resposta copiada pelo integrante |
| 3 | `P-CIT-03` (P3) | A — somente `DOC-01` | `DOC-01-politica-reembolso-v2.md` (fonte citada pelo modelo) | O prazo para desistir da compra é de até 7 (sete) dias corridos a partir do recebimento do produto, sem necessidade de justificativa. Fonte: `DOC-01-politica-reembolso-v2.md` | Factualmente correta e com fonte identificada; redação equivalente ao documento. | Não se aplica | 12:10 (latência não informada) | Resposta copiada pelo integrante |
| 4 | `P-CIT-01` (P1) | B — `DOC-01` + `DOC-02` | As duas fontes foram citadas pelo nome; trechos recuperados não informados | Há uma divergência entre os documentos encontrados na base:<br><br>- Versão atual (Versão 2.0, vigente desde 01/03/2026): O prazo para desistir da compra é de até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar 1. (Fonte: `DOC-01-politica-reembolso-v2.md`).<br>- Versão antiga (Versão 1.0, publicada em 10/05/2024): O prazo informado era de até 15 (quinze) dias corridos a partir do recebimento do produto 2. (Fonte: `DOC-02-politica-reembolso-v1-desatualizada.md`). | Correta; distingue as duas versões e cita os documentos. | Sim — aponta a divergência e identifica versão e data. | 12:16 (latência não informada) | Resposta copiada pelo integrante |
| 5 | `P-CIT-02` (P2) | B — `DOC-01` + `DOC-02` | Duas citações; trechos informados: DOC-01, “O cliente pode desistir da compra em até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar”; DOC-02, “O cliente pode desistir da compra em até 15 (quinze) dias corridos a partir do recebimento do produto” | Há uma divergência entre os documentos encontrados na base:<br><br>- Versão atual (Versão 2.0, vigente desde 01/03/2026): O prazo para desistir da compra é de até 7 (sete) dias corridos a partir do recebimento do produto, sem precisar justificar 1. (Fonte: `DOC-01-politica-reembolso-v2.md`).<br>- Versão antiga (Versão 1.0, publicada em 10/05/2024): O prazo informado era de até 15 (quinze) dias corridos a partir do recebimento do produto 2. (Fonte: `DOC-02-politica-reembolso-v1-desatualizada.md`). | Correta; apresenta as duas versões e cita os trechos que sustentam cada prazo. | Sim — aponta a divergência e identifica versão e data. | 12:16 (latência não informada) | Resposta e trechos copiados pelo integrante |
| 6 | `P-CIT-03` (P3) | B — `DOC-01` + `DOC-02` | Duas citações; mesmos trechos de DOC-01 e DOC-02 informados na execução 5 | Os documentos apresentam divergência devido à atualização da política:<br><br>- Versão 2.0 (vigente desde 01/03/2026): O prazo para desistir da compra é de até 7 (sete) dias corridos a partir do recebimento 1. Fonte: `DOC-01-politica-reembolso-v2.md`.<br>- Versão 1.0 (publicada em 10/05/2024): O prazo era de até 15 (quinze) dias corridos a partir do recebimento 2. Fonte: `DOC-02-politica-reembolso-v1-desatualizada.md`. | Correta; apresenta os prazos divergentes, versões/datas e fontes. | Sim — aponta a divergência e identifica versão e data. | 16:57 (latência não informada) | Resposta e trechos copiados pelo integrante |

Na Condição A, as três respostas informadas estão factualmente de acordo com o DOC-01. P2 e P3 citaram a fonte; P1 não apresentou citação explícita no texto enviado. Na Condição B, as três respostas identificaram a divergência, os prazos de 7 e 15 dias, as versões/datas e os nomes dos documentos. Foram informados trechos recuperados para P2 e P3; para P1, só foi informado o nome das fontes na resposta. Os horários 12:08, 12:10, 12:16 e 16:57 são horários exibidos/informados, não medidas de latência.

---

## 3. Resultados — preencher após as seis execuções

### 3.1 Conclusão justificada: qual prompt foi mais confiável?
- **Resultado observado:** nas seis execuções informadas, os três prompts responderam corretamente no cenário apenas com DOC-01; no cenário conflitante, os três identificaram a divergência entre as versões de 7 e 15 dias e citaram os documentos correspondentes. P2 e P3 tiveram trechos de apoio informados pelo integrante nas duas condições; P1 não teve trechos recuperados informados, embora a resposta tenha nomeado as fontes no cenário conflitante.
- **Conclusão para esta amostra:** P2 (estruturado) e P3 (few-shot) empataram como respostas mais rastreáveis: ambos citaram DOC-01 no contexto correto e, no cenário conflitante, apresentaram os dois documentos; também foram informados trechos de apoio para ambos. P1 acertou os fatos e reconheceu o conflito, mas não citou explicitamente uma fonte na resposta da Condição A. Assim, P1 foi menos completo quanto à rastreabilidade, enquanto não há evidência suficiente para declarar P2 ou P3 superior ao outro.
- **Justificativa baseada nos resultados:** nas seis respostas fornecidas, todos os prompts acertaram o prazo vigente e identificaram a divergência de 7 versus 15 dias. O critério de desempate observável é a citação explícita: P2 e P3 citaram fonte nas duas condições; para ambos foram informados trechos de apoio no contexto conflitante. Não há avaliação separada da qualidade/precisão das citações no contexto A além dos nomes dos arquivos citados.
- **Trade-offs observados (clareza, citações e concisão):** P1 foi mais curto, mas omitiu a citação no contexto correto. P2 foi mais explícito em regras e formato; P3 usou um exemplo e produziu resposta igualmente fundamentada nos resultados relatados. Latência comparável não foi medida.
- **Limitação:** uma execução por combinação (seis no total) não mede variabilidade entre respostas; repetir execuções seria necessário para avaliar estabilidade.
