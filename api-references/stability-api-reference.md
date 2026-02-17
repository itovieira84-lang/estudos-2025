# Stability AI API - Guia de Referência

> Data: 17 de Fevereiro de 2026
> API Key configurada para: ito.vieira84@gmail.com

---

## 🔧 Informações da Conta

- **Email:** ito.vieira84@gmail.com
- **ID:** user-x0Qcd2GGeGg4n6W1FJfnVR4v
- **Organização:** Personal (Owner)
- **Status:** ✅ Ativa

---

## 📡 Endpoints Principais

### 1. **Gerar Imagem (SD 3)**
```bash
curl -X POST "https://api.stability.ai/v2beta/stable-image/generate/sd3" \
  -H "Authorization: Bearer [API_KEY]" \
  -H "Content-Type: multipart/form-data" \
  -F "prompt=Um gato astronauta flutuando no espaço, arte digital detalhada" \
  -F "output_format=png" \
  -F "aspect_ratio=16:9" \
  -o "imagem_gerada.png"
```

### 2. **Gerar Imagem (SD Core)**
```bash
curl -X POST "https://api.stability.ai/v1/generation/stable-diffusion-v1-6/text-to-image" \
  -H "Content-Type: application/json" \
  -H "Authorization: [API_KEY]" \
  -d '{
    "text_prompts": [{"text": "uma paisagem cyberpunk futurista, neon, alta qualidade"}],
    "cfg_scale": 7,
    "samples": 1,
    "steps": 30
  }'
```

### 3. **Upscale de Imagem**
```bash
curl -X POST "https://api.stability.ai/v2beta/stable-image/upscale/fast" \
  -H "Authorization: Bearer [API_KEY]" \
  -F "image=@sua_imagem.png" \
  -F "output_format=png" \
  -o "imagem_upscaled.png"
```

### 4. **Editar Imagem (Inpainting)**
```bash
curl -X POST "https://api.stability.ai/v2beta/stable-image/edit/inpaint" \
  -H "Authorization: Bearer [API_KEY]" \
  -F "image=@imagem_original.png" \
  -F "mask=@mascara.png" \
  -F "prompt=substituir fundo por praia tropical" \
  -o "imagem_editada.png"
```

---

## ⚙️ Parâmetros Comuns

| Parâmetro | Descrição | Valores |
|-----------|-----------|---------|
| `prompt` | Descrição da imagem | Texto livre (máx 2000 chars) |
| `aspect_ratio` | Proporção | `16:9`, `1:1`, `3:2`, `4:3` |
| `output_format` | Formato | `png`, `webp`, `jpeg` |
| `cfg_scale` | Fidelidade ao prompt | `1-35` (7-12 é ideal) |
| `steps` | Passos de geração | `20-50` (30 é padrão) |
| `samples` | Número de imagens | `1-4` |
| `seed` | Reprodutibilidade | Número inteiro |

---

## 💡 Dicas de Prompting

### **Prompts que funcionam bem:**
```
"Uma paisagem futurista cyberpunk, neon roxo e azul, arranha-céus altos, 
chuva refletindo nas ruas, atmosfera noturna, Blade Runner style, 
8k highly detailed, cinematic lighting"
```

### **Estilos para adicionar:**
- `photorealistic` - Foto realista
- `digital art` - Arte digital
- `oil painting` - Pintura a óleo
- `anime style` - Estilo anime
- `cyberpunk` / `retrofuturistic` - Sci-fi
- `minimalist` - Minimalista

---

## 🎨 Modelos Disponíis

| Modelo | Endpoint | Uso |
|--------|----------|-----|
| Stable Diffusion 3 | `/v2beta/stable-image/generate/sd3` | Mais recente, melhor qualidade |
| SD 3 Turbo | `/v2beta/stable-image/generate/sd3-turbo` | Mais rápido, ligeiramente inferior |
| SD XL | `/v1/generation/stable-diffusion-xl-1024-v1-0` | Alta resolução (1024px) |
| SD 1.6 | `/v1/generation/stable-diffusion-v1-6` | Modelo clássico |

---

## ⚠️ Limitações

- **Resolução máxima:** 1024x1024 para SD XL
- **Créditos:** Verificar saldo em dreamstudio.stability.ai
- **Rate limits:** Dependem do plano (Free/Pro)
- **NSFW:** Automaticamente filtrado

---

## 🔗 Documentação Oficial

- API Docs: https://platform.stability.ai/
- Pricing: https://dreamstudio.stability.ai/pricing
- Community: https://discord.gg/stability-ai

---

*Última atualização: 17/02/2026*
