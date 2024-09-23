# Capítulo 1: Pensando como um Cientista da Computação

Este curso tem dois objetivos principais.
O primeiro é te ensinar a programar em Python.
Mas aprender a programar significa aprender uma nova forma de pensar, então o segundo objetivo é te ajudar a pensar como um cientista da computação.
Essa forma de pensar combina algumas das melhores características da matemática, engenharia e ciências naturais.

Assim como matemáticos, cientistas da computação usam linguagens formais para representar ideias, especificamente computações.
Como engenheiros, eles projetam coisas, reunindo componentes em sistemas e avaliando prós e contras entre alternativas.
Como cientistas, eles observam o comportamento de sistemas complexos, formulam hipóteses e testam previsões.

Começaremos com os elementos mais básicos da programação e seguiremos em frente. Neste capítulo, veremos como o Python representa números, letras e palavras.
E você aprenderá a realizar operações aritméticas.

Você também começará a aprender o vocabulário da programação, incluindo termos como operador, expressão, valor e tipo.
Esse vocabulário é importante e você precisará dele para entender o resto do livro, para se comunicar com outros programadores e para usar e entender assistentes virtuais.

## Operadores Aritméticos

Um operador aritmético é um símbolo que representa uma operação aritmética.
Por exemplo, o sinal `+` é utilizado para realizar adição:

=== "Código"

    ```python
    30 + 12
    ```
=== "Resultado"

    ```python
    42
    ```

O sinal `-` é utilizado para realizar subtração:

=== "Código"

    ```python
    43 - 1
    ```
=== "Resultado"

    ```python
    42
    ```

O sinal `*` é utilizado para realizar multiplicação:

=== "Código"

    ```python
    6 * 7
    ```
=== "Resultado"

    ```python
    42
    ```

O sinal `/` é utilizado para realizar divisão:

=== "Código"

    ```python
    84 / 2
    ```
=== "Resultado"

    ```python
    42.0
    ```

Observe que o resultado da divisão mostrada acima é `42.0` e não `42`.
Isso porque existem dois tipos de números em Python:

  - **Inteiros (int)**, que representam números inteiros.
  - **Números de ponto flutuante (float)**, que representam números com casas decimais.

Se você somar, subtrair ou multiplicar dois inteiros, o resultado será um inteiro (`int`).
Mas se você dividir dois inteiros, o resultado será um número de ponto flutuante (`float`).

O Python também fornece o operador `//`, que realiza a divisão inteira. O resultado da divisão inteira é sempre um inteiro:

=== "Código"

    ```python
    84 // 2
    ```
=== "Resultado"

    ```python
    42
    ```

A divisão inteira também é chamada de "floor division" (divisão de chão) porque sempre arredonda para baixo (em direção ao "chão"):

=== "Código"

    ```python
    85 // 2
    ```
=== "Resultado"

    ```python
    42
    ```

Por fim, o operador `**` eleva a um potência:

=== "Código"

    ```python
    7 ** 2
    ```
=== "Resultado"

    ```python
    49
    ```

??? Nota

    Em algumas outras linguagens, o circunflexo (`^`), é usado para exponenciação, mas em Python é um operador bitwise chamado XOR.
    Se você não está familiarizado com operadores bitwise, o resultado pode ser inesperado:

    === "Código"

        ``` python
        7 ^ 2
        ```

    === "Resultado"

        ``` markdown
        5
        ```

    Não abordarei operadores bitwise neste curso, mas você pode ler sobre eles em [neste link em inglês](http://wiki.python.org/moin/BitwiseOperators).

## Expressões

Uma coleção de operadores e números é chamada de expressão. Uma expressão pode conter qualquer vários operadores e números.
Por exemplo, aqui está uma expressão que contém dois operadores:

=== "Código"

    ```python
    6 + 6 ** 2
    ```
=== "Resultado"

    ```python
    42
    ```

Observe que a exponenciação acontece antes da adição.
Python segue a ordem de operações que você pode ter aprendido em uma aula de matemática: a exponenciação acontece antes da multiplicação e divisão, que acontecem antes da adição e subtração.

No seguinte exemplo, a multiplicação acontece antes da adição:

=== "Código"

    ```python
    12 + 5 * 6
    ```
=== "Resultado"

    ```python
    42
    ```

Se quiser que a adição aconteça primeiro, você pode usar parênteses.

```python
In [12]: (12 + 5) * 6
```

=== "Código"

    ```python
    (12 + 5) * 6
    ```
=== "Resultado"

    ```python
    102
    ```

Toda expressão tem um valor.
Por exemplo, a expressão `6 * 7` tem o valor `42`.

## Funções Aritméticas

Além dos operadores aritméticos, o Python fornece algumas funções que trabalham com números. Por exemplo, a função round pega um número de ponto flutuante e o arredonda para o número inteiro mais próximo.

```python
In [13]: round(42.4)
In [14]: round(4
