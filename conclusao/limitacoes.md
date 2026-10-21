# Limitações da Avaliação

> **Propósito:** Apontar de maneira transparente as restrições metodológicas, técnicas e operacionais que delimitaram o escopo da avaliação da AV2.

---

## 1. Tarefa
Mapear e documentar os fatores limitantes da pesquisa e dos testes executados, garantindo a adequada contextualização dos resultados e prevenindo generalizações indevidas.

---

## 2. Análise do Artefato

### 2.1 Limitações Metodológicas e Técnicas
- **Tamanho da Amostra:** O corpus experimental é sintético e reduzido (5 documentos versionados em `base-de-conhecimento/`), e a avaliação concentrou-se em 6 execuções no laboratório de prompts (1 por combinação), 5 afirmações auditadas no Tópico 3 e 10 casos obrigatórios (mais 3 complementares de JSON), não capturando a variabilidade estatística de bases corporativas extensas.
- **Variabilidade Estocástica e Alias Mutável do Modelo:** O modelo utilizado (`Gemini Flash-Lite Latest`) é acessado via alias dinâmico (`latest`), cuja versão interna não é exposta pelo provedor e pode sofrer atualizações silenciosas ao longo do tempo, afetando a reprodutibilidade estrita.
- **Opacidade dos Parâmetros de Recuperação e Chunking:** A interface e a documentação consultada do Cherry Studio `v2.0.13` não detalham de forma transparente os parâmetros internos de divisão em *chunks* nem o modelo de embeddings utilizado na indexação local, exigindo avaliação caixa-preta baseada no comportamento observável.
- **Validação Manual de Saída Estruturada e Escopo de Testes:** A conformidade ao `fontes/esquema-saida.json` (`CT-EST-01` a `CT-EST-04`) foi verificada por inspeção manual (sem execução automatizada de parser no pipeline), o teste `CT-CTX-01` cobriu consulta sobre o próprio FAQ em vez de pergunta sem resposta na base, e os horários das capturas não constituem medição formal de latência.

---

## 3. Resultados
- **Impacto das Limitações nas Conclusões:** As limitações circunscrevem as conclusões ao recorte experimental avaliado (Cherry Studio `v2.0.13` + `Gemini Flash-Lite Latest` sobre corpus sintético controlado), mas não invalidam as evidências concretas obtidas quanto à superioridade de rastreabilidade dos prompts estruturados (`P2`/`P3`) sobre o prompt direto (`P1`) e à necessidade de validação formal de JSON Schema.
- **Trabalhos Futuros Recomendados:** (1) Automatizar a execução do script `fontes/validador/validador.py` em lote; (2) Executar múltiplas repetições por caso de teste com medição cronometrada de latência; e (3) Expandir os testes adversariais e de contexto ausente em bases documentais reais de maior volume.
