# Git e Github
Arquivo da aula de Git e Github para iniciantes.

## Sobre o controle de versão
O que é "controle de versão" e por que você deveria se importar? O controle de versão é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, para que você possa recuperar versões específicas mais tarde.

É aqui que os Sistemas Distribuídos de Controle de Versão (DVCSs) entram em cena. Em um DVCS (como Git, Mercurial, Bazaar ou Darcs), os clientes não apenas conferem o último instantâneo dos arquivos; em vez disso, espelham completamente o repositório, incluindo seu histórico completo. Portanto, se algum servidor morrer, e esses sistemas estiverem colaborando por esse servidor, qualquer um dos repositórios do cliente poderá ser copiado para o servidor para restaurá-lo. Todo clone é realmente um backup completo de todos os dados.

[saiba mais em git-scm.com](https://git-scm.com/)

[![Git_ciclo.vida_.png](Git_ciclo.vida_.png)](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)

## Básico do Git 

### [Gravando alterações no repositório](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)

* git init
* git status

**Ignorando arquivos**

Muitas vezes, você tem uma classe de arquivos que não deseja que o Git adicione automaticamente ou até mostre como não rastreado. Geralmente, são arquivos gerados automaticamente, como arquivos de log ou arquivos produzidos pelo seu sistema de construção. Nesses casos, você pode criar um padrão de listagem de arquivos para corresponder aos nomeados no arquivo `.gitignore`

* git diff - Para ver o que você alterou, mas ainda não foi preparado

Com `git diff --name-only` é possível ver apenas a lista de arquivos modificados.

* git add - Rastreando novos arquivos
* git commit - Confirmando suas alterações

com `git commit -am` é possível adicionar e commitar em uma única operação

* git rm - Removendo arquivos
* git mv file_from file_to - Movendo arquivos

### Vendo o histórico de consolidação
Veja mais em

* git log

[Veja mais...](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

### Desfazendo coisas

* git commit --amend - Uma forma comum de desfazer as coisas no Git ocorre quando você confirma muito cedo e possivelmente esquece de adicionar alguns arquivos ou estraga sua mensagem de confirmação. Se você deseja refazer a confirmação, faça as alterações adicionais que você esqueceu, prepare-as e use o `commit` novamente usando a opção `--amend`
* git checkout - "Desmodificando" um arquivo modificado, mas não adicionado
* git reset HEAD - "Desmodificando" um arquivo modificado e adicionado (ver [--soft, --mixed e --hard](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified#_git_reset))

Após aplicar o `git reset HEAD`, utilize o `git checkout` 

[Veja mais...](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things)

## Trabalhando com controles remotos

### Criando um repositório no Github

[Gerando uma chave SSH do Github para o seu projeto](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

no terminal digite: 

>`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

>copie a chave contina no arquivo **__id_rsa_.pub_**

no Github:
>acesse o menu _**settings**_ e, na coluna de opções do seu perfil, clique em _**SSH and GPG Keys**_. Clique em **_New SSH Keys_**, informe o _**título**_ e cole a chave contida no arquivo _**id_rsa.pub**_

### Ligando o repositório local a um remoto (Github)

1. crie um repositório no Github, por exemplo **git_github_course.git**;
2. envie um repositório existente a partir da linha de comando:

`git remote add origin git@github.com:marcelo-dss/git_github_course.git`

digite `git remote` para que o git mostre se já existe um repositório chamado _**origin**_ preparado para ser enviado ao github. `git remote -v`, para mais informações ou se você quiser ver mais informações sobre um controle remoto específico, use o comando `git remote show <remote>`

`git push -u origin master`

o `-u` é utilizado no primeiro push para *trackear* para onde vai (*origin*) e de onde vem (*master*). Nos seguintes basta utilizar `push`

### Enviando mudanças para um repositório remoto
`git push origin master`

### Clonando repositórios remotos

`git clone git@github.com:marcelo-dss/git_github_course.git nomeRepositorioLocal`

sendo nomeRepositorioLocal, por exemplo, *git_github_course_clone*

[Veja mais sobre como trabalhar com controles remotos](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)

### Usando Fork (Bifurcação)

veja: [contribuindo para um projeto](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project)

## Ramificação (Branch)

Uma ramificação no Git é simplesmente um ponteiro móvel leve para um desses commits. O nome do ramo padrão no Git é *master*. Quando você começa a fazer confirmações, você recebe um ramo master que aponta para o último commit que você fez. Toda vez que você faz um commit, o ponteiro master do ramo avança automaticamente.

O ramo *"master"* no Git não é um ramo especial. É exatamente como qualquer outro ramo. A única razão pela qual quase todo repositório tem um é que o comando `git init` o cria por padrão e a maioria das pessoas não se preocupa em alterá-lo.

O que acontece quando você cria uma nova ramificação? Isso cria um novo ponteiro para você se movimentar. Digamos que você queira criar um novo ramo chamado *testing*. Você faz isso com o comando `git branch`: `$ git branch testing`

Isso cria um novo ponteiro para o mesmo commit em que você está atualmente.

Por que usar?

* Poder usar sem alterar o local principal ("*master*");
* Facilmente "desligável", criando-os e apagando-os;
* Permite várias pessoas trabalhando em diversos branches;
* Evita conflitos em casos de muitos commits simultâneos;
* Permite mesclar branchs "secundários" com o principal.

[veja mais sobre branchs...](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

criando um branch: 
`git branch testing` ou 
`git checkout -b testing` para criar e acessar no mesmo comando

para visualizar o branch ativo, digite: `git branch`

movendo-se entre branchs: `git checkout <nomeDoBranch>`

deletando: `git branch -D <nomeDoBranch>`

### Unindo branchs

#### Merge

supondo que você está em um branch chamado master e quiser mesclar outro branch chamado teste, digite: `git merge teste`

analise o resultado com `git log --graph`

Prós:

* operação não destrutiva - não destrõe commits, pelo contrário junta todos em um novo commit

Contras:

* necessidade de commits extras;
* histórico poluído

[mais sobre merge...](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

### Rebase

Prós:

* evita commits extras;
* mantém um histórico linear

Contras:

* perda da ordem cronológica

[mais sobre rebase...](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)

$\Overrightarrow{AB}$
