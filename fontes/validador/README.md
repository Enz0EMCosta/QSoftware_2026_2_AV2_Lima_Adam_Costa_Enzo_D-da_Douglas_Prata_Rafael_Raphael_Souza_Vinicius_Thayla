# Validador de Saída Estruturada

> **Propósito:** Validar as respostas do modelo contra `fontes/esquema-saida.json`, testando falhas de sintaxe, campos obrigatórios ausentes e inconsistências de fonte.

---

## 1. Tarefa
Prover procedimentos e scripts de validação para verificar a integridade estrutural das respostas da IA, identificando erros comuns de formatação e quebra de esquema.

---

## 2. Análise do Artefato

### 2.1 Cenários de Validação
1. **JSON Inválido:** Respostas contendo delimitadores quebrados ou caracteres não escapados.
2. **Campo Obrigatório Ausente:** Respostas que omitirem `resposta`, `confianca` ou `citacoes`.
3. **URL / Documento Inexistente:** `id_documento` apontando para arquivo que não existe na base.
4. **Fonte que Não Sustenta:** Citação formalmente presente no JSON, mas cujo `trecho_apoio` não suporta semanticamente a resposta.

### 2.2 Exemplo de Script Validador em Python (`validador.py`)

Para executar `jsonschema.validate`, o ambiente precisa ter a dependência `jsonschema` instalada. O exemplo abaixo é apenas uma referência de implementação; não há script executável nem resultado de execução versionado nesta pasta até o momento.

```python
import json
import jsonschema

def validar_saida(caminho_schema, caminho_resposta):
    with open(caminho_schema, 'r', encoding='utf-8') as f:
        schema = json.load(f)
    
    with open(caminho_resposta, 'r', encoding='utf-8') as f:
        dados = json.load(f)
        
    try:
        jsonschema.validate(instance=dados, schema=schema)
        print("[SUCESSO] A saída cumpre rigorosamente o esquema JSON.")
        return True
    except jsonschema.ValidationError as err:
        print(f"[ERRO DE VALIDAÇÃO] {err.message}")
        return False
    except json.JSONDecodeError as err:
        print(f"[ERRO DE SINTAXE JSON] {err.msg}")
        return False

if __name__ == "__main__":
    # Execução de teste
    # validar_saida("../esquema-saida.json", "exemplo-resposta.json")
    pass
```

---

## 3. Resultados
- **Execuções do validador automatizado realizadas:** não registradas. As três saídas do Cherry Studio foram comparadas manualmente com o schema.
- **Resultado da inspeção manual:** CT-EST-02 conforme; CT-EST-03 não conforme por ausência de `citacoes`; CT-EST-04 não conforme por valor de `confianca` fora da enumeração e ausência de `citacoes`.
- **Taxa observada na bateria complementar:** 1 de 3 saídas conformes (33,3%). Duas saídas foram intencionalmente solicitadas fora do schema; essa taxa não representa o desempenho espontâneo do modelo. O T10 do conjunto original é registrado separadamente como CT-EST-01.
- **Observações:** erro sintático JSON e citação incompleta ainda não foram executados. Os detalhes e as evidências estão em `testes/saida-estruturada/README.md`.
