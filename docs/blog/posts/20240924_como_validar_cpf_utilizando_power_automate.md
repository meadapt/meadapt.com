---
date: 2024-09-24
draft: True
authors: [gabrielbdornas]
comments: true
categories:
  - Power Automate
---

# Como validei CPF com Power Automate Desktop e Python: um caso real

No post [5 motivos para aprender ferramentas de automação (RPA) URGENTE](../posts/20240914_5_motivos_para_aprender_automacao.md) falei da importância de se aprender e utilizar ferramentas de RPA, em especial o Power Automate Desktop[^1].
Hoje, vou compartilhar um caso real onde precisei usar o Automate para validar uma lista de CPFs.
O desafio envolveu a integração de um código Python para realizar essa tarefa, após algumas dificuldades com JavaScript.

<!-- more -->

Onde ganho eficiência nesta construção?
Na identificação automatizada de quais CPFs são inválidos pelo Automate.
Somente estes necessitarão algum tipo de ação humana.
Os válidos já estão válidos e, portanto, podemos dormir tranquilos.

![type:video](https://www.youtube.com/embed/OuPzJKwgxc0)

## Tentativa de utilização de JavaScript

Minha primeira tentativa foi com um script JavaScript.
Pedi ao [ChatGPT](https://chat.openai.com/) (1) para gerar um código que validasse CPFs e o colei diretamente na ação `Executar Javascript` do Power Automate.
{ .annotate }

1. :simple-openai: Caso você não conheça o ChatGPT e/ou tem curiosidade para entender melhor seu funcionamento, não hesite em entrar em contato no espaço abaixo reservado para comentários, ou através do nosso e-mail [faleconosco@meadapt.com](faleconosco@meadapt.com).

Esta abordagem não funcionou.
Após algumas tentativas, entendi que a versão do interpretador JavaScript do Automate provavelmente estava conflitando com o código criado pelo [ChatGPT](https://chat.openai.com/).
Decidi então mudar de estratégia.

## A Solução com Python

Eu então solicitei ao [ChatGPT](https://chat.openai.com/) um código em Python para a mesma tarefa.
O Power Automate oferece duas versões antigas de Python, a 2.7 e 3.4.
O que poderia dificultar um pouco o trabalho.

Como previsto, o código inicialmente não funcionou.
Após várias tentativas descobri que o interpretador Python da versão 3.4 do Automate não reconhecia um operador essencial para o algoritimo.
Por algum motivo o `%`, responsável por calcular o resto da divisão, não estava funcionando[^2].
Após alguns ajustes no código, consegui resolver o problema e o script de validação de CPF em Python finalmente funcionou.

O cript criado retorna o próprio CPF caso ele seja válido.
Caso contrário, a variável `cpf` do fluxo fica vazia[^3].
Configurei o fluxo para capturar esses resultados e atualizá-los em uma planilha de Excel.

Aqui está um resumo de como o fluxo funciona:

1. Abre uma planilha de Excel contendo uma lista de CPFs.
2. Verifica cada CPF, executando o código de validação.
3. Os resultados (válido ou inválido) são gravados em uma nova coluna da planilha.
4. Ao finalizar a verificação de todos os CPFs a planilha Excel é salva e fechada, encerrando o trabalho.

## Montando seu robô

O que estou te passando aqui é um protótipo de robô.
Não copie e cole cegamente as informações abaixo.
Entenda seu funcionamento e, caso precise, ajuste-o às suas necessidades.

Para dar vida ao seu robô, reaproveitando meu trabalho, e sem a necessidade de criar tudo do zero como eu, faça:

<div class="grid" markdown>

[:fontawesome-solid-1: :octicons-copy-16: __Copie o código do robô__]() (1) e cole em um novo fluxo Power Automate Desktop.
{ .card .annotate }

1. :man_raising_hand: Na nova aba que será aberta, basta apertar ++ctrl+a++ para selecionar todo código e ++ctrl+c++ para copiar.

[:fontawesome-solid-2: :material-application-variable: __Clique aqui para baixar a planilha modelo__](javascript:void(0);) (1).
{ #download-button .card .annotate path="assets/fornecedores.csv" fileName="fornecedores.xlsx" }

1. :woman_raising_hand: Qualquer modificação além da inclusão de mais CPFs na planilha modelo pode exigir modificações no código original do robô. Download desta planilha não é suportado na versão mobile desta página.

:fontawesome-solid-3: :material-application-variable: __Crie a variável de entrada__ `caminho_excel` com o caminho onde a planilha modelo foi salva.
{ .card }

:fontawesome-solid-4: :material-run: __Execute o fluxo__ e faça as adaptações que achar necessárias.
{ .card }

</div>

## Conclusão

Essa validação automatizada de CPF economiza tempo, já que a verificação manual de grandes listas não é mais necessária.
Além disso, comprovo que com o uso do Power Automate Desktop consigo criar processos ageis e eficientes para tarefas similares de validação de dados.

Se você quiser utilizar este fluxo na íntegra ou até mesmo enviar para um amigo basta seguir os passos descritos na sessão [Montando seu robô](#montando-seu-robo).
Assim, vocês poderão replicar o processo e automatizar a validação de CPFs em suas próprias listas.

Espero que tenha sido útil, e não se esqueça de colocar a mão na massa!
Lembre-se, você não aprendeu a andar de bicicleta apenas lendo um manual, teve que colocar em prática até conseguir.
Aqui é a mesma coisa!

--8<-- "docs/overrides/partials/blog/encontrou_erro.md"

[^1]: Não recebo qualquer compensação financeira ou benefício por indicar o Power Automate. Minha recomendação é baseada na experiência e na eficácia da ferramenta para automação de processos.
[^2]: O que é bem estranho porque na [documentação desta versão](https://docs.python.org/3.4/reference/lexical_analysis.html#operators:~:text=**%20%20%20%20%20%20/%20%20%20%20%20%20%20//-,%25,-%3C%3C%20%20%20%20%20%20%3E%3E%20%20%20%20%20%20%26) este operador (`%`) existe. Vida que segue.
[^3]: Esta foi minha decisão durante a revisão do script. Poderia ter retornado simplesmente `True` para CPF válido e `False` caso contrário.
