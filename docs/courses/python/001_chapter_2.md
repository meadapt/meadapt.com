---
comments: true
---

# Capítulo 2: Variáveis e Instruções

No [capítulo anterior](001_chapter_1.md), usamos operadores para escrever expressões que realizam cálculos aritméticos.

Neste capítulo, você aprenderá sobre variáveis e instruções (1), a instrução `import` e a função `print`.
E apresentarei mais do vocabulário que usamos para falar sobre programas, incluindo "argumento" e "módulo".
{ .annotate }

1. :man_raising_hand_tone1: Do inglês statements.

## Variáveis

Um a **variável** é um nome que se refere a um valor.
Para criar uma variável, podemos escrever uma **instrução de atribuição** (1) como esta:
{ .annotate }

1. :man_raising_hand_tone1: Do inglês assignment statement.

```python
n = 17
```

Uma instrução de atribuição tem três partes:

1. O nome da variável à esquerda;
2. O operador de igualdade, `=`; e
3. Uma expressão à direita.
Neste exemplo, a expressão é um inteiro.
No seguinte exemplo, a expressão é um número de ponto flutuante.

```python
pi = 3.141592653589793
```

E no seguinte exemplo, a expressão é uma string.

```python
message = 'Python fica bem mais legal na MeAdapt.com!'
```

Quando você executa uma instrução de atribuição, não há saída.
O Python cria a variável e dá a ela um valor, mas a instrução de atribuição não tem efeito visível.
No entanto, após criar uma variável, você pode usá-la como uma expressão. Então podemos exibir o valor de `message` assim:

=== "Código"

    ```python
    message
    ```
=== "Resultado"

    ```python
    Python fica bem mais legal na MeAdapt.com!
    ```

Você também pode usar uma variável como parte de uma expressão com operadores aritméticos, como aqui:

=== "Código"

    ```python
    n + 25
    ```
=== "Resultado"

    ```python
    42
    ```
Ou aqui:

=== "Código"

    ```python
    2 * pi
    ```
=== "Resultado"

    ```python
    6.283185307179586
    ```

E você pode usar uma variável quando chamar uma função, como aqui:

=== "Código"

    ```python
    round(pi)
    ```
=== "Resultado"

    ```python
    3
    ```
Ou aqui:

=== "Código"

    ```python
    len(message)
    ```
=== "Resultado"

    ```python
    42
    ```

## Diagramas de Estado

Uma maneira comum de representar variáveis no papel é escrever o nome com uma seta apontando para seu valor.

```mermaid
stateDiagram
    direction LR
    n --> 17

    direction LR
    pi --> 3.141592653589793

    direction LR
    message --> B
    B as "Python fica bem mais legal na MeAdapt.com!"
```

Esse tipo de figura é chamado de **diagrama de estado** porque mostra qual estado cada uma das variáveis está (pense nisso como o estado mental da variável).

Usaremos diagramas de estado ao longo do curso para representar um modelo de como o Python armazena variáveis e seus valores.

## Nomes de Variáveis

Os nomes das variáveis podem ser tão longos quanto você quiser.
Eles podem conter letras e números, mas não podem começar com um número. É legal usar letras maiúsculas, mas é convencional usar apenas minúsculas para nomes de variáveis.

A única pontuação que pode aparecer em um nome de variável é o caractere de sublinhado, `_`. Ele é frequentemente usado em nomes com várias palavras, como `seu_nome` ou `velocidade_do_swallow_descarregado`.

Se você der a uma variável um nome ilegal, receberá um erro de sintaxe. O nome `million!` é ilegal porque contém pontuação.

```python
million! = 1000000
```

`76trombones` é ilegal porque começa com um número.

```python
76trombones = 'big parade'
```

`class` também é ilegal, mas pode não ser óbvio por quê.

```python
class = 'Self-Defence Against Fresh Fruit'
```

Acontece que `class` é uma **palavra-chave**, que é uma palavra especial usada para especificar a estrutura de um programa. As palavras-chave não podem ser usadas como nomes de variáveis.

Aqui está uma lista completa das palavras-chave do Python:

```
False      await      else       import     pass
None       break      except     in         raise
True       class      finally    is         return
and        continue   for        lambda     try
as         def        from       nonlocal   while
assert     del        global     not        with
async      elif       if         or         yield
```

Você não precisa memorizar esta lista. Na maioria dos ambientes de desenvolvimento, as palavras-chave são exibidas em uma cor diferente; se você tentar usar uma como nome de variável, saberá.
