---
date: 2024-10-07
draft: True
authors: [gabrielbdornas]
comments: true
categories:
  - RPA
  - Power Automate
---

# Dicas de como instalar a ferramenta de RPA Power Automate

Se você leu nosso post [5 motivos para aprender ferramentas de automação (RPA) URGENTE](../posts/20240914_5_motivos_para_aprender_automacao.md), deve estar doido para instalar e começar a utilizar o Power Automate.
Além disso, temos algumas dicas importantes para garantir que você aproveite 100% da ferramenta, mesmo na versão gratuita, que é excelente.

<!-- more -->

??? "Vídeo YouTube"

    ![type:video](https://www.youtube.com/embed/YtPN0AVckvg)

### Passo a passo para instalar o Power Automate:

!!! Tip "Dica"

    Se você encontrar qualquer dificuldade, faça uma pergunta no espaço do post reservado para comentários, no final da página, ou nos comentários do próprio vídeo [YouTube](https://youtu.be/YtPN0AVckvg) criado.

1. **Acesse a Microsoft Store**:
A maneira mais fácil de instalar o Power Automate no Windows é pela Microsoft Store.
O processo é o mesmo tanto no Windows 10 quanto no Windows 11.
Na loja, procure por **Power Automate** e selecione a opção de instalar ou obter o aplicativo.


2. **Faça login com uma conta Outlook**:
Embora o Power Automate seja gratuito, você precisará de uma conta de e-mail da Microsoft.
Caso ainda não tenha, o sistema solicitará que você crie uma.
É um processo simples e rápido.

3. **Primeiros passos no Power Automate**:
Após a instalação, faça o login com sua conta.
A interface inicial oferece opções de leitura e um tour pela ferramenta.
Recomendo explorar o tour para se familiarizar com carinha do sistema :slight_smile:.
O local onde você criará seus fluxos de automação está no campo superior esquerto, na opção **"Meus fluxos"**.

4. **Criação de um fluxo de teste**:
Clique em **"Meus fluxos"** para criar seu primeiro fluxo.
Dê um nome a ele, como "Teste Instalação".
A maioria dos fluxos envolve interação com navegadores, então uma das ações mais usadas é "Iniciar um novo Chrome".
Antes de selecioná-la confira a dica abaixo.

5. **Instalação da extensão Power Automate no Chrome**:
Como o Chrome é bastante utilizado, é necessário instalar nele a extensão do Power Automate.
Para isso, abra a [loja de extenções Google Chrome](https://chromewebstore.google.com/).
Na página de extensões, procure pela extensão **Power Automate**[^1] e instale-a.
Não esqueça de ativar a extensão após instalá-la, pois ela precisa estar ativada para funcionar corretamente.

6. **Executando o fluxo de teste**
Com a extensão instalada, vamos configurar nosso fluxo.
Ao selecionar a ação "Iniciar um novo Chrome", você deverá configurar para:
    - Abrir uma nova instância do navegador.
    - Definir `https://www.google.com` como a URL que o fluxo irá abrir.
    - Configurar o estado da janela (maximizado, minimizado ou normal). Sugiro maximizado.
    - Salve seu fluxo e clique em "Executar" para testar.

7. **Dica mais valiosa de todas:** Lembre-se de sempre salvar seu fluxo após incluir uma nova ação.

Pronto, seu fluxo abrirá uma nova instância do Chrome na página do Google.

### Conclusão

Instalar o Power Automate é um processo simples, mas requer atenção a alguns detalhes, como ter um e-mail da Microsoft e instalar a extensão para o Chrome.
Com isso, você estará pronto para criar fluxos automatizados e otimizar suas rotinas na internet.

Agora, se além de instalar você também estava aflito para criar um fluxo profissional, completo e do zero, não deixe de conferir o post [Aprenda RPA com Power Automate e construa sua primeira automação do zero](../posts/20241001_aprenda_rpa_com_power_automate_e_construa_sua_primeira_automacao_do_zero.md)

--8<-- "docs/overrides/partials/blog/encontrou_erro.md"

[^1]: Tome cuidado para não instalar a opção Legacy.
