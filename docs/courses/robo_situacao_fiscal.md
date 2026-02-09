---
hide:
  - feedback
comments: true
---

# Perguntas e Respostas do Robô de Consulta da Situação Fiscal

## Quero saber mais

??? note "Qual o objetivo do curso?"

    O objetivo é oferecer uma automação que baixe o relatório fiscal de CNPJs previamente informados, trazendo eficiência e agilidade na gestão fiscal.

??? note "Quem é o público alvo?"

    Contadores e escritórios de contabilidade

??? note "O curso está sendo atualizado?"

    Sim, a cada atualização do Power Automate, que interfira no desempenho do robô, uma nova versão será desenvolvida e enviada aos alunos.

??? note "O acesso é vitalício?"

    Sim, o material ficará disponível para o aluno pela plataforma de compra e o códido disponibilizado é do aluno.

??? note "Quais tecnologias serão utilizadas?"

    As principais tecnologia usadas são a API da Serpro e o programa Power Automate Desktop da Microsoft.

??? note "Como funciona o suporte à dúvidas?"

    As dúvidas mais frequentes são respondidas na seção [Já estou fazendo o curso](#ja-estou-fazendo-o-curso).

    Caso não encontre o que precise ali, a plataforma do curso deverá ser utilizada para entrar em contato conosco.

    Para dúvidas ainda não respondidas na seção [Já estou fazendo o curso](robo_situacao_fiscal/#ja-estou-fazendo-o-curso) **a equipe da Me Adapt terá de 1 a 3 dias úteis para responder**.

??? note "Como funciona a matrícula e compra do curso?"

    O processo de compra e inscrição do curso pode ser feito através do link disponível [aqui](https://pay.hotmart.com/U100445894K?checkoutMode=10&bid=1769622267238).

??? note "Qual a política de reembolso?"

    Conforme a legislação de proteção ao consumidor, você pode solicitar o reembolso total da compra em até 7 dias.

??? note "Qual a taxa atual de reembolso?"

    A  taxa de reembolso está em 2.7% do total de compras.


## Já estou fazendo o curso

??? example "Onde ficam salvos os PDFs depois que o robô finaliza?"

    Os Pdfs ficam salvos na pasta que você definiu na variável `caminho_pasta`.

??? example "Por que o formato do cnpjs no excel está diferente do mostrado na aula?"

    Quando você edita o excel modelo que disponibilizado para os alunos, é possível que a informação do cnpj fique diferente, algo como: `3,7984583+13`.

    Isso não é um problema e o seu robô deve funcionar normalmente. No entanto, se você quer facilitar a sua visualização, você pode tentar alterar a formatação da coluna para texto.

??? example "Qual a forma correta de inserir o valor da variável `contratante` e `autor_pedido_dados`? "

    O valor dessas duas variáveis deve ser um cnpj sem barras, traços, pontos ou outro tipo de separador.

    - Forma **incorreta**: 38.938.851/0001-52 

    - Forma **correta**: 75285262000149

??? example "Por que o meu robô está retornando 'Consulta não realizada'?"

    Este retorno significa que o robô está funcionando e executou todo o fluxo. No entanto, a conexão com a API da Serpro retornou que não foi possível consultar o relatório fiscal.

    A causa mais frequente de falha de conexão é o preenchimento equivocado de informações pelo usuário. Verifique se todas as variáveis de entrada e as informações da planilha estão no formato correto (sem separadores como barras, pontos, espaços e traços).

??? example "Invoke-WebRequest: Não é possível validar o argumento no parâmetro 'Certificate'"

    Este retorno significa que o caminho para o certificado digital não está correto, ou o certificado não se encontra na pasta indicada. Um dos motivos pode ser a existência de uma contra barra "\" no final do caminho indicado. Exemplo:

    D:\relatorio_fical\certificate.pfx\

    A contra barra "\" no final do caminho indicado faz o Automate entender que você está informando um diretório e, portanto, ele não conseguirá achar o arquivo "certificate.pfx"
