??? Question

    O comportamento da função `round()` é baseado em uma regra chamada rounding half to even, também conhecida como arredondamento bancário. Essa regra dita como o Python lida com números que estão exatamente na metade entre dois inteiros (por exemplo, 2,5, 3,5, etc.).
    Em vez de sempre arredondar para cima, o Python arredonda para o número par mais próximo.
    Esse método ajuda a minimizar o viés de arredondamento em grandes conjuntos de dados.

    Aqui está como funciona:

    Para números que estão exatamente na metade entre dois inteiros, o Python arredonda para o número par mais próximo.

      - `round(2.5)` retorna 2 (arredondado para baixo, para o número par).
      - `round(3.5)` retorna 4 (arredondado para cima, para o número par).
      - Para números que não estão exatamente na metade, o Python os arredonda para o inteiro mais próximo, como de costume.
        - `round(2.4)` retorna `2`.
        - `round(2.6)` retorna `3`.

## Exercícios

1. Qual os resultados esperados para as expressões `round(42.5) ` e `round(43.5)` respectivamente?

<?quiz?>
question: Selecione a opção correta.
answer-correct: 42 e 44
answer: 42 e 43
answer: 43 e 44
content:
<?/quiz?>
