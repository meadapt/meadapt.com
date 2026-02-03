---
hide:
  - feedback
comments: true
---

# Perguntas e Resposta do Robô de Consulta da Sitação Fiscal

## Quero saber mais

??? note "Qual o objetivo do curso?"

    O objetivo é oferecer uma automação que baixe o relatório fiscal de CNPJs previamente informados, trazendo eficiência e agilidade na gestão fiscal.

??? note "Quem é o público alvo?"

    Contadores e escritórios de contabilidade

??? note "O curso está sendo atualizado?"

    Sim, a cada atualização do Power Automate que intefira com o desempenho do robô. Uma nova versão será desenvolvida e enviada aos alunos.

??? note "O acesso é vitalício?"

    Sim, o material ficará disponível para o aluno pela plataforma de compra e o códido disponibilizado é do aluno.

??? note "Quais tecnologias serão utilizadas?"

    As principais tecnologia usadas são a API da Serpro e o programa Power Automate Desktop da Microsoft.

??? note "Como funciona o suporte à dúvidas?"

    As dúvidas devem ser enviadas na plataforma do curso e a equipe da Me Adapt irá responder com 1-3 dias.

??? note "Como funciona a matrícula e compra do curso?"

    O processo de compra e inscrição do curso pode ser feito através do link disponível [aqui](https://pay.hotmart.com/U100445894K?checkoutMode=10&bid=1769622267238)

??? note "Qual a política de reembolso?"

    Conforme a legislação de proteção ao consumidor, você pode solicitar o reembolso total da compra em até 7 dias.

??? note "Qual a taxa atual de reembolso?"

    A  taxa de reembolso está em 2.7% do total de compras.


## Já estou fazendo o curso

??? example "Onde ficam salvos os PDFs depois que o robô finaliza?"

    Os Pdfs ficam salvos na pasta que você definiu na variável `caminho_pasta`.

??? example "Por que o formato do cnpjs no excel está diferente do mostrado na aula?"

    Quando você edita o excel modelo que disponibilizado para os alunos, é possível que a informação do cnpj fique diferente, algo como: `3,7984583+13`.

    Isso não é um problema e o seu robô deve funcionar normalmente. No entanto, se você quer facilitar a sua vasualização, você pode tentar alterar a formatação da coluna para texto.

??? example "Qual a forma correta de inserir o valor da variável `contratante` e `autor_pedido_dados`? "

    O valor dessas duas variáveis deve ser um cnpj sem barras, traços, pontos ou outro tipo de separador.

    - Forma **incorreta**: 38.938.851/0001-52 

    - Forma **correta**: 75285262000149

??? example "Por que o meu robô está retornando 'Consulta não realizada'?"

    Este retorno significa que o robô está funcionando e executou todo o fluxo. No entanto, a conexão com a API da Serpro retornou que não foi possível consultar o relatório fiscal.

    A causa mais frequente de falha de conexão é o preenchimento equivocado de informações pelo usuário. Verifique que todas as variáveis de entrada e as informações da planilha estão no formato correto, sem separadores como barras, pontos, espaços e traços.
