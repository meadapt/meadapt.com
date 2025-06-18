---
date: 2025-06-16
draft: True
authors: [gabrielbdornas]
comments: true
categories:
  - GitHub
  - Automatizações
---

# Como usei o GitHub para automatizar uma tarefa simples, mas chata

Hoje, me deparei com um problema bem interessante no trabalho.
Sabe aquela típica tarefa que você faz todos os meses sem nem pensar muito?
Pois é...
**Por que eu não me tinha me livrado disso antes?**

<!-- more -->

Às vezes, a gente fica tão absorvido na correria do dia a dia que não tira um tempinho pra automatizar aquelas tarefas simples, mas que se repetem com frequência.
E olha, até pouco tempo atrás a gente até podia se enganar com aquela velha desculpa:

> _“Ah, isso aqui é tão rápido de fazer manual... deixa pra lá.”_

Mas se a pensarmos assim pra tudo, a gente vai ficar sempre atolado na rotina e nunca vai sobrar tempo pra melhorias, nem pra fazer coisas mais importantes e inteligentes.
Além idsso, hoje, com a ajuda da inteligência artificial, as soluções ficaram cada vez mais rápidas de serem construídas.

Pois bem.
A partir de hoje, essa tarefinha não tira mais nem um minuto do meu tempo!

## Mas afinal, qual era o problema?

Coisa simples.
Pegar um arquivo atualizado do **QlikView** e substituir o antigo no servidor.
Com isso, o painel passa a exibir as informações atualizadas e todo mundo fica feliz da vida. 🎉

Se você leu “QlikView” e já pensou em parar a leitura por não conhecer a ferramenta, calma aí!
Isso nem é relevante pra este post.

No lugar de "QlikView", é só pensar na palavra **arquivo**.

Sabe aquela vez que você precisou enviar um arquivo atualizado pro seu colega, pro seu time, ou pra algum sistema?
É disso que estamos falando.

O que eu precisava aqui era de uma forma de **automatizar o envio desse arquivo atualizado**.

## O cenário era esse:

- Meu colega de trabalho me enviava o arquivo (às vezes por e-mail, outras vezes por Teams ou por uma pasta no Google Drive).
- Depois, eu acessava um servidor (outro computador) e colocava esse arquivo numa pasta específica.

Pra quê?
Pra que o painel do QlikView (ou qualquer outra aplicação ou pessoa) pudesse usar a versão mais atualizada daquele arquivo.

## A ideia da automação foi:

- Criar um repositório no **GitHub** no qual os arquivos podem ser armazenados.
- Sempre que houver atualização, meu colega salva o arquivo novo no repositório (em vez de me enviar manualmente).
- O servidor roda, todo dia à meia-noite, um script que dá um `git pull` nesse repositório.
- Se tiver alteração, o arquivo novo é baixado automaticamente.

Pronto. Tá feito. O painel é atualizado, e ninguém mais precisa perder tempo com isso.

## Probleminhas no caminho... 🤦‍♂️

Claro que nem tudo são flores.
No meio do caminho, dois probleminhas apareceram:

1. **Arquivos maiores que 25 MB**, que o GitHub não permite subir de forma convencional[^1].
2. **Repositório privado**, que exige autenticação pro servidor conseguir fazer o `git pull`.

[^1]: [Sobre arquivos grandes no GitHub](https://docs.github.com/pt/repositories/working-with-files/managing-large-files/about-large-files-on-github).

## Como resolvi?

- Para o problema dos arquivos grandes, usei o **Git Large File Storage (LFS)**[^2].
- Para o problema da autenticação no repositório privado, usei um recurso chamado **Deploy Key**, porque o repositório estava no GitHub do meu colega (não era de uma organização).

[^2]: Documentação [Git lfs](https://git-lfs.com/) e post GitHub ["Sobre armazenamento de arquivo grande do Git"](https://docs.github.com/pt/repositories/working-with-files/managing-large-files/about-git-large-file-storage)

## Bora pra prática: como configurar tudo isso?

### 🔸Iniciando um repositório GitHub

1. [Iniciei um repositório no GitHub](https://docs.github.com/pt/repositories/creating-and-managing-repositories/quickstart-for-repositories) selecionando a opção para incluir um arquivo `README.md`.
2. Iniciei um [codespaces no meu novo repositório](https://docs.github.com/pt/codespaces/quickstart)[^3].
3. Adicionei o arquivo `.gitignore` no repositório com o seguinte conteúdo[^4].

[^3]: Para atualizar os arquivos poderei utilizar apenas o [editor de texto github.dev baseado na web](https://docs.github.com/pt/enterprise-cloud@latest/codespaces/the-githubdev-web-based-editor). Para mim, a maneira mais fácil para abrir este editor online é pressionar a techa ++period++ no teclado.
[^4]: Este [`.gitignore`](https://docs.github.com/pt/get-started/git-basics/ignoring-files) se baseou na minha necessidade. O seu, com toda certeza, deverá ser outro.

```yaml
# .gitignore file
# Ignore everything
*

# Except the files needed to update the panels
README.md
!.gitignore
!.gitattributes
!PainelSugesp.qvw
!Painel_EPPGG.qvw
```

### 🔸Configurando o Git LFS

O **Git LFS** é uma extensão do Git que permite versionar arquivos grandes, como planilhas pesadas, bancos de dados, imagens, etc.
Inicie e configure o `git lfs` com os comandos[^5]:

[^5]: Como estamos utilizando Codespaces não teremos a necessidade de instalar o `git lfs` na máquina, pois ele já vem instalado.

```yaml
# Inicia git lfs no repositório
git lfs install

# Inclui os arquivos .qvw na gestão lfs
git lfs track "*.qvw" # (1)

```

1. :man_raising_hand: Meu caso exigiu a configuração `git lfs` para arquivos .`qvw`, o seu, com grande certeza, deverá ser outro.

Depois de configurado, bastou adicionar os dois arquivos para o Codespaces (cliquei e arrastei os arquivos, bem fácil).

### 🔸Commitando tudo

```bash
git add .
git commit -m "Configurando lfs e adicionando arquivos."
git push origin main
```

### 🔸 Configurando o Deploy Key para repositório privado

O **Deploy Key** permite que uma máquina (no caso, o servidor onde preciso atualizar os arquivos) tenha acesso de leitura (ou leitura/escrita, se você quiser) a um repositório privado, sem depender de usuário e senha.

1. **No servidor, gere uma chave SSH:**

    ```bash
    ssh-keygen -t ed25519 -C "nome-do-servidor"
    ```

    👉 Quando ele perguntar onde salvar, você pode deixar o caminho padrão (`/home/usuario/.ssh/id_ed25519`) ou dar um nome específico.
    Eu preferi dar um nome específico pois essa chave vai ser utilizada somente neste repositório.

2. **Copie a chave pública:**

    ```bash
    cat ~/.ssh/id_ed25519_nome_servidor.pub
    ```

3. **No GitHub, entre no repositório e vá em:**

    `Settings` → `Deploy Keys` (fica no menu lateral) → `Add deploy key`

4. **Cole a chave pública lá.**

    Marque a opção **“Allow write access”** se quiser permitir que o servidor também envie alterações.
    Se for só pra baixar, como no meu caso, pode deixar desmarcada.

5. Edite seu arquivo `~/.ssh/config` para identificar a chave a ser utilizada.
Abra o arquivo com o comando `nano ~/.ssh/config` e inclua o conteúdo:

    ```yaml
    Host github-sugesp
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_ed25519_nome_servidor.pub # (1)!

    ```

    1. :man_raising_hand: O caminho e o nome do arquivo devem ser os mesmos utilizados na criação do mesmo.

6. **No servidor, teste se está funcionando:**

    ```bash
    ssh -T git@github.com
    ```

    Se aparecer uma mensagem como:

    ```text
    Hi usuario/repositorio! You've successfully authenticated, but GitHub does not provide shell access.
    ```

    Está tudo certo.

7. **Configure o remote com SSH, se ainda não tiver feito:**

```bash
# Navegue até a pasta onde os arquivos a serem atualizados vivem
cd ~/home/user/...

# Inicie git
git init

# Adicione o remote
git remote add origin git@github.com:usuario/repositorio.git
```

8. **Agora, seu script pode rodar normalmente:**

```bash
git pull origin main
```

## Resultado 🎉

Agora, meu colega não precisa mais me enviar arquivos.
Eu também não preciso mais acessar manualmente o servidor pra atualizar nada.

Basta ele atualizar o arquivo no GitHub e, na próxima execução do script no servidor (que roda todo dia à meia-noite), tudo está no lugar certo, atualizado e funcionando.

## Moral da história

Se tem uma coisa que aprendi hoje é:
**tarefas manuais e repetitivas são candidatas perfeitas para automação.**

E olha que, muitas vezes, a solução nem é tão complexa assim. Basta olhar pra sua rotina com um olhar mais crítico e questionar:

> _“Preciso mesmo continuar fazendo isso na mão?”_

Spoiler: provavelmente, **não.**

---

Se curtiu este post e quer aprender mais sobre automações no seu trabalho, seja com Git, Power Automate, Python ou outras ferramentas, continue me acompanhando por aqui. 🚀
