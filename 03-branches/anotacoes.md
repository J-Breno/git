# Git e github: Branches

## Introdução aos branches

branches são linhas do tempo, que possibilitam os desenvolvedores trabalharem em outras coisas sem impactar na código principal

Listar branches

```bash
    git branch
```

Criar branches

```bash
    git branch nome-da-branch
```

deletar branch **(Não destrutiva)**

```bash
    git branch -d nome-da-branch
```

deletar branch mesmo sem ter feito merge dele ainda **(ação destrutiva)**

```bash
    git branch -D nome-da-branch
```

fazer o merge seria levar ele para branch main

para mudar de branch voce tem que fazer o:

```bash
    git checkout <nome-da-branch>
```

### Merge fast forward

A operação merge serve para mesclar o histórico de uma branch de origem para uma branch de destino.

O camando git pull pode ser entendido como um "merge" entre o branch remoto para o repositório local

O comando do merge deve ser feito a partir do branch de DESTINO.

O correto é fazer um merge do branch main para o branch de feature, e não o contrário.

Uma vez que o branch de feature esteja devidamente mesclado, cria-se um pull request no repositório remoto.

(main) git merge ft-login

### Procedimento pull request

***não*** se faz atualização no branch main do repositório remoto enquanto a feature não estiver **homologada**. Isso porque o branch main tipicamente está configurado com um processo automatizado de CI/CD, ou seja, atualizações na branch main já disparam automaticamente uma nova build da aplicação, e/ou até mesmo a **implantação** da atenção em ambiente de **produção**.

Ou seja, primeiro voce tem que puxar algo que esteja no main para a sua feature para ver se tem alguma atualização, ai depois voce puxar o que tá na feature para o main.

Ou seja, voce volta para o main, e faz um git pull origin main lá para garatir que não tem nenhuma atualização lá no remoto que não tem no local. ai depois voce volta para a branch de feature com o git checkout <nome-da-branch> e dá um git merge nele, do main para a feature, ou seja, git merge main. e depois voce salva o git de feature lá no git hub com o git push -u origin <nome-da-branch>

### Procedimento fork + pull request

Mesmo que voce não tenha permissão de escrita em um repositório do Github, voce pode enviar contribuições para repositório.

Este procedimento é a base para colaboração em projetos de código aberto.

faça um fork do repositório para o seu Github
clone seu repositório "forkado" para seu computador
crie um novo branch faça as alterações nesse branch
envie as alterações para seu reposítório "forkado"
crie uma pull request para o reposisório original