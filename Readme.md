# Git e Github
Arquivo da aula de Git e Github para iniciantes.

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

### [Vendo o histórico de consolidação](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

* git log

### [Desfazendo coisas](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things)

* git commit --amend - Uma forma comum de desfazer as coisas no Git ocorre quando você confirma muito cedo e possivelmente esquece de adicionar alguns arquivos ou estraga sua mensagem de confirmação. Se você deseja refazer a confirmação, faça as alterações adicionais que você esqueceu, prepare-as e use o `commit` novamente usando a opção `--amend`
* git checkout - "Desmodificando" um arquivo modificado, mas não adicionado
* git reset HEAD - "Desmodificando" um arquivo modificado e adicionado (ver [--soft, --mixed e --hard](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified#_git_reset))

Após aplicar o `git reset HEAD`, utilize o `git checkout` 



$\Overrightarrow{AB}$
