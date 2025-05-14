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

