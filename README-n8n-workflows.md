# 🚀 Workflows n8n - Automação Vyve

Workflows prontos para importação no n8n Cloud.

---

## 📦 Workflows Disponíveis

### 1. `n8n-workflow-social-media-automation.json`
**Automação completa de redes sociais**

**O que faz:**
- Busca tweets sobre marketing digital/empreendedorismo
- Gera conteúdo original com OpenAI
- Publica simultaneamente em: Twitter, Facebook, Instagram
- Notifica no Telegram

**Nós incluídos:**
- Schedule Trigger (a cada 2 horas)
- Twitter Search
- OpenAI Generate
- Post Twitter
- Post Facebook  
- Post Instagram
- Notify Telegram

---

### 2. `n8n-workflow-twitter-complete.json`
**Automação específica do Twitter/X**

**O que faz:**
- Webhook para disparo manual
- Busca tweets por hashtag ou termo
- Gera conteúdo com Claude (Anthropic)
- Posta no Twitter
- Confirma no Telegram

**Nós incluídos:**
- Webhook Trigger
- Twitter API Search
- Claude Generate
- Process Tweet Text
- Post to Twitter
- Telegram Confirmation

**Modo de usar:**
```json
POST <webhook-url>
{
  "query": "#marketingdigital",
  "maxResults": 5
}
```

---

### 3. `n8n-workflow-meta-complete.json`
**Automação Facebook & Instagram**

**O que faz:**
- Webhook para criar posts
- Gera conteúdo com OpenAI
- Publica no Facebook e Instagram
- Notifica no Telegram

**Nós incluídos:**
- Webhook Trigger
- Generate Content (OpenAI)
- Post Facebook
- Post Instagram
- Notify Telegram

**Modo de usar:**
```json
POST <webhook-url>
{
  "theme": "Gestão de tráfego pago",
  "tone": "Profissional",
  "link": "https://vyve.com.br/artigo"
}
```

---

## 🔧 Como Importar

### Passo 1: Baixar os arquivos
1. Acesse: `https://github.com/itovieira84-lang/estudos-2025`
2. Baixe os arquivos JSON

### Passo 2: Configurar credenciais PRIMEIRO
Antes de importar, configure as credenciais:

1. **Vá em Settings → Credentials**
2. **Adicione cada uma:**

| Credencial | Tipo |
|------------|------|
| Twitter | OAuth2 |
| OpenAI | API Key |
| Anthropic (Claude) | API Key |
| Facebook | OAuth2 |
| Instagram | OAuth2 |
| Telegram | Bot Token |

### Passo 3: Importar workflows
1. **Workflows → Import from File**
2. Selecione o arquivo JSON
3. Clique **Active** (toggle)
4. Salve: **Ctrl+S**

---

## ⚠️ Configurações Necessárias

### Variáveis de ambiente (.env ou n8n settings):`
```
TELEGRAM_CHAT_ID=seu_chat_id_aqui
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
TWITTER_BEARER_TOKEN=...
TWITTER_API_KEY=...
TWITTER_API_SECRET=...
TWITTER_ACCESS_TOKEN=...
TWITTER_ACCESS_SECRET=...
FACEBOOK_ACCESS_TOKEN=...
INSTAGRAM_ACCESS_TOKEN=...
```

---

## 📋 Checklist de Ativação

- [ ] Todas as credenciais configuradas
- [ ] Variáveis de ambiente definidas
- [ ] Workflows importados
- [ ] Workflows ativados (toggle ON)
- [ ] Teste de webhook realizado
- [ ] Telegram recebendo notificações

---

## 🎯 Fluxo Recomendado de Uso

1. **Importar primeiro:** `n8n-workflow-social-media-automation.json` (automação completa)
2. **Testar:** Aguardar próximo trigger (a cada 2h)
3. **Adicionar:** `n8n-workflow-twitter-complete.json` (mais controle)
4. **Adicionar:** `n8n-workflow-meta-complete.json` (Meta específico)

---

## 🆘 Troubleshooting

### "Credential not found"
→ Configure as credenciais antes de importar

### "Execution failed"
→ Verifique se as variáveis de ambiente estão definidas

### "Rate limit exceeded"
→ Ajuste o Schedule Trigger para intervalos maiores

---

**Criado em:** 18/02/2026
**Para:** Vyve - Diretoria Estratégica de Marketing