---
date: 2024-09-29
draft: true
authors: [gabrielbdornas]
comments: true
categories:
  - Power Automate
---

# Construa seu primeiro fluxo RPA com Power Automate do zero

No post [5 motivos para aprender ferramentas de automação (RPA) URGENTE](./20240914_5_motivos_para_aprender_automacao.md){ target='_blank' } te mostrei a importância de aprender e utilizar ferramentas de RPA.
Em resumo, ganhamos tempo (nosso recurso mais preciosos), melhoramos a eficiência operacional e, em última análise, oferecemos serviços com maior qualidade.
Agora é o momento de te mostrar, na prática, como o **Power Automate** pode acabar com suas operações repetitivas.

<!-- more -->

Te darei neste post meu quite de sobrevivência para iniciantes.
Você sairá daqui com um fluxo que consulta de CEPs, pronto para uso.
Tudo isso com a explicação dos conceitos básicos necessários, claro.

![type:video](https://www.youtube.com/embed/ijJdrQYm6vM)

## RPA para consulta de CEPs

Mas afinal, como assim consulta de CEPs, você deve estar se perguntando.
Bom, consultaremos CEPs registrados em uma planilha do Excel para complementar, neste mesmo arquivo, as informações de logradouro, bairro, localidade e UF.

Você, com certeza, já se deparou com a necessidade de buscar informações de CEPs manualmente.
Talvez apenas um, caso se tratasse de alguma situação pessoal.
Mas já imaginou esta demanda em um ambiente corporativo onde a pesquisa seria necessária para levantar localidades para algum tipo de campanha publicitária.

Esta tarefa aparentemente simples, pode ser um bom exemplo de processo repetitivo e demorado.
Pense em uma lista de CEPs enorme para pesquisar.

Uma planilha Excel, composta por CEPs na coluna A, será a base de todo nosso trabalho.
As coluna `B`, `C`, `D` e `E` abrigarão os resultados consultados de logradouro, bairro, localidade e UF, respectivamente.
A coluna `F` será responsável por armazenar o status geral de cada consulta.

Daremos ênfase à:

- Utilização de ações na construção dos fluxos RPA.
- Criação e utilização de variáveis para armazenar dados essenciais ao longo da execução do fluxo.
- Utilização de estruturas condicionais (If/Else) para lidar com diferentes resultados de consulta.
- Criação de estruturas de repetição (Loop) para que a busca aconteça em todos os CEPs listados na planilha.

Ao compreendermos esses elementos, estaremos preparados para construir, praticamente, qualquer fluxo.

## Ações

São os blocos fundamentais que compõem a estrutura de um fluxo.
Elas representam passos individuais para realização de tarefas específicas e se combinam para formar um processo coeso.
Possuem, em geral, denominação similar às ações realizadas por nós, humanos.

São encontradas com auxílio da barra de pesquisa localizada no canto superior esquerdo do fluxo em construção.
Podem ser selecionadas com um clique duplo ou simplesmente sendo arrastadas.

Em outras palavras, são como instruções que dizem ao sistema o que deve ser feito.
Ao escolher qual ação queremos, quebramos nosso trabalho (o fluxo completo) em diversas tarefas menores, mais simples e fáceis de serem realizadas.

O Power Automate oferece uma ampla variedade de ações específicas para diferentes necessidades.
Por exemplo, `Enviar E-mail` possibilita a automação de comunicações, enquanto a ação `Aguardar página da Web` garante que a página da web esteja realmente carregada antes de sua manipulação, caso contrário nosso fluxo não executaria com sucesso.

### Exemplos Práticos de Ações[^2]

**Iniciar Novo Chrome**: Peça crucial para interações com navegadores.
Ela cria uma instância[^2] do navegador Chrome permitindo que o fluxo interaja com páginas da web de forma dinâmica.

**Iniciar Excel**: Abre uma instância[^2] do Microsoft Excel proporcionando a base para a manipulação eficiente de dados em planilhas.

**Ler da Planilha Excel**: Com ela podemos extrair dados específicos de uma planilha, como os CEPs que serão consultados no nosso exemplo.
Essa ação possibilita a interação com os dados existentes na instância[^2] Microsoft Excel desejada.

## Criação e utilização de variáveis

A utilização de variáveis desempenha um papel importante na eficiência, adaptabilidade e segurança de nossos fluxos.
Podem ser localizadas na lateral superior direita do fluxo em construção.
Variáveis permitem armazenar e utilizar informações dinamicamente durante a execução de nossos fluxos.
Pense nelas como uma caixinhas para guardar dados importantes.

Vamos explorar duas categorias principais de variáveis neste contexto: as variáveis de entrada e as variáveis de fluxo.

### Variáveis de Entrada

Garantem a segurança e a portabilidade do fluxo.
**Local para armazenar informações sensíveis, como logins e senhas, pois evitamos exposição direta desses dados no fluxo, contribuindo para práticas robustas de segurança.**

Além disso, como boa prática, recomendo utilizar variáveis de entrada para armazenar caminhos de arquivo, facilitamos a utilização do fluxo em diferentes computadores (adaptabilidade).
Esta prática não apenas aumenta a segurança, mas também simplifica a manutenção e compartilhamento do fluxo entre membros da equipe.

### Variáveis de fluxo

São variáveis criadas a longo do processo de automação.
Podem ser criadas pelo Power Automate ou por nós mesmos para armazenar informações temporárias.

Por exemplo, durante a interação com um navegador (como o Chrome) é criado uma variável para armazenar a instância[^2] do navegador aberto.
O mesmo se aplica durante a interação com o Excel, onde uma variável para armazenar a instância[^2] da planilha aberta é igualmente criada.
Também podem ser criadas para resultados de ações diversas, como a extração de dados de texto de páginas web.

Podemos listar uma infinidade de exemplos, mas o importante será entender
como essas variáveis são geradas e utilizadas.
Como boa prática, sugerimos sempre renomear[^3] as variáveis criadas pelo próprio Power Automate, dando a elas nomes que contenham um significado claro em relação à informação armazenada.
Isso facilitará a construção do fluxo, bem como sua manutenção.

## Estruturas condicionais

As estruturas condicionais do Power Automate são criadas utilizando-se as ações If e Else.
Elas são semelhantes a divisões de um caminho, permitindo que o fluxo de automação tome decisões com base em condições específicas.

Estas condições direcionam o fluxo do processo e proporcionam flexibilidade, pois permitem a execução de multiplas possibilidades, adaptando a automação conforme as regras do negócio.

Podemos usar o simples ato de atravessar a rua como exemplo.

Antes de atravessar uma rua olhamos para os dois lados.
Se (If) vejo algum carro vindo em algum dos lados aguardo e não atravesso.
Caso contrário (Else), não havendo nenhum carro avistado, posso atravessar tranquilamente.

??? note "**Clique e veja a estrutura condicional do fluxo de atravessar a rua.**"

    **Para facilitar o entendimento, a estrutura condicional foi destacada de laranja no fluxograma abaixo:**

    ```mermaid
      flowchart LR
          1((Início)) --> 2
          2[Chego para atravessar a rua] --> 3
          3[Olho para os dois lados]  --> 4
          4:::conditions
          4{Vejo algum carro?}
          4-->|Sim|5
          4-->|Não|6
          5[Aguardo]
          5:::conditions-->7
          6[Atravesso]
          6:::conditions-->7
          7((Fim))
          classDef conditions fill:#f96
    ```

Em nosso caso iremos configurar uma estrutura condicional para verificar se o CEP consultado existe.
Se (If) sim, registro logradouro, bairro, localidade e UF em nossa planilha, caso contrário (Else), registro `CEP não localizado` na coluna `F` (responsável por receber o status geral do trabalho).

??? note "**Clique e veja a estrutura condicional do fluxo de consulta de CEPs.**"

    **Para facilitar o entendimento, a estrutura condicional foi destacada de laranja no fluxograma abaixo:**

    ```mermaid
    flowchart TD
        1((Início)) --> 2
        2[Consultar CEPs] --> 3
        3:::conditions
        3{CEP existe}
        3-->|Não|4
        3-->|Sim|5
        4:::conditions
        4[Registra CEP não localizado] --> 6
        5:::conditions
        5[Registra informações] --> 6
        6((Fim))
        classDef conditions fill:#f96
    ```

## Estruturas de repetição (Loop)

Como o próprio nome indica, são ações criadas com objetivo de repetir determinado processo.
Melhorando nosso exemplo de atravessar a rua, devemos incluir um loop após a etapa aguardar, caso contrário aguardaremos eternamente ou não sairemos do lugar.

Após um tempo aguardando, volto a olhar para os dois lados e o processo se repete até o momento que não vejo nenhum carro e posso atravessar a rua com segurança.

??? note "**Clique e veja a estrutura de repetição do fluxo de atravessar a rua.**"

    **Para facilitar o entendimento, a estrutura condicional foi destacada de laranja no fluxograma abaixo:**

    ```mermaid
    flowchart LR
        1((Início)) --> 2
        2[Chego para atravessar a rua] --> 3
        3[Olho para os dois lados]  --> 4
        3:::conditions
        4{Vejo algum carro?}
        4:::conditions
        4-->|Sim|5
        4-->|Não|6
        5[Aguardo]-->3
        5:::conditions
        6[Atravesso]-->7
        7((Fim))
        classDef conditions fill:#f96
    ```

Para o Power Automate, **um loop permite que uma sequência de ações seja executada repetidamente** com base em condições específicas.
É como uma máquina que faz a mesma tarefa várias vezes de forma automática, economizando tempo e esforço.

Utilizaremos um loop em nossa lista de CEPS afim de realizarmos todas as nossas consultas.
Configuraremos a condição que permitirá ajustar, de maneira dinâmica, o número de repetições de acordo com o número de CEPs existentes na lista.

??? note "**Clique e veja o fluxo de consulta de CEPs completo.**"

    **Para facilitar o entendimento, a estrutura condicional foi destacada de laranja no fluxograma abaixo:**

    ```mermaid
    flowchart TD
        1((Início)) --> 2
        2[Consultar CEP] --> 3
        2:::conditions
        3[Registrar resultado no Excel] --> 4
        3:::conditions
        4{Todos CEPs consultados?}
        4:::conditions
        4-->|Sim|5
        4-->|Não|2
        5((Fim))
        classDef conditions fill:#f96
    ```
## Montando seu robô

No vídeo incluído no início do post está a construção detalhada de nosso fluxo RPA para consulta de CEPs.
**Para que você realmente aprenda, recomendo fortemente que além de assistir o vídeo, você repita todos os passos demonstrados no vídeo.**

Como prometido na introdução do post, incluo abaixo o código final do protótipo criado.
Ele servirá, entre outros, de molde para conferência o que você criou.

Siga as instruções abaixo para sua utilização.
Mas lembre-se, não copie e cole cegamente as informações abaixo.
Entenda seu funcionamento e, caso precise, ajuste-o às suas necessidades.

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

Penso que posso concluir dizendo que construir nosso primeiro fluxo RPA com o Power Automate pode parecer desafiador à primeira vista, mas com os conceitos certos conseguimos simplificar bem as coisas.

Ao explorar ações, variáveis e estruturas como loops e condicionais, você estará preparado para aplicar RPA em diferentes cenários do seu dia a dia profissional, economizando tempo e elevando a qualidade do trabalho.

Com o Power Automate, você tem o poder de transformar processos manuais em automações inteligentes, começando hoje mesmo!

[^1]: Não é nossa intenção aqui explicar todas as ações disponíveis, pois são muitas. Navegue nesta lista e tente, por conta própria, utilizar ações que te chamaram atenção, uma vez que suas configurações são, via de regra, bastante autoexplicativas.
[^2]: Instâncias no Power Automate são aplicativos abertos pelo fluxo, como um navegador ou uma planilha de Excel. Elas permitem que o Power Automate interaja diretamente com esses aplicativos, como se você estivesse clicando ou digitando neles.
[^3]: Não utilize espaços e ou caracteres especiais como acentos, cedilha e til, para renomear as variáveis de fluxo. Sugerimos a utilização de letras minúsculas, separadas por underscore (`_`) como em `resultado_pesquisa`.
