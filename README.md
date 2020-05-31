# git-samples
  Amostras de comando do git.

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

- Para listar as branchs existentes, utilize o seguiente comando:
```
git branch -a
```

[Documentação do comando branch](https://git-scm.com/docs/git-branch)

- Para trocar de branch, utilize o seguiente comando:
```
git checkout nome_da_branch
```

**Obs:.** O comando checkout pode ser utilizado para para executar duas ações, que são, criar uma nova branch e imediatamente trocar para o nova branch. A utilizaçãod o comando é o seguinte:
```
git checkout -b nome_da_nova_branch
```



