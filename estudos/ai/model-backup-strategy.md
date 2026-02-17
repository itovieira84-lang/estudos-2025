# Estratégia de Modelos - Configuração de Backup

> Data: 17 de Fevereiro de 2026
> Objetivo: Usar Gemini como backup para tarefas específicas

---

## 🎯 MODELOS DISPONÍVEIS

### **Primário: Kimi (Moonshot)**
- **Uso padrão:** Todas as interações normais
- **Força:** Conversação, raciocínio complexo, Português
- **Limite:** Conforme disponibilidade do gateway

### **Backup: Gemini 2.0 Flash**
- **Uso:** Fallback quando precisar
- **Força:** Velocidade, tasks simples, análise de imagem
- **Limite:** Rate limits do plano gratuito

### **Imagem: Stability AI**
- **Uso:** Geração de imagens
- **Primário e único** para este caso

---

## 🔄 QUANDO USAR GEMINI (BACKUP)

### **Use Gemini quando:**
1. ⚡ **Precisar de resposta ultra-rápida** - Gemini Flash é mais rápido
2. 📊 **Análise de dados/imagem** - Gemini tem boa visão
3. 🌍 **Traduções rápidas** - Bem otimizado para idiomas
4. 📝 **Sumarização longa** - Contexto grande (1M tokens)
5. 💤 **Kimi estiver indisponível** - Fallback técnico
6. 🔢 **Cálculos/Código simples** - Respostas diretas

### **Continue com Kimi quando:**
1. 🧠 **Raciocínio profundo** - Análises complexas
2. 💬 **Conversação contínua** - Contexto de longo prazo
3. 🎨 **Tarefas criativas** - Escrita, storytelling
4. 🔧 **Debugging complexo** - Problemas de código difíceis
5. 🇧🇷 **Nuances em Português** - Tom casual/explicativo

---

## ⚙️ COMO ACIONAR O BACKUP

### **Opção 1: Sub-agente com Gemini**
```
sessions_spawn(task="...", model="gemini")
```

### **Opção 2: Verificação automática**
Se Kimi der erro 429/limites → fallback para Gemini

### **Opção 3: Task-specific**
Tarefas pré-definidas que sempre usam Gemini:
- Análise de imagem
- Tradução de documentos
- Sumarização de PDFs
- Queries simples de FAQ

---

## 📋 WORKFLOWS CONFIGURADOS

### **Workflow A: Chat Rápido**
1. Tentar Kimi
2. Se timeout/erro → Gemini
3. Informar usuário sobre switch

### **Workflow B: Análise de Imagem**
1. Sempre Gemini (tem visão nativa)
2. Processar visual
3. Retornar descrição

### **Workflow C: Geração de Código**
1. Tentar Kimi (melhor para complexidade)
2. Se não conseguir → Gemini
3. Revisar resultado

### **Workflow D: Tradução**
1. Gemini (mais rápido para textos)
2. Revisão opcional com Kimi

---

## 🛠️ CONFIGURAÇÃO TÉCNICA

### **Comando para spawn com Gemini:**
```javascript
{
  "task": "Análise específica...",
  "agentId": "main",
  "model": "gemini",  // ou provider: "google"
  "runTimeoutSeconds": 120
}
```

### **Endpoints configurados:**
- Primary: `nvidia-nim/moonshotai/kimi-k2.5`
- Backup: `google/gemini-2.0-flash`
- Image: `stability-ai/stable-diffusion`

---

## 📊 MAPEAMENTO DE TAREFAS

| Tarefa | Primário | Backup | Motivo Backup |
|--------|----------|--------|---------------|
| Chat geral | Kimi | Gemini | Velocidade/Fallback |
| Gerar imagem | Stability | - | Único disponível |
| Analisar imagem | Gemini | - | Visão nativa |
| Tradução | Gemini | Kimi | Velocidade/custo |
| Resumir texto | Gemini | Kimi | Contexto longo |
| Debug código | Kimi | Gemini | Qualidade primeiro |
| Criar código | Kimi | Gemini | Complexidade |
| Pesquisar web | Kimi | Gemini | Autonomia |
| Escrever texto | Kimi | Gemini | Criatividade |
| Sequência numérica | Gemini | Kimi | Velocidade |

---

## 🔄 PROCEDIMENTO DE FALLBACK

### **Se Kimi falhar:**
1. Identificar erro (429, timeout, 500)
2. Verificar se tarefa aceita Gemini
3. Spawn sub-agente com Gemini
4. Informar usuário: *"Usando modelo de backup para esta tarefa..."*
5. Executar
6. Retornar resultado

### **Se Gemini falhar (rate limit):**
1. Aguardar 60 segundos
2. Re tentar ou informar usuário
3. Alternativa: usar Kimi se apropriado

---

## 💾 STATUS ATUAL

| Modelo | Status | Último Teste | Ação |
|--------|--------|--------------|------|
| Kimi | 🟢 Online | Agora | Padrão |
| Gemini | 🟡 Rate Limited | 17/02 10:28 | Aguardando reset |
| Stability | 🟢 Online | 17/02 10:00 | Imagem |

---

## 🔗 COMANDOS ÚTEIS

### **Forçar uso do Gemini:**
```
Dom, use o Gemini para [tarefa]
```

### **Voltar ao Kimi:**
```
Volta pro modelo principal
```

### **Verificar qual está usando:**
```
Qual modelo está ativo?
```

---

*Configuração de backup ativada em 17/02/2026*
