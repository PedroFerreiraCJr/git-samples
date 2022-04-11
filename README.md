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

## Configuração inicial

- Para que seja possível utilizar o Git da maneira correta é necessário configurar alguma informações relacionadas ao usuário que está atualmente usando a ferramenta. Esses comandos são necessários para que o Git faça o reconhecimento do usuário atualmente fazendo o commit, pois ele não solicita credenciais como o email, ou nome de usuário.
```
git config --global user.name "Nome da pessoa"
git config --global user.email "email.da.pessoa@email.com"
```

- Outra configuração que é considerada importante é o editor padrão utilizado pelo Git em alguma situações que precisam de intervenção do usuário. O comando para alterar o editor padrão utilizado pelo Git é o seguinte:
```
git config --global core.editor "nano"
```
**Obs:.** O editor configurado neste exemplo foi o Nano.
</br>
**Obs:.** Para verificar se o comando surtiu efeito, use: *git config --list*.

- Uma forma de visualizar o arquivo global de configuração do Git, é através do comando abaixo:
```
git config --global -e
```
**Obs:.** Isso possibilita visualizar e alterar o arquivo.

- Exemplo de arquivo de configuração que usa o editor vscode para algumas das operações que precisam de intervenção do usuário:
<pre>
[user]
	email = pedroferreiracjr@gmail.com
	name = Pedro Júnior
[core]
	editor = code --wait
[merge]
	tool = vscode
[mergetool "vscode"]
	cmd = code --wait $MERGED
[diff]
	tool = vscode
[difftool "vscode"]
	cmd = code --wait --diff $LOCAL $REMOTE
[mergetool]
	keepBackup = false
</pre>

## Comandos

- Para fazer a criação de um novo repositório local, utilize o comando abaixo, na pasta onde o repositório deve ser criado:
```
git init
```
**Obs:.** Um repositório Git nada mais é do que um diretório que contém um subdiretório chamado *.git*; este é o diretório que o git usa para controlar o versionamento do projeto.
</br>
**Obs:.** Com relação ao comentado acima, para remover o controle de versão de um projeto, basta remover a pasta que faz o controle do git (*.git*) de dentro do projeto.

- Para fazer a criação de um novo repositório local fornecendo o nome pasta onde o repositório deve ser criado, use:
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

- O comando abaixo mostra o estado atual do diretório de trabalho (working directory) do Git:
```
git status
```
**Obs:.** Os arquivos listados na cor vermelha são os arquivos que foram alterados (modified) ou ainda não estão sendo rastreados (untracked) pelo git.

- Para adicionar os arquivos alterados ou criados ao commit, utilize o comando:
```
git add [.|file_name|--all|-A]
```

- Antes de realmente fazer o commit dos arquivos que estão no diretório de trabalho do Git, e salvar o estado atual no histórico de commits, caso seja preciso remover qualquer arquivo rastreado pelo Git do commit atual (após ter executado o comando git add .), utilize o comando:
```
git reset HEAD <nome_do_arquivo>
```

**Obs:.** Outra forma de remover um arquivo da Staging Area do Git e, deixar de fazer o rastreamento do arquivo deixando ele no diretório de trabalho, é executando o comando a seguir:
```
git rm --cached <nome_do_arquivo>
```

- Para desfazer alterações feitas em um arquivo que está no Staging Area, utilize o comando:
```
git restore --staged <nome_do_arquivo>
```

- Utilize o seguinte comando para remover o arquivo do repositório local do Git, assim como remover do sistema de arquivos:
```
git rm <nome_do_arquivo>
```
**Obs:.** O arquivo a ser removido já deve estar sendo rastreado pelo Git.
</br>
**Obs:.** Para remover um arquivo do rastreamento do Git, basta adicioná-lo ao arquivo .gitignore.

- Para desfazer todas as alterações no diretório de trabalho do Git, e apontar para o último estado rastreado por commit, utilize o comando:
```
git reset --hard HEAD
```

- Qual o comando para listar todos os arquivos rastreados pelo Git?
```
git ls-tree -r master --name-only
```

- Quando estiver pronto para salvar o estado dos arquivos no diretório de trabalho, primeiro use o comando *add* e depois, utilize o comando a seguir:
```
git commit -m "Mensagem do commit"
```

- Para visualizar todos os commits efetuados em determinada branch (ramo), utilize o seguinte comando:
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

- Qual o comando para listar todos os arquivos rastreados e até mesmo os deletados?
```
git log --pretty=format: --name-only --diff-filter=A | sort - | sed '/^$/d'
```
[Stack Overflow](https://stackoverflow.com/questions/15606955/how-can-i-make-git-show-a-list-of-the-files-that-are-being-tracked/15606998)
</br>
[Documentação do comando log](https://git-scm.com/docs/git-log)

- Para visualizar os arquivos que foram alterados em determinado commit, utilize o seguinte comando:
```
git show --pretty="" --name-only d542f8a1b1d8c0f409222cf7999dd742e10bc6b1
```

[Documentação do comando show](https://git-scm.com/docs/git-show)

- Para criar uma nova branch (ramificação) a partir da branch atual, utilize o seguinte comando:
```
git branch <nome_da_nova_branch>
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

**Obs:.** O comando checkout pode ser utilizado para para executar algumas operações, sendo: criar uma nova branch e imediatamente trocar para o nova branch; navegar pelo histórico de commits do Git.

- O comando seguinte cria uma nova branch e torna ela o ramo atual:
```
git checkout -b <nome_da_nova_branch>
```

- Outra funcionalidade muito importante do Git, conforme já mencionado, são as branchs. Com elas é possível criar uma linha de desenvolvimento paralela a principal. E quando for preciso mesclar as funcionalidades desenvolvidas, por exemplo, uma feature de login (branch: feature-login), basta usar o comando:
```
git checkout master
git merge feature-login
```

- Caso seja preciso abortar a mesclagem dos arquivos por qualquer motivo, em caso de conflito por exemplo, basta executar o comando abaixo, e a mesclagem será cancelada:
 ```
 git merge --abort
 ```
 
- Para analisar e corrigir qualquer conflito que tenha sido causado no momento do merge entre branchs usando o vscode, é possível usar o comando:
```
git mergetool
```
**Obs:.** Para usar outra ferramenta de análise de conflito, use o parâmetro -t e o comando, exemplo: -t vscode.

-  Para visualizar as modificações nos arquivos da branch atual usando um editor de análise de diferenças padrão, basta executar o comando abaixo:
```
git difftool
```
**Obs:.** Caso se depare com a criação de arquivos como: *.orig, .BACKUP, .BASE, .LOCAL, .REMOTE; e quiser eliminar esses arquivos no momento da correção do merge e commit, basta executar a seguinte configuração no Git: *git config --global mergetool.keepBackup false*

- Para deletar uma branch local, utilize o seguinte comando:
```
git branch -d <nome_da_branch>
```
**Obs:.** O parâmtro -d é um atalho para --delete.

- Para forçar a deleção em uma branch local, utilize o seguinte comando:
```
git branch -D nome_da_branch
```
**Obs:.** O parâmtro -D é um atalho para os parâmetros --delete --force.
</br>
**Obs:.** A deleção forçada pode ser utilizada quando a branch não foi mesclada, e mesmo assim se deseja deletá-la.

- Para forçar a deleção de uma branch remota, utilize o seguinte comando:
```
git push origin --delete <nome_da_branch>
```
**Obs:.** O alias 'origin' é o identificador do servidor remoto.
</br>
**Obs:.** Este comando deve funcionar mesmo não tendo deletado a branch localmente. 

- O comando a seguir permite que seja feita a troca de contexto, salvando temporariamente as alterações (sem commit, para arquivos modificados e adicionados com o comando *git add*) na branch atual, para que seja possível trabalhar em outra branch; após este comando a branch se tornar "clean":
```
git stash
```
**Obs:.** O comando stash só permanece localmente.
</br>
**Obs:.** Arquivos ignorados pelo Git, assim como não rastreados não são adicionados ao stash.
</br>
**Obs:.** Para que seja possível adicionar um arquivo não rastreado pelo Git ao stash, é necessário passar o parâmetro -u (ou --include-untracked) para esse propósito.

- O comando seguinte faz a listagem dos índices de stash salvos atualmente:
```
git stash list
```

- Para remover todos os índices de stash salvos para serem aplicados posteriormente, basta executar o comando a seguir:
```
git stash clear
```
**Obs:.** Este comando descarta todas as alterações salvas temporariamente no stash.

- Para remover somente um determinado índice do stash, execute o seguinte comando:
```
git stash drop stash@{1}
```
**Obs:.** Este comando descarta o índice do stash de valor 1.

- Para aplicar as alterações salvas temporariamente no stash, mesmo existindo mais de um índice no stash, basta executar o seguinte comando para aplicar o primeiro índice:
```
git stash apply
```
**Obs:.** Este comando não descarta o índice do stash.

- Para aplicar as alterações salvas temporariamente no primeiro índice do stash, basta executar o seguinte comando para aplicar o último índice e remover automaticamente:
```
git stash pop
```
- Para ter uma lista de arquivos alterados que foram salvos temporariamente pelo comando stash, basta usar o comando a seguir:
```
git stash show
```

- Para visualizar uma lista de diff's dos arquivos alterados, execute:
```
git stash show -p
```
**Obs:.** O parâmtro *-p* é de patch, ou *--patch*.

- Para adicionar um repositório remoto ao repositório local do git, utilize o seguinte comando:
```
git remote add origin https://github.com/PedroFerreiraCJr/git-samples.git
```
**Obs:.** "origin" é um alias para a branch remota.
</br>
**Obs:.** É possível adicionar mais de uma branch remota.

- Forma de adicionar um repositório remoto a uma repositório local que utiliza SSH
**Obs: ** A configuração da chave SSH deve ter sido feita previamente.
```
git remote set-url origin git@github.com:pedroferreiracjr/your-repository.git
```

- Para visualizar as branchs remotas do repositório local do git, utilize o seguinte comando:
```
git remote -v
```

- Para remover um repositório remoto do repositório local, utilize o seguinte comando:
```
git remote rm <nome_do_repositório_remoto>
```

- Para obter mais informações sobre o comando *remote* no próprio terminal, utilize o comando:
```
git help remote
```

[Documentação do comando remote](https://git-scm.com/docs/git-remote)

- Para baixar todas as alterações do repositório remoto para o repositório local, utilize o seguinte comando:
```
git pull <origin> <master>
```
**Obs:.** O comando acima está apontando para o repositório remoto origin e branch master. Alterar os parametros *origin* e *master* para o repositório remoto e branch, respectivamente, de sua escolha.

[Documentação do comando pull](https://git-scm.com/docs/git-pull)

- Para enviar a branch do repositório local para a servidor remoto, utilize o seguinte comando:
```
git push -u <origin> <master>
```
**Obs:.** Utilize o parâmetro *-u* equivamente à *--set-upstream* somente quando a branch ainda não existir no repositório remoto.

- Para mandar todas as alterações (commits) do repositório local para o repositório remoto, utilize o seguinte comando:
```
git push <origin> <master>
```
**Obs:.** É possível trocar os parâmetros: *origin*, e *master*, para um repositório remoto e branch remota pré-existente.

[Documentação do comando push](https://git-scm.com/docs/git-push)

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
git diff <nome_da_branch1> <nome_da_branch2>
```

[Documentação do comando diff](https://git-scm.com/docs/git-diff)

