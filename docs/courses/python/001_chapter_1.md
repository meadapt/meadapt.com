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

Além dos operadores aritméticos, o Python fornece algumas funções que trabalham com números.
Por exemplo, a função `round` pega um `float` e o arredonda para o número inteiro mais próximo:

=== "Código"

    ```python
    round(42.4) #(1)
    ```

    1. :woman_raising_hand_tone4: Experimente passar os valores `4.5` e `4.6` para a função `round()`. O resultado final era o esperado por você?

=== "Resultado"

    ```python
    42
    ```


A função `abs` calcula o valor absoluto de um número.
Para um número positivo, o valor absoluto é o próprio número.

=== "Código"

    ```python
    abs(42)
    ```
=== "Resultado"

    ```python
    42
    ```

Para um número negativo, o valor absoluto é positivo.

=== "Código"

    ```python
    abs(-42)
    ```
=== "Resultado"

    ```python
    42
    ```

Quando usamos funções como essas, dizemos que estamos "chamando" a função.
Uma expressão que chama uma função é uma "chamada de função".

Quando você chama uma função, os parênteses são obrigatórios.
Se você os omitir, receberá uma mensagem de erro.

=== "Código"

    ```python
    abs 42
    ```
=== "Resultado"

    ```python
    File "<stdin>", line 1
        abs 42
            ^^
    SyntaxError: invalid syntax
    ```

Você pode ignorar a primeira linha dessa mensagem; ela não contém nenhuma informação que precisamos entender agora.
A segunda linha é o código que contém o erro, com acentos circunflexos (`^^`) abaixo dela para indicar onde o erro foi descoberto.

A última linha indica que este é um erro de sintaxe, o que significa que há algo errado com a estrutura da expressão.
Neste exemplo, o problema é que uma chamada de função requer parênteses.

Vamos ver o que acontece se você omitir os parênteses e o valor.

=== "Código"

    ```python
    abs
    ```
=== "Resultado"

    ```python
    <built-in function abs>
    ```

Um nome de função sozinho é uma expressão legal que tem um valor.
Quando é exibido, o valor indica que `abs` é uma função e inclui algumas informações adicionais que explicarei mais tarde.

## Strings

Além de números, o Python também pode representar sequências de letras, que são chamadas de strings (`str`), ou cadeias de caracteres porque as letras são enfileiradas como pedras em um colar.
Para escrever uma string, podemos colocar uma sequência de letras dentro de aspas simples.

=== "Código"

    ```python
    'Olá'
    ```
=== "Resultado"

    ```python
    Olá
    ```

Também é permitido usar aspas duplas.

=== "Código"

    ```python
    "Olá"
    ```
=== "Resultado"

    ```python
    Olá
    ```

Aspas duplas facilitam a escrita de uma string que contém um apóstrofo, que é o mesmo símbolo que uma aspa simples.

=== "Código"

    ```python
    "Copa d'água" # (1)
    ```

    1. :woman_raising_hand_tone4: Como você criaria uma `str` para um texto que contenha aspas duplas como em `Ele ironisou ao falar que está muito "preocupado" com a situação`?

=== "Resultado"

    ```
    Copa d'água
    ```

Strings também podem conter espaços, pontuação e dígitos.

=== "Código"

    ```python
    'Bem , . '
    ```
=== "Resultado"

    ```
    Bem , .
    ```

Quando você cria uma string, certifique-se de sempre usar aspas.
O acento grave, também conhecido como backtick, causa um erro de sintaxe.

=== "Código"

    ```python
    `Olá`
    ```
=== "Resultado"

    ```
    File "<stdin>", line 1
        `Olá`
        ^
    SyntaxError: invalid syntax
    ```

As aspas inteligentes, também conhecidas como aspas curtas, também não são permitidas.

=== "Código"

    ```python
    ‘Olá’
    ```
=== "Resultado"

    ```
    File "<stdin>", line 1
        ‘Olá’
        ^
    SyntaxError: invalid character '‘' (U+2018)
    ```

O operador `+` também funciona com strings.
Ele unifica duas ou mais strings em uma só, o que é chamado de concatenação.

=== "Código"

    ```python
    'Bem, gostaria de um ' + "copo d'água " + 'gelada.'
    ```
=== "Resultado"

    ```
    Bem, gostaria de um copo d'água gelada.
    ```

Da mesma forma, o operador `*` também funciona com strings.
Ele concatena várias cópias de uma mesma string.

=== "Código"

    ```python
    'Spam, ' * 4
    ```
=== "Resultado"

    ```
    Spam, Spam, Spam, Spam,
    ```

Os outros operadores aritméticos não funcionam com strings.

Por fim, também temos a função `len` que calcula o comprimento de uma string.

=== "Código"

    ```python
    len('Olá') # (1)
    ```

    1. :person_raising_hand_tone2: Observe são contadas apenas as letras entre as aspas, mas não as aspas.

=== "Resultado"

    ```
    3
    ```

## Valores e Tipos

Até agora, vimos três tipos de valores:

  - **2** é um inteiro.
  - **42.0** é um número de ponto flutuante.
  - **'Olá'** é uma cadeia de caracteres ou string.

Cada valor pertence a um tipo ou categoria.
O Python fornece a função chamada `type` que informa o tipo de qualquer valor.

O tipo de um inteiro é `int`:

=== "Código"

    ```python
    type(2)
    ```
=== "Resultado"

    ```
    <class 'int'>
    ```

O tipo de um número de ponto flutuante é `float`:

=== "Código"

    ```python
    type(42.0)
    ```
=== "Resultado"

    ```
    <class 'float'>
    ```

E o tipo de uma cadeia de caracteres é `str`.

=== "Código"

    ```python
    type('Olá, Mundo!')
    ```
=== "Resultado"

    ```
    <class 'str'>
    ```

Em todos os resultado mostrados acima para a função `type`, a palavra `class` é usada com sentido de categoria.
Um tipo é uma categoria deste valor.

Os tipos `int`, `float` e `str` podem ser usados como funções.
Por exemplo, `int` pode pegar um `float` e convertê-lo em um inteiro (sempre arredondando para baixo):

=== "Código"

    ```python
    int(42.9)
    ```
=== "Resultado"

    ```
    42
    ```

E `float` pode converter um inteiro em um valor de ponto flutuante:

=== "Código"

    ```python
    float(42)
    ```
=== "Resultado"

    ```
    42.0
    ```

Agora, aqui está algo que pode ser confuso.
O que você obtém se colocar uma sequência de dígitos entre aspas?
Pode parecer um número, mas na verdade é um `int`.

=== "Código"

    ```python
    type('126')
    ```
=== "Resultado"

    ```
    <class 'str'>
    ```

Se você tentar usá-lo como um número, poderá receber um erro.

=== "Código"

    ```python
    '126' / 3
    ```
=== "Resultado"

    ```python
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: unsupported operand type(s) for /: 'str' and 'int'
    ```
Este exemplo gera um `TypeError`, o que significa que os valores na expressão, chamados de `operands`, têm o tipo errado.
A mensagem de erro indica que o operador `/` não suporta os tipos desses valores, que são `str` e `int`.

Se você tiver uma cadeia de caracteres que contém dígitos, pode usar `int` para convertê-la em um inteiro.

```python
int('126') / 3
```

=== "Código"

    ```python
    int('126') / 3
    ```
=== "Resultado"

    ```python
    42.0 # (1)
    ```

    1. :woman_raising_hand_tone1: Lembre-se que o [resultado de uma divisão com operador `/`](#__tabbed_4_1) é um `float`.

Se você tiver uma cadeia de caracteres que contém dígitos e um ponto decimal, pode usar `float` para convertê-la em um número de ponto flutuante.

```python
float('12.6')
```

=== "Código"

    ```python
    float('12.6')
    ```
=== "Resultado"

    ```python
    12.6
    ```

Quando você escreve um grande inteiro, você pode ser tentado a usar vírgulas entre grupos de dígitos, como em `1,000,000`.
Esta é uma expressão válida em Python, mas o resultado não é um inteiro.

=== "Código"

    ```python
    1,000,000
    ```
=== "Resultado"

    ```python
    (1, 0, 0)
    ```

O Python interpreta `1,000,000` como uma sequência de inteiros separada por vírgulas.
Aprenderemos sobre esse tipo de sequência mais tarde.

Você pode usar `_` para tornar grandes números mais fáceis de ler.

=== "Código"

    ```python
    1_000_000
    ```
=== "Resultado"

    ```python
    1000000
    ```
## Linguagens Formais e Naturais

**Linguagens naturais**: São as línguas que as pessoas falam, como inglês, espanhol e francês.
Elas não foram projetadas por pessoas.
Elas evoluíram naturalmente.

**Linguagens formais**: São linguagens que são projetadas por pessoas para aplicações específicas.
Por exemplo, a notação que os matemáticos usam é uma linguagem formal que é particularmente boa em denotar relações entre números e símbolos.
Da mesma forma, as linguagens de programação são linguagens formais que foram projetadas para expressar computações.

Embora as linguagens formais e naturais tenham algumas características em comum, existem diferenças importantes:

  - **Ambiguidade:**: As linguagens naturais estão cheias de ambiguidade, que as pessoas lidam usando pistas contextuais e outras informações.
  As linguagens formais são projetadas para não serem ambiguas, o que significa que qualquer programa tem exatamente um significado, independentemente do contexto.
  - **Redundância:**: Para compensar a ambiguidade e reduzir mal-entendidos, as linguagens naturais usam redundância.
  Como resultado, elas são frequentemente prolixas.
  As linguagens formais são menos redundantes e mais concisas.
  - **Literalidade:**: As linguagens naturais estão cheias de idiomatismo e metáfora.
  As linguagens formais significam exatamente o que dizem.

Porque todos nós crescemos falando línguas naturais, às vezes é difícil ajustar às linguagens formais.
As linguagens formais são mais densas do que as linguagens naturais, por isso leva mais tempo para lê-las.

Além disso, a estrutura é importante, por isso nem sempre é melhor ler de cima para baixo, da esquerda para a direita.

Finalmente, os detalhes importam.
Pequenos erros de ortografia e pontuação, com os quais você pode se safar em línguas naturais, podem fazer uma grande diferença em uma linguagem formal.

## Depuração

Programadores cometem erros.
Por razões caprichosas, erros de programação são chamados de **bugs** e o processo de rastreá-los é chamado de **debugging**.

A programação, e especialmente o debug, às vezes trazem fortes emoções.
Se você estiver lutando com um bug difícil, você pode sentir raiva, tristeza ou vergonha.

Preparar-se para essas reações pode ajudá-lo a lidar com elas.
Uma abordagem é pensar no computador como um funcionário com certas forças, como velocidade e precisão, e fraquezas particulares, como falta de empatia e incapacidade de compreender o quadro geral.

Seu trabalho é ser um bom gerente: encontrar maneiras de tirar vantagem das forças e mitigar as fraquezas.
Você deverá encontrar maneiras de usar suas emoções para se envolver com o problema, sem deixar que suas reações interfiram na sua capacidade de trabalhar eficazmente.

Aprender a depurar pode ser frustrante, mas é uma habilidade valiosa e útil para muitas atividades além da programação.
No final de cada capítulo, há uma seção, como esta, com minhas sugestões para depuração.

Espero que ajudem!

## Glossário

- **Operador aritmético:** Um símbolo, como `+` e `*`, que denota uma operação aritmética como adição ou multiplicação.

- **Inteiro:** Um tipo que representa números inteiros ou da classe `int`.

- **Ponto flutuante:** Um tipo que representa números com partes fracionárias ou da classe `float`.

- **Divisão inteira:** Um operador, `//`, que divide dois números e arredonda para baixo para um inteiro (1).

- **Expressão:** Uma combinação de variáveis, valores e operadores.

- **Valor:** Um `int`, `float` ou `str`, ou um dos outros tipos de valores que veremos mais tarde.

- **Função:** Uma sequência nomeada de instruções que executa alguma operação útil.
As funções podem ou não receber argumentos e podem ou não produzir um resultado.

- **Chamada de função:** Uma expressão, ou parte de uma expressão, que executa uma função. Consiste no nome da função seguido por uma lista de argumentos entre parênteses.

- **Erro de sintaxe:** Um erro em um programa que o torna impossível de analisar, e portanto impossível de executar.

- **Cadeia de caracteres:** Um tipo que representa sequências de caracteres ou `str`.

- **Concatenação:** Juntar duas ou mais `str` de ponta a ponta.

- **Tipo:** Uma categoria de valores.
Os tipos que vimos até agora são inteiros `int`, números de ponto flutuante `float` e cadeias de caracteres`str`.

- **Operando:** Um dos valores sobre os quais um operador opera.

- **Linguagem natural:** Qualquer uma das línguas que as pessoas falam e que evoluíram naturalmente.

- **linguagem formal:** Qualquer uma das linguagens que as pessoas projetaram para propósitos específicos, como representar ideias matemáticas ou programas de computador.
Todas as linguagens de programação são linguagens formais.

- **Bug:** Um erro em um programa.

- **Debugging:** O processo de encontrar e corrigir bugs.
