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

- Antes de realmente fazer o commit dos arquivos, caso seja preciso remover algum arquivo do commit atual, utilize o comando:
```
git reset HEAD nome_do_arquivo
```
