# Git e Github

## 📌 Introdução

- **Git**: Sistema de versionamento para controlar versões (commits) de projetos
- **Github**: Serviço online de hospedagem para repositórios Git

🔹 Um projeto controlado pelo Git é chamado de **repositório de versionamento**.

### 🔄 Repositório Remoto vs Local

| Tipo          | Descrição                                                                 |
|---------------|---------------------------------------------------------------------------|
| **Remoto**    | Cópia "oficial" armazenada em um servidor (ex: Github)                   |
| **Local**     | Cópia no computador do desenvolvedor, onde as alterações são feitas      |

🔹 Fluxo típico:
1. Desenvolvedor clona o repositório remoto (`git clone`)
2. Faz alterações localmente
3. Cria novos commits
4. Envia as alterações de volta ao servidor

⚠️ Importante: `git clone` copia o **repositório completo** (com todo histórico), não apenas os arquivos atuais.

## ⚙️ Configuração Inicial

```bash
# Configurar identidade
git config --global user.name "Seu nome"
git config --global user.email "Seu email de cadastro do github"

# Verificar configurações
git config --list

# Mostra o histórico completo
git log

# Versão resumida (uma linha por commit)
git log --oneline

git diff: Mostra diferenças em arquivos modificados

git checkout: Permite reverter arquivos temporariamente para o estado de um commit ou branch específico
```

# Git e GitHub: Resolvendo Problemas Comuns

Este guia aborda problemas comuns ao usar Git e GitHub, explicando de forma clara as soluções e os comandos necessários para resolver cada situação. Abaixo, você encontrará os passos detalhados com exemplos para facilitar o seu entendimento.

```bash
# 1. A Área de Stage
# A área de stage é onde você coloca os arquivos que serão comitados, ou seja, você prepara as mudanças para serem registradas no histórico do repositório.

# Para remover arquivos da área de stage, mas sem deletá-los do seu diretório local, use o comando:
git reset

# Caso você tenha alterações que não foram salvas e deseja descartá-las, use os seguintes comandos para limpar o seu repositório local:
git clean -df     # Remove arquivos não rastreados do diretório
git checkout -- .  # Desfaz as alterações feitas nos arquivos

# 2. Trabalhando com o Vim
# - No Vim, pressione 'i' para entrar no modo de inserção (onde você pode editar o arquivo).
# - Para **salvar e sair**, use o comando ':wq'.
# - Para **sair e descartar alterações**, use o comando ':q!'.

# 3. Desfazendo Commits
# Se você cometeu algo errado ou deseja desfazer um commit, existem duas formas de lidar com isso, dependendo do que você deseja manter:

# 3.1. Para **desfazer o último commit**, mas **manter as modificações nos arquivos**:
git reset --soft HEAD~1

# 3.2. Para **deletar um commit** e também **remover as modificações dos arquivos**, use o seguinte comando:
git reset --hard <commit-hash>
# Aqui, substitua `<commit-hash>` pelo identificador do commit que você quer voltar. Este comando apagará tanto o commit quanto as modificações feitas após ele.

# 4. Atualizando seu Repositório Local
# Para **trazer as mudanças do repositório remoto para o repositório local** e evitar conflitos com commits que foram feitos diretamente no GitHub:
git pull origin main

# Esse comando vai garantir que seu repositório local esteja atualizado com as últimas alterações feitas no repositório remoto. Após isso, você pode fazer o push normalmente.

# 5. Como Resolver um Push Rejeitado
# Quando você tenta fazer um **push** e ele é rejeitado, é porque seu repositório local está **desatualizado** em relação ao repositório remoto.
# O Git não permite o push de alterações que conflitariam com o histórico remoto.

# Para resolver isso, primeiro, atualize seu repositório local com as últimas alterações:
git pull origin main

# Após atualizar seu repositório local, se houver conflitos, resolva-os e tente fazer o push novamente.

# 6. Sobrescrevendo o Histórico no GitHub
# Em algumas situações, você pode precisar **sobrescrever o histórico no repositório remoto**. Isso pode ser necessário se você fez alterações no seu repositório local e quer forçar essas alterações no remoto.
# **Cuidado:** Este comando pode sobrescrever o histórico remoto e pode causar a perda de dados importantes!

git push -f
# O `-f` (force) vai forçar o envio das suas alterações, mesmo que o histórico do repositório remoto seja diferente. Use este comando com cuidado, especialmente quando estiver trabalhando em projetos colaborativos.
```

# 🌿 Git e GitHub: Trabalhando com Branches


Branches (ou ramificações) são linhas do tempo independentes dentro do seu repositório Git. Elas permitem que você trabalhe em funcionalidades, correções ou testes sem impactar diretamente a branch principal (geralmente a `main`). Isso torna o desenvolvimento mais seguro, organizado e colaborativo.

```bash
# 📋 LISTAR BRANCHES EXISTENTES
# Mostra todas as branches do seu repositório local. A branch atual estará marcada com um asterisco (*)
git branch

# 🌱 CRIAR UMA NOVA BRANCH
# Cria uma nova branch chamada "nome-da-branch"
git branch nome-da-branch

# 🔀 CRIAR E MUDAR PARA A NOVA BRANCH DIRETAMENTE
git checkout -b nome-da-branch

# 🔄 TROCAR DE BRANCH
# Muda para outra branch já existente
git checkout nome-da-branch

# ❌ DELETAR UMA BRANCH
# Deleta uma branch local SOMENTE se ela já foi mesclada (ação segura)
git branch -d nome-da-branch

# ⚠️ FORÇAR A DELEÇÃO DE UMA BRANCH
# Deleta a branch mesmo que ela não tenha sido mesclada (ação destrutiva!)
git branch -D nome-da-branch

# 🔀 MERGE ENTRE BRANCHES
# Merge significa "mesclar". Você incorpora as alterações de uma branch na outra.
# O MERGE deve ser feito a partir da branch de DESTINO.

# Exemplo: para mesclar a branch "ft-login" na "main"
# 1. Vá para a branch main:
git checkout main

# 2. Faça o merge:
git merge ft-login

# 🎯 MERGE FAST-FORWARD
# Esse tipo de merge ocorre quando não houve divergência entre os históricos das branches.
# O Git apenas "avança o ponteiro" da branch principal.

# OBS: sempre atualize sua branch de feature com a main ANTES de mesclar no final do processo.
# Isso evita conflitos e garante que sua feature esteja atualizada com o código mais recente.

# 💡 SOBRE O git pull
# O git pull é um atalho que faz:
# git fetch (traz alterações do remoto) + git merge (mescla com seu branch atual)

# ✅ PROCEDIMENTO DE PULL REQUEST

# NUNCA atualize diretamente a branch main enquanto a feature não estiver homologada.
# Isso porque geralmente a main está ligada a um processo automatizado (CI/CD) que pode enviar o código para PRODUÇÃO.

# Fluxo correto:
# 1. Esteja na branch main e atualize ela com o que está no remoto:
git checkout main
git pull origin main

# 2. Volte para a branch da sua feature:
git checkout nome-da-feature

# 3. Mescle a main na sua feature para garantir que ela esteja atualizada:
git merge main

# 4. Envie sua branch para o GitHub:
git push -u origin nome-da-feature

# 5. Agora sim, crie o pull request no GitHub para que a branch feature seja mesclada na main.

# 🌍 FORK + PULL REQUEST (contribuindo para projetos open source)

# Mesmo sem ter permissão de escrita em um repositório, você pode contribuir com o modelo fork + PR:

# 1. Faça um fork do repositório original para o seu GitHub
# 2. Clone o repositório forkado para sua máquina:
git clone https://github.com/seu-usuario/nome-do-repositorio.git

# 3. Crie e altere para uma nova branch:
git checkout -b minha-feature

# 4. Faça as alterações no código, commits, etc.

# 5. Envie suas alterações para seu repositório forkado:
git push -u origin minha-feature

# 6. Acesse o repositório original no GitHub e clique em "Compare & Pull Request" para enviar sua contribuição.
```