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

