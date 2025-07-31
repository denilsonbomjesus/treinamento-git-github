> Este treinamento pressupõe que você já tem o [Git](https://git-scm.com/downloads) instalado em sua máquina e uma conta ativa no [GitHub](https://github.com/).

# 📁 Treinamento Git e GitHub

Este repositório contém anotações úteis sobre comandos Git, links de referência, conceitos importantes e soluções para erros comuns.

-----

## O que é Git e GitHub?

Entender a diferença entre **Git** e **GitHub** é fundamental para quem começa a trabalhar com controle de versão.

### **Git**

O **Git** é um **sistema de controle de versão distribuído (VCS)**. Ele permite que você e sua equipe rastreiem alterações no código-fonte durante o desenvolvimento de software. Pense nele como uma ferramenta que tira "snapshots" do seu código em momentos específicos, permitindo que você retorne a versões anteriores, veja o histórico de alterações, e colabore com outras pessoas de forma organizada. Ele funciona localmente na sua máquina.

### **GitHub**

O **GitHub** é uma **plataforma de hospedagem de repositórios Git baseada na web**. Em outras palavras, é um serviço online que armazena seus projetos Git na nuvem. Além de hospedar o código, o GitHub oferece diversas funcionalidades sociais e colaborativas, como gerenciamento de **issues**, **pull requests**, wikis e muito mais, facilitando a colaboração em projetos de software. Existem outras plataformas semelhantes, como GitLab e Bitbucket.

### **Diferenças e Semelhanças**

| Característica | Git                                           | GitHub                                                 |
| :------------- | :-------------------------------------------- | :----------------------------------------------------- |
| **Natureza** | Software de controle de versão (local)        | Plataforma de hospedagem e colaboração (online)        |
| **Onde roda?** | Na sua máquina local                          | No navegador web, na nuvem                             |
| **Função** | Rastreia e gerencia alterações no código      | Hospeda repositórios, facilita colaboração, gerencia projetos |
| **Dependência** | O GitHub depende do Git para funcionar         | O Git não depende do GitHub para funcionar             |

-----

## Conceitos Fundamentais

Para trabalhar eficientemente com Git e GitHub, é importante entender alguns conceitos-chave:

### **Repositório (Repo)**

Um **repositório** é um diretório (pasta) onde o Git armazena todas as informações do seu projeto, incluindo todas as versões dos seus arquivos e o histórico de alterações. Pode ser local (na sua máquina) ou remoto (no GitHub).

### **Branch**

Uma **branch** (ramo) é uma linha independente de desenvolvimento. Quando você cria uma branch, você está criando uma cópia do seu código em um ponto específico no tempo, permitindo que você trabalhe em novas funcionalidades ou correções de bugs sem afetar a linha principal do projeto. É uma prática comum para isolar o desenvolvimento de diferentes funcionalidades.

#### **Branch Padrão (`main` ou `master`)**

Por padrão, quando você inicia um repositório Git, a branch principal é chamada de `master`. No entanto, o **GitHub mudou sua branch padrão de `master` para `main` em outubro de 2020**. Essa mudança foi para promover a inclusão e evitar termos com conotações de escravidão. Novos repositórios criados no GitHub agora usam `main` como branch padrão.

  * [Anúncio oficial do GitHub sobre a mudança para `main`](https://github.blog/changelog/2020-10-01-the-default-branch-for-newly-created-repositories-is-now-main/)

### **Commit**

Um **commit** é um "snapshot" das alterações no seu código em um determinado momento. Cada commit registra as mudanças feitas, quem as fez e uma mensagem descritiva. É a **unidade básica de trabalho no Git**. Existem padrões para a mensagem colocada no commit, e embora não seja obrigatório segui-los, é altamente recomendado para organizar o controle sobre o que é adicionado ao projeto.

  * [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/)
  * [Padrões de Commits (Commit Patterns)](https://dev.to/renatoadorno/padroes-de-commits-commit-patterns-41co)

### **Issue**

No GitHub, uma **Issue** é uma forma de rastrear tarefas, bugs, melhorias ou perguntas relacionadas ao projeto. Elas funcionam como itens de uma lista de tarefas, permitindo que a equipe discuta e gerencie o trabalho.

### **Pull Request (PR)**

Um **Pull Request** é uma proposta de integração de alterações de uma branch para outra (geralmente da sua branch de funcionalidade para a branch `main`). Ele permite que outros colaboradores revisem seu código, discutam as mudanças e sugiram melhorias antes que o código seja mesclado ao projeto principal.

### **Organização**

No GitHub, uma **Organização** é uma conta compartilhada por várias pessoas, geralmente usada por empresas ou grandes projetos de código aberto. Ela permite que equipes gerenciem repositórios, membros e permissões de forma centralizada.

-----

## ⚙️ Configuração Inicial do Git (`git config`)

Antes de começar a usar o Git, é importante configurá-lo com suas informações. O comando `git config` permite definir opções de configuração para o Git.

```bash
git config --list
```

Lista todas as configurações do Git.

### **Flags `--local` e `--global`**

As flags `--local` e `--global` determinam o escopo da sua configuração:

  * **`--local`**: As configurações são aplicadas apenas ao **repositório atual**. Se você estiver dentro de um repositório Git, essas configurações terão precedência sobre as configurações globais.
  * **`--global`**: As configurações são aplicadas a **todos os repositórios Git no seu sistema**. Estas são as configurações padrão para qualquer novo repositório que você criar.

Se nenhuma flag for especificada, o Git assume `--local` se você estiver em um repositório, ou `--global` se não estiver em um repositório.

### **Configurações Essenciais (com `--global`)**

É fundamental configurar seu nome de usuário e e-mail, pois essas informações serão associadas aos seus commits.

  * **`git config --global user.name "Seu Nome"`**
    Define o nome de usuário que será exibido nos seus commits.

  * **`git config --global user.email seu.email@exemplo.com`**
    Define o e-mail que será associado aos seus commits.

  * **`git config --global init.defaultBranch main`**
    Define a branch padrão para `main` ao inicializar novos repositórios localmente, alinhando com a prática atual do GitHub. Se você não configurar isso, o padrão ainda pode ser `master` dependendo da sua versão do Git.

### **Como Consultar Configurações Específicas**

Você pode consultar uma configuração específica sem listar todas elas. Por exemplo:

```bash
git config user.name
```

Este comando retornará apenas o valor configurado para `user.name`.

  * [Documentação Oficial Git - Configuração Inicial](https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Configura%C3%A7%C3%A3o-Inicial-do-Git)

-----

## Criando um Repositório no GitHub (Interface Web)

Criar um repositório no GitHub é o primeiro passo para hospedar seu projeto online.

1.  **Entre no GitHub:** Faça login na sua conta do GitHub.

2.  **Novo Repositório:** No canto superior direito, clique no sinal de **`+`** (mais) e selecione **"New repository"** (Novo repositório).

3.  **Nome do Repositório:** Digite um nome para o seu repositório (ex: `meu-primeiro-projeto`). Escolha um nome claro e conciso.

4.  **Descrição (Opcional):** Adicione uma breve descrição do seu projeto.

5.  **Público ou Privado:**
      * **Público:** O repositório será visível para qualquer pessoa na internet. É ótimo para projetos de código aberto.
      * **Privado:** O repositório só será visível para você e para as pessoas com quem você compartilhar explicitamente. Ideal para projetos pessoais ou confidenciais.

6.  **Inicializar com um `README.md` (Opcional, mas recomendado):** Marcar esta opção cria um arquivo **`README.md`** automaticamente no seu repositório. O `README.md` é um arquivo de [**linguagem Markdown**](https://docs.github.com/pt/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax), um sistema de marcação simples que permite formatar texto de forma fácil, usando símbolos para títulos, listas, negrito, itálico e muito mais. No contexto de um repositório, o `README.md` é um arquivo especial: ele é exibido automaticamente na página principal do seu repositório no GitHub, servindo como a **principal documentação do projeto**. É o primeiro lugar onde as pessoas que visitam seu repositório procuram informações sobre o que o projeto faz, como instalá-lo, como usá-lo e como contribuir. Por isso, é altamente recomendado iniciar com um `README.md` para fornecer um contexto claro e imediato ao seu projeto.

7.  **Adicionar `.gitignore` (Opcional):** Você pode escolher um template de **`.gitignore`** para a linguagem ou framework que está usando. O `.gitignore` é um arquivo essencial que **instrui o Git a ignorar certos arquivos e pastas**, impedindo que eles sejam rastreados pelo controle de versão. Isso é crucial para manter seu repositório limpo e focado apenas no código-fonte relevante. Por exemplo, arquivos de cache, diretórios de dependências de pacotes (`node_modules/`, `venv/`), arquivos de configuração sensíveis ou arquivos gerados automaticamente pela sua IDE são exemplos comuns de itens que devem ser listados no `.gitignore`. Ao ignorar esses arquivos, você evita adicionar ruído ao histórico do seu projeto e previne problemas de compatibilidade entre diferentes ambientes de desenvolvimento.
  * [Como usar o .gitignore: Uma introdução prática com exemplos](https://www.datacamp.com/pt/tutorial/gitignore)

8.  **Escolher uma Licença (Opcional):** Adicionar uma licença ao seu projeto define como outras pessoas podem usá-lo. Para projetos de código aberto, licenças como MIT ou Apache 2.0 são comuns.

9.  **Criar Repositório:** Clique em **"Create repository"** (Criar repositório).

Pronto\! Seu repositório agora está no GitHub. O próximo passo seria cloná-lo ou conectar seu projeto local a ele.

  * [Documentação Oficial GitHub - Criar um repositório](https://docs.github.com/pt/repositories/creating-and-managing-repositories/creating-a-new-repository)

-----

## 📦 Inicializando e Conectando um Repositório

### **Inicializando Repositório Local (`git init`)**

```bash
git init
```

Cria um novo repositório Git vazio dentro da pasta atual. Isso inicializa o rastreamento de versões para o seu projeto.

**IMPORTANTE:** Caso ocorra qualquer tipo de erro ou alguma configuração incorreta gere problemas, é possível redefinir o Git no diretório local. Para isso, basta excluir a pasta oculta **.git**, que é criada automaticamente após a execução do comando `git init`.

Essa pasta não é exibida por padrão, sendo necessário habilitar a visualização de arquivos ocultos no sistema para localizá-la. A exclusão pode ser feita manualmente, como qualquer outro arquivo ou pasta.

Após a remoção, o repositório Git será completamente desvinculado do diretório. Para iniciar uma nova configuração, recomenda-se fechar o terminal (por exemplo, o Git Bash), reabri-lo e executar novamente o comando `git init`, seguindo então com os passos de configuração desde o início.

### **Verificando Status (`git status`)**

```bash
git status
```

Mostra o estado atual do seu repositório: quais arquivos foram modificados, quais estão na área de staging (preparados para o próximo commit) e quais são novos ou não estão sendo rastreados. É um comando essencial para acompanhar seu trabalho.

### **Associando Repositório Remoto (`git remote add origin`)**

```bash
git remote add origin <link do repositório no GitHub>
```

Associa o seu repositório local a um repositório remoto no GitHub. O termo **`origin`** é um apelido padrão usado para se referir ao repositório remoto principal. Embora você possa usar outro nome no lugar de `origin`, é uma convenção comum e recomendada. Se você tiver múltiplos repositórios remotos (por exemplo, um para produção e outro para desenvolvimento), poderá dar nomes diferentes a eles.

**IMPORTANTE:** Verifique se o link utilizado no comando é **exatamente** o mesmo do repositório desejado. Caso haja qualquer diferença, corrija o link para que corresponda integralmente ao endereço correto do repositório.

**IMPORTANTE:** Na maioria dos sistemas operacionais, recomenda-se colar o link no terminal Git Bash utilizando o **mouse**, e não o teclado. No caso do sistema Windows, caso prefira colar utilizando o teclado, utilize a combinação de teclas **Ctrl + Shift + Insert**.

  * [Documentação oficial GitHub - Gerenciando repositórios remotos](https://docs.github.com/en/get-started/git-basics/managing-remote-repositories)
  * [Documentação oficial GitHub - Criar e deletar branchs](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository)

-----

## 📥 Puxando do GitHub (`git pull`)

**IMPORTANTE:** Antes de enviar qualquer alteração para o GitHub, **sempre puxe as alterações mais recentes do repositório remoto para o seu repositório local.** Isso evita conflitos e garante que você esteja trabalhando com a versão mais atualizada do código.

```bash
git pull origin <branch>
```

Puxa as alterações do repositório remoto (`origin`) para a branch especificada no seu repositório local. Por exemplo, `git pull origin main` puxará as alterações da branch `main` remota.

### **Erros Comuns Relacionados a Puxar do GitHub**

Se você tentar enviar alterações sem antes puxar, pode encontrar erros como:

  * **`![rejected] master -> master (fetch first)`**
    Este erro indica que suas alterações foram rejeitadas porque o repositório remoto tem alterações que você não possui localmente. A solução é puxar as alterações remotas primeiro (`git pull origin <branch>`) e então tentar enviar novamente.

      * [Solução no StackOverflow](https://stackoverflow.com/questions/28429819/rejected-master-master-fetch-first)
      * Este erro pode ocorrer se você tiver feito alterações diretamente no GitHub (ex: editado um arquivo, criado uma branch) e não as puxou para o seu ambiente local antes de tentar um `git push`.

  * **`fatal: refusing to merge unrelated histories`**
    Este erro geralmente acontece quando você tenta mesclar dois históricos de repositório que não têm um commit inicial comum. Isso pode ocorrer se você inicializou um repositório localmente com `git init` e depois tentou associá-lo a um repositório GitHub que já tinha commits. Para resolver, você pode forçar a fusão (com cuidado, pois pode sobrescrever o histórico) ou puxar com a opção `--allow-unrelated-histories`:

    ```bash
    git pull origin <branch> --allow-unrelated-histories
    ```

      * [Como resolver na comunidade Umbler](https://community.umbler.com/br/t/resolvendo-o-erro-fatal-refusing-to-merge-unrelated-histories-no-git/657)

-----

## ➕ Adicionando Arquivos (`git add`)

```bash
git add .
```

Adiciona todos os arquivos modificados ou novos para a **área de staging**. A área de staging (ou index) é um local intermediário onde você prepara as mudanças que farão parte do próximo commit.

### **Adicionando Arquivos Específicos**

Se você quiser adicionar apenas arquivos específicos, pode usar:

```bash
git add nome-do-arquivo.txt
git add pasta/outro-arquivo.js
```

### **Adicionando Múltiplos Arquivos por Padrão**

Você também pode usar curingas para adicionar arquivos com um determinado padrão:

```bash
git add *.html
git add docs/
```

O primeiro comando adicionaria todos os arquivos `.html` na pasta atual, e o segundo adicionaria todos os arquivos na pasta `docs/`.

-----

## 💬 Realizando Commit (`git commit`)

```bash
git commit -m "mensagem do commit"
```

Salva as alterações que estão na área de staging no seu repositório local. A **mensagem do commit** é crucial, pois deve descrever de forma clara e concisa o que foi alterado naquele commit. Boas mensagens de commit facilitam o entendimento do histórico do projeto.

-----

## 🚀 Enviando para o GitHub (`git push`)

```bash
git push origin <branch>
```

Envia as alterações do seu repositório local para o repositório remoto (`origin`) na branch especificada. Por exemplo, `git push origin main` enviará suas alterações para a branch `main` no GitHub.

  * [Documentação Oficial Git - Push](https://git-scm.com/docs/git-push)

-----

## 🌿 Trabalhando com Branches

O controle de branches é uma das funcionalidades mais importantes do Git, permitindo o desenvolvimento paralelo e organizado.

### **Listando Branches**

```bash
git branch
```

Lista todas as branches locais no seu repositório. A branch atual será destacada.

```bash
git branch -a
```

Lista todas as branches locais e remotas.

### **Criando uma Nova Branch**

```bash
git branch <nome da nova branch>
```

Cria uma nova branch localmente, mas não muda para ela.

### **Trocando entre Branches (`git checkout`)**

```bash
git checkout <nome da branch existente>
```

Muda para uma branch existente. Você precisa salvar ou fazer commit de suas alterações antes de trocar de branch, ou usar `git stash` para guardá-las temporariamente.

#### **Destaque: Criando e Trocando para uma Nova Branch (`git checkout -b`)**

```bash
git checkout -b <nome da nova branch>
```

Este é um atalho muito comum e útil. Ele **cria uma nova branch e, imediatamente, muda para ela**. É equivalente a executar `git branch <nome da nova branch>` seguido por `git checkout <nome da nova branch>`.

  * [git checkout - Documentação oficial](https://git-scm.com/docs/git-checkout)
  * [Como criar uma nova branch no GitHub - StackOverflow PT](https://pt.stackoverflow.com/questions/411048/como-criar-uma-nova-branch-no-github)

-----

## 📥 Clonando Repositório (`git clone`)

```bash
git clone <link do repositório no GitHub>
```

Cria uma cópia completa de um repositório Git remoto (localizado no GitHub, por exemplo) para o seu computador local. Ao clonar, ele automaticamente:

1.  Cria uma pasta com o nome do repositório.
2.  Baixa todo o histórico do projeto.
3.  Configura a conexão remota (`origin`) para o repositório original.
4.  Cria uma branch local (`main` ou `master`) rastreando a branch remota correspondente.

### **Implicações do Clone e Cuidados**

  * **Histórico Completo:** Você terá acesso a todas as versões do projeto.

  * **Colaboração:** É o ponto de partida ideal para colaborar em projetos existentes.

  * **Cuidado com Acesso:** Certifique-se de ter permissões adequadas (se for um repositório privado) para clonar.

  * **Evite Clonar e Pushar sem Entender:** Se você não pretende contribuir com o projeto original, mas apenas ter uma cópia para estudo ou modificação pessoal, considere fazer um **Fork** (explicado abaixo) ao invés de um clone direto de um repositório que você não possui permissão de escrita.

  * [Guia oficial para clonar repositórios GitHub](https://docs.github.com/pt/repositories/creating-and-managing-repositories/cloning-a-repository)

-----

## 🍴 Fork

Um **Fork** no GitHub é uma cópia pessoal de um repositório de outra pessoa ou organização. Ele permite que você faça alterações em um projeto sem afetar o repositório original. É uma forma comum de contribuir para projetos de código aberto.

### **Como Fazer um Fork**

O Fork é feito diretamente na interface do GitHub:

1.  Navegue até o repositório que você deseja "forkar".
2.  No canto superior direito da página do repositório, clique no botão **"Fork"**.
3.  O GitHub criará uma cópia do repositório em sua própria conta.

### **Implicações e Fluxo de Trabalho**

  * **Repositório Público:** O repositório "forkado" será público por padrão (se o original for público). Você pode alterá-lo para privado se o GitHub permitir para sua conta e o tipo de repositório.
  * **Sua Cópia:** O fork é sua cópia pessoal do projeto. Você tem controle total sobre ele.
  * **Colaboração com o Projeto Original:** Se você fizer alterações no seu fork e quiser que elas sejam incorporadas ao projeto original, você precisará abrir um **Pull Request** (Requisição de Pull) do seu fork para o repositório original.

### **Comandos Após o Fork (Local)**

Após fazer o fork no GitHub, você precisará cloná-lo para sua máquina local:

```bash
git clone <link do seu repositório forked no GitHub>
```

Agora, você pode fazer suas alterações, commitar e enviar para o **seu fork** no GitHub:

```bash
git add .
git commit -m "Minhas alterações"
git push origin main
```

Para manter seu fork atualizado com o repositório original (upstream), você precisará adicioná-lo como um novo remote e puxar as alterações:

```bash
git remote add upstream <link do repositório original>
git pull upstream main
```

  * [Guia oficial GitHub para fazer fork de um repositório](https://docs.github.com/pt/get-started/quickstart/fork-a-repo)

-----

## ❗ Erros Comuns e Soluções

### **`fatal: invalid branch name: init.defaultBranch =`**

Este erro geralmente ocorre devido a uma sintaxe incorreta ao tentar configurar a branch padrão inicial. A mensagem `init.defaultBranch =` sugere que o valor da branch padrão não foi especificado corretamente.

  * **Solução:** Certifique-se de que você está definindo a branch padrão com um nome válido, como `main` ou `master`, sem espaços em branco ou caracteres inválidos no final da atribuição. Por exemplo:
    ```bash
    git config --global init.defaultBranch main
    ```
  * [Solução no StackOverflow](https://stackoverflow.com/questions/64349920/git-error-fatal-invalid-branch-name-init-defaultbranch)

-----

### **`![rejected] master -> master (fetch first)`**

  * **Causa:** Suas alterações locais não podem ser enviadas porque o repositório remoto tem alterações que você não possui. Isso significa que alguém enviou algo para a branch remota enquanto você estava trabalhando.
  * **Solução:** Primeiro, puxe as alterações remotas para sua branch local usando `git pull origin <branch>`. Resolva quaisquer conflitos de mesclagem que possam surgir e, em seguida, tente fazer o `git push` novamente.
      * [Solução no StackOverflow](https://stackoverflow.com/questions/28429819/rejected-master-master-fetch-first)

-----

### **`fatal: refusing to merge unrelated histories`**

  * **Causa:** Ocorre quando você tenta mesclar ou puxar de um repositório que tem um histórico de commits completamente diferente do seu repositório local. Isso pode acontecer, por exemplo, se você criou um repositório no GitHub com um README.md e depois inicializou um repositório localmente e tentou conectá-los.
  * **Solução:** Se você tem certeza de que deseja mesclar os históricos, use a flag `--allow-unrelated-histories` ao puxar:
    ```bash
    git pull origin <branch> --allow-unrelated-histories
    ```
    **Cuidado:** Use esta opção apenas se você realmente deseja combinar os dois históricos.
      * [Como resolver na comunidade Umbler](https://community.umbler.com/br/t/resolvendo-o-erro-fatal-refusing-to-merge-unrelated-histories-no-git/657)

-----

### **`You have not concluded your merge (MERGE_HEAD exists)`**

  * **Causa:** Este erro indica que uma operação de mesclagem (merge) anterior não foi concluída corretamente. Isso pode acontecer se houver conflitos de mesclagem que não foram resolvidos ou se a mesclagem foi interrompida.
  * **Solução:**
    1.  Verifique o status para identificar os arquivos com conflito: `git status`.
    2.  Resolva os conflitos nos arquivos (remova as marcações `<<<<<<<`, `=======`, `>>>>>>>`).
    3.  Adicione os arquivos resolvidos à área de staging: `git add <arquivos-resolvidos>`.
    4.  Conclua a mesclagem com um commit: `git commit`. Se você não quiser concluir a mesclagem e desfazer tudo, pode usar `git merge --abort`.
    <!-- end list -->
      * [Solução no StackOverflow](https://stackoverflow.com/questions/11646107/you-have-not-concluded-your-merge-merge-head-exists)
      * [Hora de Codar - Solução](https://horadecodar.com.br/resolver-o-erro-you-have-not-concluded-your-merge/)

-----

## 🛠️ Outras Dicas

### **Commit não funciona?**

Se você está tendo problemas para fazer um commit ou push, verifique os seguintes pontos:

  * **Arquivos na área de staging:** Você adicionou os arquivos à área de staging com `git add .` ou `git add <arquivo>`?

  * **Mensagem de commit:** Você incluiu uma mensagem de commit com a flag `-m`?

  * **Branch correta:** Você está na branch correta para o commit/push?

  * **Puxar antes de enviar:** Você puxou as últimas alterações do repositório remoto antes de tentar enviar (`git pull origin <branch>`)?

  * **Credenciais Git:** Suas credenciais Git estão configuradas corretamente (nome de usuário e e-mail)? Você pode verificar com `git config --list`.

  * [Discussão no fórum da Alura 'Erro ao execultar git push'](https://cursos.alura.com.br/forum/topico-erro-ao-execultar-git-push-74711)

-----

## 🌐 Publicando Páginas com GitHub Pages

O **GitHub Pages** é um serviço de hospedagem de sites estáticos gratuito diretamente do seu repositório GitHub. É uma ótima maneira de hospedar portfólios, blogs, documentações de projetos e até mesmo pequenos sites pessoais ou de negócios.

### **Como Funciona**

O GitHub Pages funciona publicando o conteúdo de uma branch específica (geralmente `main` ou `gh-pages`) do seu repositório. Quando você ativa o GitHub Pages para um repositório, o GitHub serve seu conteúdo como um site.

### **O que é Preciso**

1.  **Repositório GitHub:** Você precisa ter um repositório no GitHub.
2.  **Conteúdo HTML, CSS, JS:** Seu site precisa ser composto por arquivos estáticos (HTML, CSS, JavaScript, imagens, etc.).
3.  **Branch de Publicação:** Você designa uma branch específica (ex: `main`, `gh-pages` ou uma pasta `docs/` dentro da `main`) para ser a fonte dos arquivos do seu site.

### **Relação com Repositórios Públicos e Privados**

  * **Repositórios Públicos:** Você pode publicar sites do GitHub Pages a partir de repositórios públicos gratuitamente. O URL do site será no formato `username.github.io/repository-name` ou `orgname.github.io/repository-name`.
  * **Repositórios Privados:** Para publicar sites do GitHub Pages a partir de repositórios privados, você geralmente precisa de uma conta GitHub Pro, Team ou Enterprise. O acesso ao site pode ser restrito se o repositório for privado.

### **O que significa ter uma página publicada no GitHub Pages**

Significa que seu conteúdo web estático está acessível publicamente (ou de forma restrita, se for um repositório privado com conta Pro/Team) através de uma URL fornecida pelo GitHub. Não há necessidade de configurar um servidor web separado ou pagar por hospedagem para sites simples.

### **Passos para Ativar (via interface GitHub)**

1.  Vá para o seu repositório no GitHub.
2.  Clique em **"Settings"** (Configurações).
3.  No menu lateral esquerdo, clique em **"Pages"**.
4.  Em "Source" (Fonte), escolha a branch que contém o seu site (geralmente `main`) e a pasta (se for o caso, como `/docs`).
5.  Clique em **"Save"** (Salvar).

O GitHub levará alguns minutos para construir e publicar seu site. Uma mensagem indicará o URL da sua página quando estiver pronta.

  * [Documentação oficial GitHub Pages](https://docs.github.com/pt/pages)

-----

## 🚀 Tópicos Avançados

## `.gitattributes`

O arquivo **`.gitattributes`** é uma ferramenta do Git que permite configurar atributos específicos para caminhos ou tipos de arquivo dentro do seu repositório. Ele gerencia como o Git lida com certos arquivos, especialmente em cenários mais complexos de desenvolvimento ou colaboração.

### O que é e Para que Serve?

Em sua essência, o `.gitattributes` é um arquivo de texto simples que você coloca na raiz do seu repositório (ou em subdiretórios, se quiser aplicar atributos localmente). Ele define regras para diferentes arquivos com base em seus nomes, extensões ou caminhos, controlando como o Git os trata em operações como `diff`, `merge`, `checkout`, e muitas outras.

Seu principal propósito é garantir consistência no comportamento do Git, melhorar a experiência do desenvolvedor e otimizar a forma como o repositório é gerenciado, especialmente em equipes ou projetos com diversos tipos de arquivo.

### O que Pode ser Usado?

O `.gitattributes` pode ser usado para:

  * **Normalização de quebras de linha:** Garante que todos os colaboradores usem o mesmo tipo de quebra de linha (`LF` ou `CRLF`), evitando problemas de compatibilidade entre sistemas operacionais.
  * **Identificação de arquivos binários:** Ajuda o Git a reconhecer arquivos binários, o que melhora a visualização de diferenças (`diff`) e a manipulação de mesclagens para esses arquivos.
  * **Controle de fusão (merge) de arquivos específicos:** Permite definir estratégias de fusão personalizadas para determinados tipos de arquivo.
  * **Geração automática de arquivos:** Pode ser usado para "limpar" ou "smudgar" arquivos durante `checkout` e `commit`, útil para gerar versões otimizadas ou formatadas.
  * **Exibição de diffs específicos:** Permite que o Git use ferramentas de diff externas ou regras personalizadas para tipos de arquivo complexos (como imagens, documentos de texto com formatação, etc.).

### Tipos de Atributos e Configurações Principais

Dentro do `.gitattributes`, você define regras no formato `padrão atributo1 atributo2...`. O `padrão` pode ser um nome de arquivo, uma extensão (`*.txt`), um caminho (`src/data/**`), etc.

Alguns dos atributos mais comuns e suas configurações:

  * **`text`**: Define como o Git deve lidar com quebras de linha em arquivos de texto.
      * `*.txt text`: Trata todos os arquivos `.txt` como texto, normalizando as quebras de linha.
      * `*.sh text eol=lf`: Garante que scripts shell sempre usem quebras de linha `LF` (Unix-style).
      * `*.bat text eol=crlf`: Garante que arquivos batch sempre usem quebras de linha `CRLF` (Windows-style).
      * `*.png binary`: Informa ao Git que arquivos `.png` são binários, desabilitando a tentativa de diffs de texto neles.
  * **`merge`**: Define estratégias de fusão específicas.
      * `*.xml merge=union`: Usa a estratégia "union" para mesclar arquivos XML, que tenta incluir todas as linhas de ambas as versões.
  * **`diff`**: Permite configurar como o Git gera as diferenças (`diffs`).
      * `*.docx diff=word`: Indica que arquivos `.docx` devem ser comparados usando uma ferramenta de diff externa específica para documentos Word.
  * **`linguist`**: Usado para informar ao GitHub (especificamente ao Linguist, que detecta linguagens) como tratar certos arquivos para estatísticas de linguagem.
      * `*.vue linguist-language=JavaScript`: Diz ao Linguist para tratar arquivos Vue como JavaScript para as estatísticas de linguagem do repositório.
  * **`export-ignore`**: Impede que arquivos ou diretórios sejam incluídos em arquivos `.zip` gerados pelo GitHub (por exemplo, ao baixar o repositório).
      * `/build/ export-ignore`: Exclui a pasta `build` de exports.
  * **`filter`**: Configura filtros de "limpeza" (clean) e "smudge" (smudge) que executam um programa em um arquivo quando ele é adicionado ao index ou quando é feito um `checkout`.
      * `*.js filter=js-formatter`: Pode ser usado para formatar automaticamente arquivos JavaScript ao fazer commit (`clean`) ou reverter a formatação ao fazer checkout (`smudge`). Isso é mais avançado e geralmente envolve configurar o filtro no `.git/config` também.

### Quando é Indicado Usar?

O `.gitattributes` é especialmente indicado em cenários como:

  * **Projetos multi-plataforma:** Para garantir que desenvolvedores em Windows, macOS e Linux não enfrentem problemas com quebras de linha.
  * **Projetos com diversos tipos de arquivo:** Ao lidar com arquivos binários, documentos, ou formatos específicos que se beneficiam de tratamento especial no Git.
  * **Padronização de código:** Para impor formatação automática ou outras transformações via filtros.
  * **Melhora da legibilidade do histórico:** Ao configurar diffs inteligentes para arquivos não-texto.
  * **Otimização do tamanho do repositório:** Usando filtros para "limpar" arquivos antes de serem armazenados.

### Vantagens de Usar o `.gitattributes`

  * **Consistência:** Garante que todos na equipe sigam as mesmas regras de Git para o tratamento de arquivos.
  * **Menos conflitos:** Ajuda a prevenir conflitos de mesclagem relacionados a quebras de linha ou formatos de arquivo.
  * **Histórico mais limpo:** Evita commits desnecessários de mudanças insignificantes (como alteração de quebra de linha).
  * **Melhor experiência de desenvolvimento:** Simplifica o trabalho com diferentes tipos de arquivos e automações.
  * **Centralização:** As regras são versionadas junto com o código, facilitando a colaboração e a integração contínua.

### Links de Referência

  * [Documentação Oficial do Git - `gitattributes`](https://git-scm.com/docs/gitattributes)
  * [Para que serve o arquivo .gitattributes?](https://pt.stackoverflow.com/questions/437894/para-que-serve-o-arquivo-gitattributes)
  * [Overrides - Using gitattributes](https://github.com/github-linguist/linguist/blob/main/docs/overrides.md)

-----

## Git LFS (Large File Storage)

Quando você trabalha com Git, especialmente em projetos que incluem muitos **arquivos grandes**, como imagens de alta resolução, vídeos, modelos 3D ou grandes conjuntos de dados, o repositório pode inchar rapidamente, tornando as operações Git lentas e o armazenamento ineficiente. É aqui que o **Git LFS (Large File Storage)** entra em cena.

### O que é Git LFS?

O **Git LFS** é uma extensão de código aberto para o Git que foi projetada para lidar com arquivos grandes de forma eficiente. Em vez de armazenar o conteúdo desses arquivos diretamente no repositório Git (o que acontece com arquivos de texto e código), o Git LFS os substitui por **ponteiros de texto leves**. O conteúdo real dos arquivos é armazenado em um servidor remoto separado (geralmente fornecido pela sua plataforma Git, como GitHub, GitLab ou Bitbucket).

Quando você clona um repositório ou faz `checkout` de uma branch, o Git LFS baixa automaticamente apenas as versões dos arquivos grandes que você precisa, em vez de todo o histórico de todas as versões. Isso resulta em:

  * **Clones mais rápidos:** O tamanho inicial do repositório é significativamente reduzido.
  * **Operações Git mais leves:** `fetch`, `pull` e `push` se tornam mais eficientes.
  * **Melhor desempenho geral:** O Git não precisa lidar com grandes objetos binários em seu histórico principal.

### Como o Git LFS Funciona e a Relação com `.gitattributes`

A chave para o funcionamento do Git LFS está no arquivo **`.gitattributes`**. É nesse arquivo que você informa ao Git quais tipos de arquivos devem ser gerenciados pelo LFS.

Primeiro, você precisa **instalar o Git LFS** e configurá-lo uma vez por sistema:

```bash
git lfs install
```

Em seguida, para que o Git LFS comece a rastrear arquivos específicos, você adiciona uma linha ao seu arquivo **`.gitattributes`** que associa a extensão ou o caminho do arquivo ao atributo `filter=lfs`, `diff=lfs`, `merge=lfs` e `dontdiff`:

```
# Exemplo de configuração no .gitattributes
*.psd filter=lfs diff=lfs merge=lfs -text
*.mp4 filter=lfs diff=lfs merge=lfs -text
/assets/large_image.png filter=lfs diff=lfs merge=lfs -text
```

**Explicação dos Atributos:**

  * **`filter=lfs`**: Este é o atributo principal que instrui o Git a usar o filtro LFS para "limpar" (antes do commit, substituindo o arquivo real pelo ponteiro) e "smudge" (no checkout, baixando o arquivo real do servidor LFS).
  * **`diff=lfs`**: Informa ao Git para usar a ferramenta de diff do LFS para esses arquivos. Em vez de tentar mostrar um diff de texto para um binário (o que geralmente é inútil), ele pode indicar apenas que o arquivo foi alterado.
  * **`merge=lfs`**: Ajuda o Git a lidar com mesclagens de arquivos LFS.
  * **`-text`**: É importante adicionar `-text` para arquivos binários, pois isso evita que o Git tente normalizar quebras de linha ou trate o arquivo como texto.

Depois de configurar o `.gitattributes`, você pode adicionar e commitar esses arquivos normalmente. O Git LFS fará a "mágica" por trás dos panos.

### Quando é Indicado Usar o Git LFS?

O Git LFS é altamente recomendado para projetos que:

  * Contêm muitos **arquivos binários grandes** que mudam frequentemente.
  * Têm uma longa **história de versões** de arquivos grandes.
  * Envolvem **equipes grandes** onde o desempenho do Git é crítico.
  * Estão atingindo os **limites de tamanho de repositório** impostos por plataformas como o GitHub (que possuem limites de tamanho para arquivos individuais e para o repositório total).

### Vantagens de Usar o Git LFS

  * **Otimização de desempenho:** Reduz significativamente o tempo de clone, fetch e checkout, melhorando a experiência do desenvolvedor.
  * **Gerenciamento eficiente de armazenamento:** Mantém o repositório Git principal leve, movendo o armazenamento de grandes arquivos para fora.
  * **Compatibilidade:** Funciona de forma transparente com o fluxo de trabalho Git existente.
  * **Controle de versão para todos os arquivos:** Permite que você continue versionando arquivos grandes com o Git, mesmo que eles não sejam ideais para o armazenamento direto no Git.

### Links de Referência

  * [Site Oficial do Git LFS](https://git-lfs.github.com/)
  * [GitHub Docs - About Git Large File Storage](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage)
  * [Atlassian - Git LFS Tutorial](https://www.atlassian.com/git/tutorials/git-lfs)
