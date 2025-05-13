# Git e Github
## Resolvendo problemas comuns

Areá de stage é o local que você coloca os arquivos para serem salvos na sua versão;

Então como faço para remover eles de lá?

git reset ele faz isso.

supondo você salva um arquivo e ainda não commitou, é só fazer o git reset

Se caso voc^Çe não salvou o projeto ainda, você deve fazer dois comandos

git clean -df e git checkout -- .


no vim a tecla i faz o modo de inserção. salvar e sair é wq e sair e descartar é q!

Para desfazer último commit sem desfazer as modificações nos arquivos

git reset --soft HEAD~1