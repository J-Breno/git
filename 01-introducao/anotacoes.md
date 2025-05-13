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
