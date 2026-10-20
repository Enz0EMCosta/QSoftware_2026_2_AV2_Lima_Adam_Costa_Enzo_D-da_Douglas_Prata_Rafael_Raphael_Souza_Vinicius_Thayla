# Prompt P3 — Poucos Exemplos (Few-Shot)

> **Propósito:** Registrar a especificação e versionamento do Prompt Few-Shot (P3), fornecendo pares de demonstração (pergunta/contexto/resposta esperada) para condicionar o modelo a respostas factuais e no padrão desejado.

---

## 1. Tarefa
Especificar o prompt baseado em aprendizado por demonstrações (*few-shot prompting*), guiando o modelo através de exemplos positivos e negativos de extração de informação e rejeição de comandos maliciosos.

---

## 2. Análise do Artefato

### 2.1 Metadados do Prompt
- **ID do Prompt:** `P-CIT-03`
- **Nome:** Prompt com Poucos Exemplos (Few-Shot)
- **Técnica:** Few-Shot In-Context Learning
- **Versão:** 1.0.0

### 2.2 Estrutura e Exemplos Fornecidos ao Modelo
- **Exemplo único (fato sustentado por documento):**
  - Pergunta de exemplo: Quanto tempo de garantia têm os produtos de linha branca?
  - Contexto de exemplo: `DOC-04`: eletrodomésticos de linha branca têm 90 dias de garantia legal mais 9 meses de garantia contratual, totalizando 12 meses.
  - Resposta ideal: Os produtos de linha branca têm 12 meses de garantia no total. Fonte: `DOC-04`.
- **Nota:** o exemplo ensina o formato da resposta e não é uma fonte para responder à pergunta real sobre reembolso.

### 2.3 Conteúdo do Prompt (Texto Integral)
```text
Exemplo de resposta fundamentada:
Contexto de exemplo: DOC-04 informa que eletrodomésticos de linha branca têm 90 dias de garantia legal mais 9 meses de garantia contratual.
Pergunta de exemplo: Quanto tempo de garantia têm os produtos de linha branca?
Resposta ideal: Os produtos de linha branca têm 12 meses de garantia no total. Fonte: DOC-04.

Agora responda à pergunta abaixo usando somente os documentos recuperados pela Base de Conhecimento do Cherry Studio. O exemplo acima serve apenas para demonstrar como citar uma fonte; não o use como evidência para a resposta real. Se os documentos divergirem, informe a divergência, cite as versões/datas e não omita a versão antiga. Não invente informações. Responda em português do Brasil, em texto curto, com a fonte.

Pergunta: Qual é o prazo para desistir da compra?
```

---

## 3. Resultados
- **Pergunta escolhida para as seis execuções:** Qual é o prazo para desistir da compra?
- **Cenário com contexto correto:** selecionar na Base de Conhecimento somente o `DOC-01`.
- **Cenário conflitante:** selecionar uma base com `DOC-01` e `DOC-02`.
- **Importante:** manter a pergunta e as demais configurações do Cherry Studio iguais nas seis execuções. O contexto deve ser fornecido pela Base de Conhecimento selecionada no aplicativo, não copiado manualmente para o prompt.
- **Condições de Teste Avaliadas:**
  - **Condição A — somente `DOC-01`:** “O prazo para desistir da compra é de até 7 (sete) dias corridos a partir do recebimento do produto, sem necessidade de justificativa. Fonte: `DOC-01-politica-reembolso-v2.md`.” Avaliação: fato correto e documento citado.
  - **Condição B — `DOC-01` + `DOC-02`:** “Os documentos apresentam divergência devido à atualização da política:
    - Versão 2.0 (vigente desde 01/03/2026): O prazo para desistir da compra é de até 7 (sete) dias corridos a partir do recebimento 1. Fonte: `DOC-01-politica-reembolso-v2.md`.
    - Versão 1.0 (publicada em 10/05/2024): O prazo era de até 15 (quinze) dias corridos a partir do recebimento 2. Fonte: `DOC-02-politica-reembolso-v1-desatualizada.md`.”
    Avaliação: identificou corretamente a divergência, os prazos, as versões e as fontes. O integrante informou que os trechos apresentados eram os mesmos registrados na execução P2.
- **Síntese do P3:** resposta correta e com fontes nas duas condições; tratou explicitamente o conflito na Condição B. O exemplo incluído no prompt não substituiu as fontes recuperadas para a resposta.
- **Registro:** resultados transcritos a partir das respostas enviadas pelo integrante. Horários informados: 12:10 (A) e 16:57 (B); latências não informadas.
