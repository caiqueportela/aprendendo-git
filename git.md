﻿# Git

O git é uma ferramenta que auxilia no controle de versão de arquivos, oferecendo ferramentas para equipes poderem ao mesmo tempo editar arquivos e poder gerenciar as alterações e centraliza-las com segurança.

Ele oferece um histórico de alterações que permite verificar todas alterações feitas e o que foi editado nela, seja adição ou exclusão de arquivos, e até mesmo verificar qual linha foi adicionada, deletada ou alterada, mostrando o antigo e o novo valor. Esse recurso apesenta a data e hora das alterações, além do usuário autor da mudança.

O GitHub é uma plataforma online onde você pode armazenar seus arquivos utilizando o Git.

Inicialmente, para se identificar como usuário autor no git, utilize os comandos:

    git config --global user.name "<<nome>>"
    git config --global user.email "<<email>>"

Substituindo <<nome>> e <<email>> pelo seu nome e e-mail, respectitivamente. Isso é necessário para identificar o autor das alterações, e será necessário para aplica-las.

Para criar um novo repostirório local (pasta com controle de alterações) você deve navegar até a pasta desejada e dar o comando:

git init

Será criado os arquivos necessários (ocultos) para tornar a pasta um repositório. Lembrando que todo conteúdo da pasta (arquivos, pastas, subpastas e seus arquivos) farão parte do repositório.

Você pode verificar todos os arquivos que o git está controlando, ou seja, os arquivos que ele está verificando se houve alterações, utilizando o comando:

git ls-files

Para verificar o status atual do repositório, o commit atual, o branch atual e os arquivos untracked (arquivos não monitorados), utilize o comando:

git status

Para adicionar um novo arquivo, utilize o comando:

git add <<arquivo>>

Após, se dar um `git status` esse arquivo aparecerá como alterado e pronto para ser commitado.
Após editar um arquivo, ele tambem precisa ser adicionado utilizando `git add` para adiciona-lo ao commit.
Você pode adicionar vários arquivos separados por espaços, uma pasta ou todos arquivos do diretório atual utilizando um ponto como nome do arquivo.

Para enviar as alterações, ou seja, efetuar um commit, utilize o comando:

git commit -m "<<comentario>>"

Onde em <<comentario>> (Sempre entre aspas!) você deve dar um comentário referente as alterações.
Se adicionarmos a opção `-a` automaticamente irá adicionar ao commit todos os arquivos alterados, mesmo sem terem suas alterações adicionadas; porém eles devem já estar sendo rastreados para funcionar.
Caso a opção `-m` não seja utilizada, será aberto um editor de texto para realizar o comentário do commit (útil quando a descrição precisar ser um pouco maior).

Para verificar o histórico de commits, utilize o comando:

git log

Se utiliza a opção `-p` será listado as mudanças em cada commit.

Para listar as mudanças de cada commit, mostrando quais arquivos foram alterados, utilize o comando:

git whatchanged

Par alistar com mais detalhes, mostrando o que foi alterado em cada arquivo, adicione a opção `-p`.
Tecle 'Q' para sair da tela que exibe os detalhos.

Para mostrar os repositórios remotos que seu repositório local está associado, utilize o comando:

git remote

Com o repositório remoto já criado no GitHub, você pode associar ao repositório local com o comando:

git remote add <<nome>> <<URL>>

Sendo <<nome>> um nome (apelido) para o repositório (pode ser qualquer nome, porém normalmente chamando de origin) e <<URL>> o endereço do repositório remoto. Ex:

git remote add origin https://github.com/caiqueportela/aprendendo-git.git

Para enviar as alterações (commits já feitos) para o repositório remoto, utilize o comando:

git push <<nome>> <<branch>>

Sendo <<nome>> o nome dado ao repositório (normalmente origin) e <<branch>> o nome da branch que está trabalhando (geralmente master). Ex:

git push origin master

Para baixar (clonar) um repositório do Github, basta utilizar o comando:

git clone <<URL>>

Sendo <<URL>> substutida pelo endereço do repositório desejado. Ex:

git clone https://github.com/minsait-veloe/check-in.git

Ele por padrão irá criar uma pasta com o nome do repositório e dentro dela irá baixar todos os arquivos.

Para evitar problemas nos arquivos, devemos trabalhar utilizando branchs. Assim, assim as suas alterações ficam em uma área separada, e ao terminar você poderá adicina-la a área principal, a branch master.

Para listar as branchs do projeto, utilize o comando:

git branch

Para criar uma nova branch:

git branch <<nome>>

Sendo <<nome>> o nome que quer dar para a nova branch.
Para apagar uma branch utilize a opção `-d`, ou `-D` para forçar em caso de não estar associada com a remota.

Para mudar de branch, utilize o comando:

git checkout <<nome>>

Sendo <<nome>> o nome da branch que quer trabalhar.
Utilize a opção `-b` para alterar para branch após criar.

Para enviar essa nova branch para o repositório online e seus commits, utilize o comando:

git push -u <<nome>> <<branch>>

Sendo <<nome>> o nome dado ao repositório (normalmente origin) e <<branch>> o nome da branch que está trabalhando.
A opção `-u` serve para associar a branch local com a remota.

Para baixar as atualizações do repositório remoto, utilize o comando:

git pull <<nome>> <<branch>>

Sendo <<nome>> o nome dado ao repositório (normalmente origin) e <<branch>> o nome da branch que deseja atualizar.
Se der apenas `git pull` irá atualizar a branch de trabalho atual.

Para listar as branchs locais, utilize o comando:

git branch

Para listar as remotas, utilize a opção `-r`.
Para listar todas, utilize a opção `-a`.

Caso tenha sido criado uma nova branch no repositório remoto, deve cria-la e associar utilizando o comando:

git branch -t <<branch-local>> <<nome>>/<<branch>>

Sendo <<branch-local>> o nome da branch local a ser criada, <<nome>> o nome dado ao repositório (normalmente origin) e <<branch>> o nome da brench remoto. Normalmente a branch local e remoto possuem o mesmo nome (isso evita confusões).

Para listar as alterações realizadas no repositório remoto, utilize o comando:

git fetch <<nome>>

Sendo <<nome>> o nome dado ao repositório (normalmente origin).

Para juntar o conteudo de duas branchs, utilize o comando:

git merge <<brench>>

Sendo <<brench>> o nome da brench onde fez as alterações. Ele irá juntar as alterações com a brench atual.

Para puxar as alterações de uma branch, por exemplo a master, para a atual, utilize o comando:

git rebase <<brench-base>> <<brench>>

Sendo <<brench-base>> de onde você quer pegar as alterações e <<brench>> a brench onde você quer colocar as alterações.

Se deseja voltar a versão de um arquivo para sua versão da ultima commit no repositório, utilize o comando:

git checkout <<nome>>

Sendo <<nome>> o nome do arquivo a ter sua versão restaurada.

Se a alteração já estiver no Index (preparada para commit). Para remover, utilize o comando:

git reset HEAD <<nome>>

Sendo <<nome>> o nome do arquivo a ter seu estado voltado a não alterado.
HEAD pode ser alterado pelo identificador do commit.

Para reverter as alterações feitas em um commit, utilize o comando:

git revert <<commit>>

Sendo <<commit>> o identficador do commit a ter suas mudanças revertidas.
Obs: APENAS alterações feitas nesse commit serão desfeitas, as alteraçõs posteriores se mantem. Um novo commit é criado automaticamente.

Para salvar as aterações com commit que não foram enviadas para um "mais tarde", utilize:

git start

Ele irá zerar todas as alterações que não foram enviadas e restaurar os arquivos para o ultimo commit do repositório web.

Para ver o que estar no "mais tarde", utilize:

git stash list

Para restaurar o ultimo "mais tarde" da lista, utilize:

git stash pop

Para restaurar um especifico, utilize:

git stash apply <<numero>>

Sendo <<numero>> o numero do "mais tarde" a ser restaurado.

Para apagar um "mais tarde", utilize:

git stash drop

`git stash clear` limpa tudo

Para fazer buscar de alterações utilize `git bisect`. Um pouco complexo.

Para dar merge com apenas as alterações feitas em um commit específico, utilize:

git cherry-pick <<commit>>

Sendo <<commit>> a hash do commit desejado.



___________________________________________________________________________


Para verificar as versões (releases) do nosso projeto, utilizamos o comando:

git tag

Se quisermos editar o código de uma versão diferente, podemos alterar para a versão desejada utilizando o comando:

git checkout <<versao>>

Sendo <<versao>> substituido pelo nome da versão desejada.

Podemos ver a diferença entre duas versões utilizando o comando:

git diff <<v1>> <<v2>>

Substituindo <<v1>> e <<v2>> pelo nome das duas versões que deseja comparar. Ele irá listar os arquivos alterados e cada linha que foi alterada, adicionada ou removida.
