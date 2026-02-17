# Técnicas Avançadas de Prompting para IA de Imagem e Vídeo (2025)

> Data: 17 de Fevereiro de 2026
> Tema: Prompt Engineering para Midjourney, DALL-E 3, Stable Diffusion/Flux, Runway e Pika

---

## 🎯 PRINCÍPIOS FUNDAMENTAIS

### **1. Estrutura de Prompt Ideal**

A fórmula universal para prompts efetivos:

```
[SUJEITO] + [AÇÃO/CONTEXTO] + [AMBIENTE/CENÁRIO] + [ESTILO] + [TÉCNICA/QUALIDADE] + [PARÂMETROS]
```

**Exemplo aplicado:**
```
A majestic lion (sujeito) standing on a rocky cliff (ação/contexto), 
at golden hour with dramatic clouds (ambiente), photorealistic wildlife 
photography (estilo), 8k resolution, sharp focus, National Geographic style 
(técnica/qualidade)
```

---

## 🔷 MIDJOURNEY

### **Parâmetros Essenciais**

| Parâmetro | Descrição | Exemplos |
|-----------|-----------|----------|
| `--ar` | Aspect ratio | `--ar 16:9`, `--ar 2:3` |
| `--s` | Stylization (0-1000) | `--s 250` (padrão), `--s 750` (mais artístico) |
| `--c` | Chaos/variabilidade (0-100) | `--c 25` (mais variedade) |
| `--seed` | Reprodutibilidade | `--seed 123456` |
| `--no` | Negative prompt | `--no blur, low quality` |
| `--iw` | Image weight | `--iw 2.0` (referência de imagem forte) |
| `--tile` | Padrão repetível | Para texturas |
| `--q` | Quality | `--q 2` (mais detalhes, mais lento) |

### **Técnicas Avançadas**

#### **Multi-Prompts (::)**
Separar conceitos com `::` e atribuir pesos:
```
hot::2 dog (hot dog forte)
hot::0.5 dog (hot fraco, dog forte)
```

#### **Prompts de Imagem (Image Prompts)**
Usar URL de imagem + texto descritivo:
```
https://upload.wikimedia.org/sunflower.png a field of --ar 16:9
```

#### **Permutações {}**
Testar variações rapidamente:
```
a {cyberpunk, steampunk, solarpunk} cityscape --ar 16:9
```
Gerará 3 imagens com cada estilo.

### **Template Midjourney (Prompt Otimizado)**

```markdown
/imagine prompt: [SUJEITO PRINCIPAL], [DESCRIÇÃO DETALHADA], 
[ILUMINAÇÃO: golden hour/studio lighting/dramatic lighting/neon], 
[COMPOSIÇÃO: wide shot/macro/bird's eye], 
[ESTILO: photorealistic/illustration/cyberpunk/Art Nouveau], 
[TÉCNICA: 8k, highly detailed, octane render/Unreal Engine], 
--ar [RATIO] --s [STYLIZATION] --q [QUALITY]
```

### **Erros Comuns Midjourney**

❌ **Prompt genérico:**
```
a beautiful landscape
```

✅ **Prompt otimizado:**
```
a serene Japanese garden at dawn, Zen aesthetic with carefully raked sand patterns, 
cherry blossom trees in full bloom, wooden torii gate in the background, 
misty atmosphere with soft golden light, minimalist composition, 
fine art photography style --ar 4:5 --s 500 --q 2
```

---

## 🔷 DALL-E 3

### **Princípio Fundamental: "Descriptive Prompting"**

DALL-E 3 **não precisa** de prompt engineering complexo. Funciona melhor com descrições naturais e detalhadas.

### **Estrutura Recomendada**

```
"Create an image of [SUJEITO] [AÇÃO] [LOCAL/CONTEXTO], 
[DETALHES DA CENA], [ILUMINAÇÃO], [FILME/CÂMERA/ESTILO], mood/atmosphere"
```

### **Dicas Específicas DALL-E 3**

1. **Não force "art styles"** - DALL-E 3 recusa estilos de artistas vivos
2. **Descreva visualmente** - Em vez de "estilo Van Gogh", descreva: "swirling brushstrokes, vibrant colors"
3. **Seja específico nas dimensões** - "quadrado", "panorâmico", "formato Instagram"

### **Template DALL-E 3**

```
A [ADJECTIVE] [SUBJECT] [VERB] [LOCATION], 
[LIGHTING: bathed in golden hour light/backlit by sunset], 
[COMPOSITION: rule of thirds/centered subject], 
[STYLE: cinematic/photorealistic/documentary], 
[QUALITY: 8k, sharp focus, shallow depth of field], 
[MOOD: serene/dramatic/whimsical]
```

---

## 🔷 STABLE DIFFUSION / FLUX

### **Anatomia do Prompt (SD/SDXL)**

```
(subject), (action/scene), (environment), (lighting), (style), (quality), (artists)
```

### **Negative Prompts (Cruciais para SD)**

```
low quality, blurry, deformed, ugly, duplicate, watermark, 
signature, text, cropped, worst quality, normal quality, 
jpeg artifacts, error, sketch, extra limbs, bad anatomy, 
disfigured, mutation, mutated
```

### **Técnicas de Ordenação**

```
(emphasis)          → aumenta peso em 1.1x
((strong emphasis)) → aumenta peso em 1.21x
[de-emphasis]       → diminui peso em 0.9x
```

### **Template Stable Diffusion**

```
(masterpiece), (best quality), (ultra-detailed), (8k), 
[SUBJECT], [DETAILED DESCRIPTION], 
[BACKGROUND: detailed background], 
[LIGHTING: volumetric lighting/cinematic lighting], 
[STYLE: digital painting, concept art], 
by [ARTIST REFERENCES]
```

---

## 🔷 RUNWAY (Geração de Vídeo)

### **Motion Prompting**

```
"A [SUBJECT] [MOVEMENT], camera [CAMERA MOVEMENT], 
[SPEED], [QUALITY DESCRIPTORS]"
```

### **Motion Controls**

**Camera Movements:**
- `pan left/right/up/down`
- `zoom in/out`
- `dolly in/out`
- `handheld`, `gimbal smooth`

**Motion Strength:**
- `subtle motion`
- `controlled motion`  
- `dynamic motion`

---

## 🔷 PIKA (Pikaformance)

### **Prompt Structure**

```
"[IMAGE PROMPT], motion: [ACTION], camera: [MOVE], mood: [ATMOSPHERE]"
```

---

## 🎨 TERMOS VISUAIS ESSENCIAIS

### **Estilos Artísticos**

| Termo | Uso |
|-------|-----|
| `photorealistic` | Fotografia real |
| `cinematic` | Estilo filme |
| `concept art` | Arte de jogo/filme |
| `illustration` | Ilustração digital |
| `oil painting` | Pintura óleo |
| `minimalist` | Minimalismo |

### **Iluminação**

```
Golden hour     → luz dourada do amanhecer
dramatic        → alto contraste
studio          → iluminação controlada
rim lighting    → luz de contorno
volumetric      → raios de luz visíveis
neon            → iluminação neon
```

### **Composição/Ângulos**

```
Wide shot       → plano geral
Close-up        → close
Macro           → macro
Bird's eye      → vista de cima
Dutch angle     → ângulo holandês
Leading lines   → linhas guia
```

### **Qualidade**

```
8k, highly detailed, sharp focus, octane render, Unreal Engine 5, 
architecture photography, HDR, RAW photo, shallow depth of field
```

---

## 📋 TEMPLATES PRONTOS

### **Retrato Fotorealista**
```
Editorial portrait of a [NATIONALITY] [AGE] [GENDER] with [FEATURE], 
fbathed in golden hour light, shallow depth of field, 
professional studio quality, Leica 85mm f/1.4, bokeh background, 
captured with high-end equipment, fashion photography style
```

### **Paisagem Cenográfica**
```
Epic [ENVIRONMENT: mountain range/coastal cliff/forest] at [TIME], 
dramatic sky with scattered clouds, volumetric lighting through mist, 
8K resolution, landscape photography, centered composition, 
national geographic style, highly detailed textures
```

### **Produto Comercial**
```
[PRODUCT] floating in mid-air, studio lighting setup, 
soft shadows, gradient background, professional product photography, 
depth of field, ray tracing reflections, 8K, commercial advertising style
```

### **Cena de Vídeo (Runway/Pika)**
```
[SUBJECT] walking through [LOCATION], camera slowly dolly in, 
subtle motion in background elements, cinematic color grading, 
24fps film look, shallow depth of field, professional color correction
```

---

## 🔗 FONTES

- huggingface.co/docs/diffusers
- promptbase.com
- openai.com/dall-e-3
- runwayml.com
- pika.art

---

*Documento criado em 17/02/2026. Técnicas compiladas de múltiplas fontes técnicas.*
