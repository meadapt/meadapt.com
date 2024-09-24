---
date: 2024-09-24
draft: True
authors: [gabrielbdornas]
comments: true
categories:
  - Power Automate
---

# Como validei CPF com Power Automate e Python: um caso real

No post [5 motivos para aprender ferramentas de automação (RPA) URGENTE](../posts/20240914_5_motivos_para_aprender_automacao.md) falei da importância de se aprender utilizar ferramentas de RPA, em especial o Power Automate[^1].
Hoje, vou compartilhar um caso prático onde precisei usar Power Automate para validar uma lista de CPFs.
O desafio envolveu a integração de um código Python para realizar essa tarefa, após algumas dificuldades com JavaScript.

<!-- more -->

Onde ganho eficiência nesta construção?
Na identificação de quais CPFs são inválidos pelo Power Automate.
Somente estes necessitarão algum tipo de ação humana.
Os válidos já estão válidos e, portanto, podemos dormir tranquilos.

## Tentativa de utilização de JavaScript

Minha primeira tentativa foi com utilizar um script JavaScript.
Pedi ao ChatGPT para gerar um código que validasse CPFs e colei diretamente no Power Automate.
Embora o script funcionasse no navegador, ele gerava um erro de sintaxe quando tentava rodá-lo no Power Automate.

Após algumas tentativas, imaginei a versão do interpretador JavaScript do Automate provavelmente estava conflitando com o código criado pelo ChatGPT.
Como o código continuava a dar erro, decidi mudar de estratégia.

## A Solução com Python

Eu então solicitei ao ChatGPT um código em Python para a mesma tarefa.
O Power Automate oferece duas versões de Python, a 2.7 e 3.4, ambas antigas.

O código inicialmente não funcionou porque o Power Automate não reconhecia um operador essencial para o algoritimo, o `%`, responsável por calcular o resto da divisão.
Após alguns ajustes no código, consegui resolver o problema e o script de validação de CPF em Python finalmente rodou corretamente.

O código de validação de CPF em Python retorna o próprio CPF caso ele seja válido, não sendo nada informado para CPFs inválidos.
Configurei o fluxo para capturar esses resultados e atualizá-los em uma planilha de Excel.

Aqui está um resumo de como o fluxo funciona:

1. O fluxo abre uma planilha de Excel contendo uma lista de CPFs.
2. Ele verifica cada CPF, executando o código de validação.
3. Os resultados (válido ou inválido) são gravados em uma nova coluna da planilha.
4. O fluxo faz isso de maneira automática para todos os CPFs da lista.

## Conclusão

Essa validação automatizada de CPF economiza tempo, já que a verificação manual de grandes listas não é mais necessária.
Com o uso do Power Automate e do código Python, consigo criar um processo ágil e eficiente para tarefas similares de validação de dados.

Se você quiser testar esse fluxo vou disponibilizar, com o código Python e os passos necessários em um post aqui no site. Assim, você poderá replicar o processo e automatizar a validação de CPFs em suas próprias listas.

Espero que tenha sido útil, e não se esqueça de conferir os detalhes técnicos e o código completo no nosso próximo post!

--8<-- "docs/overrides/partials/blog/encontrou_erro.md"

[^1]: Não recebo qualquer compensação financeira ou benefício por indicar o Power Automate. Minha recomendação é baseada na experiência e na eficácia da ferramenta para automação de processos.
