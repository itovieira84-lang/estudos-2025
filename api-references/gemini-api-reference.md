# Google Gemini API - Guia de Referência

> Data: 17 de Fevereiro de 2026
> API Key configurada (Free Tier)

---

## 🔧 Status da Conta

- **Plano:** Free Tier (gratuito)
- **Modelos disponíveis:** Gemini 2.0 Flash, Gemini 1.5 Pro/Flash
- **Status:** ✅ Ativa (com limites de quota)

---

## 📊 Limites (Free Tier)

| Modelo | RPM | RPD | TPM | TPD |
|--------|-----|-----|-----|-----|
| **Gemini 2.0 Flash** | 15 | 1.500 | 1 milhão | - |
| **Gemini 1.5 Pro** | 2 | 50 | 32.000 | - |
| **Gemini 1.5 Flash** | 15 | 1.500 | 1 milhão | - |

**RPM** = Requisições por minuto  
**RPD** = Requisições por dia  
**TPM** = Tokens por minuto  
**TPD** = Tokens por dia

---

## 📡 Endpoints Principais

### 1. **Gemini 2.0 Flash (Recomendado)**
```bash
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=API_KEY" \
  -H 'Content-Type: application/json' \
  -X POST \
  -d '{
    "contents": [{
      "parts":[{"text": "Escreva uma história sobre um dragão"}]
    }]
  }'
```

### 2. **Gemini 1.5 Flash**
```bash
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=API_KEY" \
  -H 'Content-Type: application/json' \
  -X POST \
  -d '{
    "contents": [{
      "parts":[{"text": "Explique IA para uma criança de 8 anos"}]
    }]
  }'
```

### 3. **Streaming (resposta em tempo real)**
```bash
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:streamGenerateContent?key=API_KEY" \
  -H 'Content-Type: application/json' \
  -X POST \
  -d '{
    "contents": [{
      "parts":[{"text": "Conte uma piada curta"}]
    }]
  }'
```

---

## ⚙️ Parâmetros Comuns

```json
{
  "contents": [{
    "parts": [{"text": "Seu prompt aqui"}]
  }],
  "generationConfig": {
    "temperature": 0.9,
    "maxOutputTokens": 2048,
    "topP": 1,
    "topK": 1
  },
  "safetySettings": [
    {
      "category": "HARM_CATEGORY_DANGEROUS_CONTENT",
      "threshold": "BLOCK_NONE"
    }
  ]
}
```

| Parâmetro | Descrição | Padrão |
|-----------|-----------|--------|
| `temperature` | Criatividade (0-2) | 0.9 |
| `maxOutputTokens` | Tamanho máximo da resposta | 2048 |
| `topP` | Diversidade de sampling | 1 |
| `topK` | Top-k tokens | 1 |

---

## 📷 Processamento de Imagem

```bash
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?key=API_KEY" \
  -H 'Content-Type: application/json' \
  -X POST \
  -d '{
    "contents": [{
      "parts": [
        {"text": "Descreva esta imagem:"},
        {
          "inlineData": {
            "mimeType": "image/jpeg",
            "data": "BASE64_IMAGE_DATA"
          }
        }
      ]
    }]
  }'
```

---

## 💡 Modelos e Uso

### **Gemini 2.0 Flash**
- ✅ **Use para:** Tarefas rápidas, chats, sumarização
- ⚡ **Velocidade:** Extremamente rápido
- 💰 **Custo:** Grátis (até limites)

### **Gemini 1.5 Pro**
- ✅ **Use para:** Análise complexa, código, documentos longos
- 🧠 **Contexto:** Até 2 milhões de tokens
- 📄 **Ideal:** PDFs, vídeos longos

### **Gemini 1.5 Flash**
- ✅ **Uso geral:** Equilíbrio velocidade x qualidade
- 🎯 **Recomendado:** Maioria das tarefas

---

## 🐛 Tratamento de Erros

| Código | Significado | Solução |
|--------|-------------|---------|
| **429** | Rate limit excedido | Aguardar 1 minuto (reseta por minuto) |
| **400** | Bad request | Verificar formato JSON |
| **403** | API key inválida | Verificar chave |
| **503** | Serviço indisponível | Retry com backoff |

---

## 📝 Exemplos Práticos

### **Sumarizar texto**
```json
{
  "contents": [{
    "parts": [{"text": "Resuma em 3 frases: [seu texto aqui]"}]
  }]
}
```

### **Explicar código**
```json
{
  "contents": [{
    "parts": [{"text": "Explique o que este código faz:\n```python\ndef fib(n):\n    if n <= 1: return n\n    return fib(n-1) + fib(n-2)\n```"}]
  }]
}
```

### **Criar conteúdo**
```json
{
  "contents": [{
    "parts": [{"text": "Escreva um post de Instagram sobre sapatos casuais masculinos, tom descontraído, 150 palavras"}]
  }]
}
```

### **Tradução**
```json
{
  "contents": [{
    "parts": [{"text": "Traduza para inglês profissional: 'Gostaria de agendar uma reunião para discutir o projeto'"}]
  }]
}
```

---

## 🔗 Documentação Oficial

- **Overview:** https://ai.google.dev/
- **API Reference:** https://ai.google.dev/api
- **Pricing:** https://ai.google.dev/pricing
- **Rate Limits:** https://ai.google.dev/gemini-api/docs/rate-limits

---

*Última atualização: 17/02/2026*
