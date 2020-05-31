# git-samples
  Amostras de comando do git.

**Obs:.** Os usuários do linux podem utilizar o seguinte script para visualizar a branch atual no terminal. Para isso, altere o arquivo ~/.bashrc adicionando o seguinte shell script.
```shell
parse_git_branch() {
     git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}
export PS1="\u@\h \[\033[32m\]\w\[\033[33m\]\$(parse_git_branch)\[\033[00m\] $ "
```


- Para fazer criação de um novo repositório local, utilize o comando abaixo, na pasta onde o repositório deve ser criado:
```
git init
```

- Para fazer a criação de um repositório local a partir de um repositório já existente, utilize o seguinte comando:
```
git clone https://github.com/PedroFerreiraCJr/git-samples.git
```

- O comando abaixo mostra o estado atual do diretório de trabalho do git:
```
git status
```
**Obs:.** Os arquivos listados na cor vermelhos são os arquivos que foram alterados (modified) ou ainda não estão sendo rastreados (untracked) pelo git.

- Para adicionar os arquivos alterados ou criados no commit, utilize o comando:
```
git add [.|file_name|--all|-A]
```

- Antes de realmente fazer o commit dos arquivos e salvar o estado atual do diretório de trabalho, caso seja preciso remover algum arquivo do commit atual, utilize o comando:
```
git reset HEAD nome_do_arquivo
```

**Obs:.** Outra forma de remover um arquivo da área de trabalho do git é executando o comando:
```
git rm --cached nome_do_arquivo
```

- Para desfazer alterações feitas em um arquivo, utilize o comando:
```
git checkout nome_do_arquivo
```

- Utilize o seguinte comando para remover o arquivo do repositório local do git, e remover do sistema de arquivos:
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

-- Para visualizar todos os commit efetuados em determinado na branch atual, utilize o seguinte comando:
```
git log
```
**Obs:.** Para visualizar somente os últimos 5 commits, por exemplo, utilize o parametro: -n 5.

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

- Para listar as branchs existentes, utilize o seguinte comando:
```
git branch -a
```

[Documentação do comando branch](https://git-scm.com/docs/git-branch)

- Para trocar de branch, utilize o seguiente comando:
```
git checkout nome_da_branch
```

**Obs:.** O comando checkout pode ser utilizado para para executar duas ações, que são, criar uma nova branch e imediatamente trocar para o nova branch. O comando é o seguinte:
```
git checkout -b nome_da_nova_branch
```

- Para deletar uma branch, utilize o seguinte comando:
```
git branch -d nome_da_branch
```

- Para adicionar um repositório remoto ao repositório local do git, utilize o seguinte comando:
```
git remote add origin https://github.com/PedroFerreiraCJr/git-samples.git
```

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

**Obs:.** O comando acima está apontando para o repositório remoto origin e branch master. Altera os parametros *origin* e *master* para o repositório remoto e branch, respectivamente.

[Documentação do comando pull](https://git-scm.com/docs/git-pull)

- Para criar a branch do repositório local na branch remota, utilize o seguinte comando:
```
git push -u origin master
```

**Obs:.** Utilize o parametro *-u* equivamente à *--set-upstream* somente quando a branch ainda não existir no repositório remoto.

- Para mandar todas as alterações (commits) do repositório local para o repositório remoto, utilize o seguinte comando:
```
git push origin master
```

**Obs:.** É possível trocar os parametros: *origin*, e *master*; para a um repositório remoto e branch remota pré-existente.

[Documentação do comando push](https://git-scm.com/docs/git-push)

- Para remover uma branch do repositório remoto, utilize o seguinte comando:
```
git branch -d nome_da_branch_local
git push origin --delete nome_da_branch_remote
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











