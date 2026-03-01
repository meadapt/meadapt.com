---
draft: false
authors: [gabrielbdornas]
comments: true
date:
  created: 2025-11-18
categories:
  - TOML
---

# Introdução ao TOML: o que é e como usar em poucos minutos

Neste post vou explicar **o que é o arquivo TOML**, o básico de sua especificação e como utilizar Python para interagir com ele.
Bora?

<!-- more -->

TOML é a sigla para **Tom’s Obvious Minimal Language**, introduzida em 2013 e nomeada humildemente pelo seu criador.
Ele prioriza humanos, segundo seu [site oficial](https://toml.io/pt/):

> TOML visa ser um formato de arquivo de configuração mínimo que seja fácil de ler devido à semântica óbvia. O TOML foi projetado para mapear inequivocamente para uma tabela hash. O TOML deve ser fácil de analisar em estruturas de dados em uma ampla variedade de idiomas.

TOML oferece sintaxe familiar: **strings, inteiros, floats, booleanos**.
Se você já usa Python, isso vai parecer natural.

A seguir, veremos como criar um arquivo TOML, como carregar esse arquivo em Python e como usar tabelas, subtabelas e outros recursos.

## Criando um arquivo TOML

Para começar, no diretório de sua preferência, crie um novo arquivo chamado `config.toml`:

```
touch config.toml
```

Esse arquivo vai armazenar as configurações do nosso projeto.

### Comentários

Em TOML, comentários usam o caractere `#`, exatamente como no Python:

```toml
# config.toml
# Arquivo de configuração
```

### Pares chave–valor

```toml
# config.toml
name = "my project"
version = "1.0.0"
website = "example.com"
```

## Carregando TOML no Python (Python 3.11+)

A partir do **Python 3.11**, temos o módulo nativo `tomllib` para carregar dados TOML.

Então no mesmo diretório que você criou o arquivo `config.toml` crie o `toml.py` e inclua o seguinte código:


```python
# toml.py
import tomllib
from pprint import pprint

def load_toml():
    with open('config.toml', 'rb') as f:
        toml_data = tomllib.load(f)
    return toml_data

if __name__ == '__main__':
    data = load_toml()
    pprint(data, sort_dicts=False)
```

Quando você executar esse script, verá algo como:

```bash
{'name': 'my project',
 'version': '1.0.0',
 'website': 'example.com'}
```

Qualquer modificação feita em `config.toml` será refletida diretamente quando você rodar o código novamente.

## Aprendendo mais sobre TOML

Agora que o script está funcionando, vamos testar diferentes recursos da linguagem TOML.

### Tabelas

Uma tabela agrupa valores relacionados:

```toml
# toml.py
[items]
numbers = [1, 2, 3]
letters = ["a", "b", "c"]
```

Isso gera um dicionário dentro de outro no Python.

Quando você executar o script `toml.py`, verá algo como:

```bash
{'name': 'my project',
 'version': '1.0.0',
 'website': 'example.com',
 'items': {'numbers': [1, 2, 3], 'letters': ['a', 'b', 'c']}}
```

### Subtabelas (tabelas aninhadas)

```toml
[items.details]
updated = true
author = "John Doe"
```

Agora, quando você executar o script `toml.py`, verá algo como:

```bash
'name': 'my project',
 'version': '1.0.0',
 'website': 'example.com',
 'items': {'numbers': [1, 2, 3],
           'letters': ['a', 'b', 'c'],
           'details': {'updated': True, 'author': 'John Doe'}}}
```

Detalhe importante, booleanos em TOML são sempre `true` e `false` (minúsculos).
Mas experimente executar o script no modo iterativo `python -i toml.py` e buscar o tipo de dado do valor booleano que inserimos:

```bash
>>> data
{'name': 'my project', 'version': '1.0.0', 'website': 'example.com', 'items': {'numbers': [1, 2, 3], 'letters': ['a', 'b', 'c'], 'details': {'updated': True, 'author': 'John Doe'}}}
>>> data.keys()
dict_keys(['name', 'version', 'website', 'items'])
>>> data['items']['details']['updated']
True
>>> type(data['items']['details']['updated'])
<class 'bool'>
```

## Chaves são sempre strings

Se você fizer:

```toml
# config.toml
10 = "value"
```

O TOML converte `10` automaticamente para string.
Quer conferir?
Basta utilizar o modo interativo novamente, `python -i toml.py`:

```bash
>>> data
{'name': 'my project', 'version': '1.0.0', 'website': 'example.com', '10': 'value', 'items': {'numbers': [1, 2, 3], 'letters': ['a', 'b', 'c'], 'details': {'updated': True, 'author': 'John Doe'}}}
>>> list(data.keys())[3]
'10'
>>> type(list(data.keys())[3])
<class 'str'>
```

## TOML não tem tipo `null`

Não existe `null`, `None` ou chave sem valor.
Caso você inclua alguma chave sem valor, você receberá um erro `tomllib.TOMLDecodeError: Invalid value` ao rodar o script `toml.py`.

## Suporte a UTF-8 e caracteres especiais

TOML usa UTF-8, então você pode usar símbolos como:

```toml
"ø" = "algum valor"
```

Chaves com símbolos precisam de aspas.
Se você executar o script `toml.py`, verá algo como:

```bash
{'name': 'my project',
 'version': '1.0.0',
 'website': 'example.com',
 '10': 'value',
 'ø': 'algum valor',
 'items': {'numbers': [1, 2, 3],
           'letters': ['a', 'b', 'c'],
           'details': {'updated': True, 'author': 'John Doe'}}}
```

## Subchaves (usando ponto)

A estrutura:

```toml
file.type = "sqlite"
file.path = "data.db"
```

É equivalente a estrutura:

```toml
[file]
type = "sqlite"
path = "data.db"
```

Experimente incluir uma de cada vez e você terá um resultado igual a:

```bash
{'name': 'my project',
 'version': '1.0.0',
 'website': 'example.com',
 '10': 'value',
 'ø': 'algum valor',
 'items': {'numbers': [1, 2, 3],
           'letters': ['a', 'b', 'c'],
           'details': {'updated': True, 'author': 'John Doe'}},
 'file': {'type': 'sqlite', 'path': 'data.db'}}
```

Mas cuidado, uma chave não pode ser declarada mais de uma vez.
Caso você tente incluir as duas estruturas como:

```toml
# config.toml
name = "my project"
version = "1.0.0"
website = "example.com"
10 = "value"
"ø" = "algum valor"
file.type = "sqlite"
file.path = "data.db"

[items]
numbers = [1, 2, 3]
letters = ["a", "b", "c"]

[items.details]
updated = true
author = "John Doe"

[file]
type = "sqlite"
path = "data.db"
```

Você receberá o erro `tomllib.TOMLDecodeError: Cannot declare ('file',) twice` ao tentar executar o arquivo `toml.py`.

## Tabelas inline

Você também pode criar tabelas assim:

```toml
inline = { name = "John Doe", age = 30 }
```

Mas isso pode deixar o arquivo confuso, então recomendo utilizar com moderação.

---

## Lista de tabelas

```toml
[[table_group]]
fruit = "Apple"
price = 1.5

[[table_group]]
fruit = "Orange"

[[table_group]]
fruit = "Banana"
```

O resultado é uma lista de dicionários no Python:

```bash
{'name': 'my project',
 'version': '1.0.0',
 'website': 'example.com',
 '10': 'value',
 'ø': 'algum valor',
 'items': {'numbers': [1, 2, 3],
           'letters': ['a', 'b', 'c'],
           'details': {'updated': True, 'author': 'John Doe'}},
 'file': {'type': 'sqlite', 'path': 'data.db'},
 'table_group': [{'fruit': 'Apple', 'price': 1.5},
                 {'fruit': 'Orange'},
                 {'fruit': 'Banana'}]}
```

## Timestamps

TOML suporta timestamps nativos:

```toml
[items.details]
timestamp = 2019-10-12T07:20:50Z
```

No Python, isso vira um objeto `datetime`.
Se quiser checar esta informação novamente, já sabe, `python -i toml.py`:

```bash
>>> data['items']['details']['timestamp']
datetime.datetime(2019, 10, 12, 7, 20, 50, tzinfo=datetime.timezone.utc)
>>> type(data['items']['details']['timestamp'])
<class 'datetime.datetime'>
```

## Conclusão

Minha intenção neste post foi te mostrar que o arquivo `.toml` não é nada assustador.
Bom, à primeira vista, ele parece sim um pouco assustador, mas com um pouquinho de esforço conseguimos simplificar um pouco seu entendimento, correto.

Confesso para você que para mim ele está se mostrando mais simples que o `.yaml`, por exemplo.
Inclusive, deve ser por isso que ele é considerado perfeito para arquivos de configuração.

Ficou com alguma dúvida?
Claro que ficou, pois este post não foi tão completo assim.
Então, sugiro como material suplementar:

- Vídeo YouTube [Everything about TOML format](https://www.youtube.com/watch?v=n9mGk8_tQtM).
- Vídeo YouTube [Learn TOML in 10 Minutes (Tutorial)](https://www.youtube.com/watch?v=D_Jb52jw2HY).

Bom, sugiro também o vídeo YouTube [Entendendo o arquivo pyproject.toml | Live de Python #257](https://www.youtube.com/watch?v=6p1HKaHrk0Y).
Aqui, o conteúdo é um pouquinho mais complexo e vai além do arquivo `.toml`, mas se você tiver tempo, acredito que irá se surpreender com o que é mostrado.
