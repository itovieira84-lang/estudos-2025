# GitHub CLI - Guia de Referência

> Data: 17 de Fevereiro de 2026
> Conta: itovieira84-lang

---

## 🔧 Status da Conta

- **Conta:** itovieira84-lang
- **Token:** Configurado via gh CLI
- **Status:** ✅ Autenticado
- **CLI:** gh version 2.86.0

---

## 📋 Comandos Úteis

### **Repositórios**
```bash
# Listar seus repos
gh repo list --limit 20
gh repo list --visibility public
gh repo list --visibility private

# Criar novo repo
gh repo create nome-repo --public
gh repo create nome-repo --private

# Clonar repo
gh repo clone owner/repo

# Ver info do repo atual
gh repo view
```

### **Issues**
```bash
# Listar issues do repo atual
gh issue list
gh issue list --state open
gh issue list --state closed --limit 5

# Criar issue
gh issue create --title "Bug no login" --body "Descrição do erro"

# Ver issue específica
gh issue view 42

# Fechar issue
gh issue close 42
```

### **Pull Requests**
```bash
# Listar PRs
gh pr list
gh pr list --state merged

# Criar PR
gh pr create --title "Nova feature" --body "Descrição"

# Ver PR específico
gh pr view 55

# Verificar CI checks
gh pr checks 55

# Fazer merge
gh pr merge 55 --squash
```

### **Git Workflow**
```bash
# Commit e push em um comando
gh auth setup-git  # configura credenciais

# Status
gh status
```

### **CI/CD (GitHub Actions)**
```bash
# Listar runs recentes
gh run list --limit 10
gh run list --repo owner/repo

# Ver detalhes de uma run
gh run view <run-id>

# Ver logs de falhas
gh run view <run-id> --log-failed

# Rerun workflow
gh run rerun <run-id>
```

### **API Customizada**
```bash
# Qualquer endpoint da API REST
gh api repos/owner/repo/pulls/55
gh api repos/owner/repo/issues --jq '.[].title'

# GraphQL
gh api graphql -f query='
  query {
    viewer {
      login
      repositories(first: 10) {
        nodes { name }
      }
    }
  }'
```

### **Gists**
```bash
# Criar gist
gh gist create arquivo.txt --public
gh gist create arquivo.txt --private
```

---

## 🐍 Usando em Scripts

### **Exemplo: Criar repo de estudo automaticamente**
```bash
#!/bin/bash
REPO_NAME="estudo-$1"
gh repo create "$REPO_NAME" --private --description "Estudo de $1" --gitignore Python
gh repo clone "$REPO_NAME"
cd "$REPO_NAME"
echo "# Estudo de $1" > README.md
git add .
git commit -m "Initial commit"
git push
```

### **Exemplo: Listar issues por label**
```bash
gh issue list --label bug --json number,title,assignee --jq '.[] | "\(.number): \(.title)"'
```

---

## 🔗 Documentação

- **Manual gh:** https://cli.github.com/manual/
- **GitHub API:** https://docs.github.com/en/rest
- **Extensions:** `gh extension list`

---

*Configurado em 17/02/2026*
