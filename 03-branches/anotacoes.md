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