<h1 align="center">git-samples</h1>
  Repositório contendo uma referência aos principais comandos do git.

<br/>

## Árvores do Git

<p align="center">
  <img width="460" height="300" src="https://raw.githubusercontent.com/PedroFerreiraCJr/git-samples/master/git_stages.png">
</p>

<br/>

## Variável de ambiente linux

Os usuários do linux podem utilizar o seguinte script para visualizar a branch atual no terminal. Para isso, altere o arquivo ~/.bashrc adicionando o seguinte shell script.
```shell
parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u@\h \[\033[32m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\] $ "
```

## Comandos

- Para fazer a criação de um novo repositório local, utilize o comando abaixo, na pasta onde o repositório deve ser criado:
```
git init
```
**Obs:.** Um repositório Git nada mais é do que um diretório que contém um subdiretório chamado *.git*; este é o diretório que o git usa para controlar o versionamento do projeto.
</br>
**Obs:.** Com relação ao comentado acima, para remover o controle de versão de um projeto, basta remover a pasta que faz o controle do git (*.git*) de dentro do projeto.

- Para fazer criação de um novo repositório local, utilize o comando abaixo, na pasta onde o repositório deve ser criado:
```
git init nome-do-projeto
```
**Obs:.** Este comando é utilizado em um projeto criado do zero, sem ter o diretório do projeto criado, é possível executar o comando que segue para criar a pasta e inicializar um repositório Git:

- Para fazer criação de um novo repositório que será utilizado como servidor remoto, é possível usar o seguinte comando:
```
git init --bare
```
> Com o comando git init --bare você está criando um repositório que é pushable. Geralmente os repositórios bare são criados no servidor e são considerados repositórios para armazenamento, em contraste aos repositórios que vão nas máquinas dos desenvolvedores que seriam os repositórios de desenvolvimento, criados com o comando git init (sem o --bare).

[FAQ do StackOverflow](https://pt.stackoverflow.com/questions/80182/qual-%C3%A9-a-diferen%C3%A7a-entre-git-init-e-git-init-bare)

- Para fazer a criação de um repositório local a partir de um repositório já existente hospedado, por exemplo, em um serviço de hospedagem de repositório do Git, utilize o seguinte comando:
```
git clone https://github.com/PedroFerreiraCJr/git-samples.git
```
**Obs:.** Neste caso, foi usado uma url de repositório que está hospedado no serviço do GitHub.

- O mesmo comando permite clonar um repositório que existe localmente; supondo que mywebsite seja um repositório local do git, para clonar o mesmo para outro repositório local, execute:
```
git clone mywebsite/ mywebsite2
```

- O comando abaixo mostra o estado atual do diretório de trabalho (working directory) do git:
```
git status
```
**Obs:.** Os arquivos listados na cor vermelha são os arquivos que foram alterados (modified) ou ainda não estão sendo rastreados (untracked) pelo git.

- Para adicionar os arquivos alterados ou criados no commit, utilize o comando:
```
git add [.|file_name|--all|-A]
```

- Antes de realmente fazer o commit dos arquivos e salvar o estado atual do diretório de trabalho, caso seja preciso remover qualquer arquivo rastreado pelo git do commit atual (após ter executado o comando git add .), utilize o comando:
```
git reset HEAD nome_do_arquivo
```

**Obs:.** Outra forma de remover um arquivo da área de trabalho do git, e deixar de fazer o rastreamentod o arquivo, é executando o comando:
```
git rm --cached nome_do_arquivo
```

- Para desfazer alterações feitas em um arquivo que está no diretório de trabalho (working directory), utilize o comando:
```
git checkout nome_do_arquivo
```

- Utilize o seguinte comando para remover o arquivo do repositório local do git, assim como remover do sistema de arquivos:
```
git rm nome_do_arquivo
```
**Obs:.** O arquivo a ser removido já deve estar sendo rastreado pelo git.

- Para desfazer todas as alterações no diretório de trabalho do git, e apontar para o último estado rastreado por commit, utilize o comando:
```
git reset --hard HEAD
```
- Quando estiver pronto para salvar o estado dos arquivos no diretório de trabalho, utilize o comando a seguir:
```
git commit -m "Mensagem do commit"
```

- Para visualizar todos os commits efetuados em determinada branch, utilize o seguinte comando:
```
git log
```
**Obs:.** Para visualizar somente os últimos 5 commits, por exemplo, utilize o parametro: -n 5.

- Para visualizar todos os commits efetuados em determinada branch de forma resumida, mostrando somente o hash do commit e mensagem, utilize o seguinte comando:
```
git log --oneline
```

- Para visualizar todos os commits efetuados em determinada branch, mostrando as alterações que foram feitas nos arquivos, utilize o seguinte comando:
```
git log -p
```

- Para visualizar um resumo de todos os arquivos alterados em todos os commits, utilize o seguinte comando:
```
git log --stat
```
[Documentação do comando log](https://git-scm.com/docs/git-log)

- Para visualizar os arquivos que foram alterados em determinado commit, utilize o seguinte comando:
```
git show --pretty="" --name-only d542f8a1b1d8c0f409222cf7999dd742e10bc6b1
```

[Documentação do comando show](https://git-scm.com/docs/git-show)

- Para criar uma nova ramificação a partir da branch atual, utilize o seguiente comando:
```
git branch nome_da_nova_branch
```

- Para listar todas as branchs locais, utilize o seguinte comando:
```
git branch
```
**Obs:.** A branch que contém um asterísco, é a branch que está em uso.

- Para listar todas as branchs existentes, seja local ou remota, utilize o seguinte comando:
```
git branch -a
```
**Obs:.** A branch que contém um asterísco, é a branch que está em uso.

[Documentação do comando branch](https://git-scm.com/docs/git-branch)

- Para trocar de branch, utilize o seguiente comando:
```
git checkout nome_da_branch
```

**Obs:.** O comando checkout pode ser utilizado para para executar duas ações, que são: criar uma nova branch e imediatamente trocar para o nova branch; e também navegar pelo histórico de commits do git. O comando é o seguinte cria uma nova branch e torna ela o ramo atual:
```
git checkout -b nome_da_nova_branch
```

- Para deletar uma branch, utilize o seguinte comando:
```
git branch -d nome_da_branch
```

- O comando a seguir permite que seja feita a troca de contexto, salvando temporariamente as alterações (sem commit, para arquivos modificados e adicionados com o comando *git add*) na branch atual, para que seja possível trabalhar em outra branch; após este comando a branch se tornar "clean":
```
git stash
```
**Obs:.** O comando stash só permanece localmente.
</br>
**Obs:.** Arquivos ignorados pelo Git, assim como não rastreados não são adicionados ao stash.
</br>
**Obs:.** Para que seja possível adicionar um arquivo não rastreado pelo Git ao stash, é necessário passar o parâmetro -u (ou --include-untracked) para esse propósito.

- O comando seguinte faz a listagem dos indices de stash salvos atualmente na branch:
```
git stash list
```

- Para remover todos os indices de stash salvos para serem aplicados posteriormente, basta executar o comando a seguir:
```
git stash clear
```
**Obs:.** Este comando descarta todas as alterações salvas temporariamente no stash.

- Para remover somente um determinado índice do stash, execute o comando seguinte:
```
git stash drop stash@{1}
```
**Obs:.** Este comando descarta o índice do stash de valor 1.

- Para aplicar as alterações salvas temporariamente no stash, mesmo existindo mais de um índice no stash, basta executar o comando seguinte para aplicar o último índice:
```
git stash apply
```
**Obs:.** Este comando não descarta o índice do stash.

- Para aplicar as alterações salvas temporariamente no último índice do stash, basta executar o seguinte comando para aplicar o último índice e remover automaticamente:
```
git stash pop
```
- Para ter uma lista de arquivos alterados que foram salvos temporariamente pelo comando stash, basta usar o comando a seguir:
```
git stash show
```

- Para adicionar um repositório remoto ao repositório local do git, utilize o seguinte comando:
```
git remote add origin https://github.com/PedroFerreiraCJr/git-samples.git
```

**Obs:.** "origin" é um alias para a branch remota.
</br>
**Obs:.** É possível adicionar mais de uma branch remota.

- Para visualizar as branchs remotas do repositório local do git, utilize o seguinte comando:
```
git remote -v
```

- Para remover um repositório remoto do repositório local, utilize o seguinte comando:
```
git remote rm nome_do_repositório_remoto
```

- Para obter mais informações sobre o comando *remote* no próprio terminal, utilize o comando:
```
git remote --help
```

[Documentação do comando remote](https://git-scm.com/docs/git-remote)

- Para baixar todas as alterações do repositório remoto para o repositório local, utilize o seguinte comando:
```
git pull origin master
```

**Obs:.** O comando acima está apontando para o repositório remoto origin e branch master. Alterar os parametros *origin* e *master* para o repositório remoto e branch, respectivamente, de sua escolha.

[Documentação do comando pull](https://git-scm.com/docs/git-pull)

- Para criar a branch do repositório local na branch remota, utilize o seguinte comando:
```
git push -u origin master
```

**Obs:.** Utilize o parâmetro *-u* equivamente à *--set-upstream* somente quando a branch ainda não existir no repositório remoto.

- Para mandar todas as alterações (commits) do repositório local para o repositório remoto, utilize o seguinte comando:
```
git push origin master
```

**Obs:.** É possível trocar os parâmetros: *origin*, e *master*, para um repositório remoto e branch remota pré-existente.

[Documentação do comando push](https://git-scm.com/docs/git-push)

- Para remover uma branch do repositório remoto, utilize o seguinte comando:
```
git branch -d nome_da_branch_local    // remove a branch localmente
git push origin --delete nome_da_branch_remote    // remove a branch no servidor remoto
```

**Obs:.** O repositório remoto, neste caso *origin* pode ser troacado por outro caso necessário.

- Para visualizar todas as modificações na branch atual, utilize o seguinte comando:
```
git diff
```

**Obs:.** Para visualizar todas as modificações na branch atual, quando já houver usado o comando *git add*, use o seguinte comando:
```
git diff --cached
```

- Para visualizar as diferenças entre duas branchs, utilize o seguinte comando:
```
git diff nome_da_branch1 nome_da_branch2
```

[Documentação do comando diff](https://git-scm.com/docs/git-diff)

