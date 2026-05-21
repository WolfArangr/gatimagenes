# Guía de uso de MIAU

Aprende a usar todas las características de MIAU para crear imágenes increíbles con inteligencia artificial.

## Tabla de contenidos

1. [Interfaz principal](#interfaz-principal)
2. [Generación de imágenes (txt2img)](#generación-de-imágenes-txt2img)
3. [Mejora de imágenes (img2img)](#mejora-de-imágenes-img2img)
4. [Edición local (Inpainting)](#edición-local-inpainting)
5. [Prompts efectivos](#prompts-efectivos)
6. [Parámetros avanzados](#parámetros-avanzados)
7. [Consejos y trucos](#consejos-y-trucos)

## Interfaz principal

### Componentes básicos

```
┌─────────────────────────────────────────────┐
│  [txt2img] [img2img] [Inpainting] [Extras]  │
├─────────────────────────────────────────────┤
│                                             │
│  Prompt: ___________________________        │
│  Negative Prompt: _________________        │
│                                             │
│  [Settings]  [Generate]                    │
│                                             │
│  Resultado:                                 │
│  ┌─────────────────────────────────────┐   │
│  │                                     │   │
│  │         [Imagen generada]           │   │
│  │                                     │   │
│  └─────────────────────────────────────┘   │
└─────────────────────────────────────────────┘
```

### Barra de pestañas
- **txt2img**: Genera imágenes desde cero mediante texto
- **img2img**: Modifica imágenes existentes
- **Inpainting**: Edita áreas específicas
- **Extras**: Herramientas adicionales (upscaling, face fix, etc.)

## Generación de imágenes (txt2img)

### Guía paso a paso

#### 1. Accede a la pestaña txt2img
La pestaña de txt2img es la predeterminada cuando abres MIAU.

#### 2. Escribe tu prompt (descripción)

En el campo **"Prompt"** describe la imagen que deseas:

**Ejemplo básico:**
```
a beautiful landscape with mountains and lake
```

**Ejemplo detallado:**
```
a woman with long red hair, wearing a white dress, standing in a field 
of sunflowers, golden hour light, professional photography, sharp focus
```

**Elementos clave de un buen prompt:**
- Sujeto principal (qué quieres ver)
- Atributos (color, textura, tamaño)
- Contexto (dónde, ambiente)
- Estilo (fotografía, pintura, digital art)
- Calidad (masterpiece, high quality, sharp focus)

#### 3. Prompt negativo (opcional)

En el campo **"Negative Prompt"** especifica lo que NO quieres:

```
deformed, ugly, bad anatomy, missing limbs, blurry, low quality
```

#### 4. Configura los parámetros

**Parámetros esenciales:**

| Parámetro | Rango | Recomendado | Descripción |
|-----------|-------|-------------|-------------|
| Sampling steps | 1-150 | 20-30 | Más pasos = mejor calidad, más lento |
| Sampling method | - | DPM++, Euler | Algoritmo de generación |
| CFG Scale | 1-30 | 7-12 | Control sobre el prompt (más = más literal) |
| Seed | - | -1 (aleatorio) | Para reproducir resultados |
| Width | 512-768 | 512 | Ancho de la imagen |
| Height | 512-768 | 512 | Alto de la imagen |

#### 5. Genera la imagen

Haz clic en el botón **"Generate"** y espera. La barra de progreso mostrará:
- Pasos completados
- Vista previa en tiempo real
- Tiempo estimado

#### 6. Descarga tu imagen

Una vez completa, la imagen aparecerá en el panel derecho. Haz clic en la imagen para descargarla o copia los parámetros para ajustes posteriores.

### Ejemplos de prompts

**Retrato:**
```
portrait of a beautiful woman with green eyes, studio lighting, 
professional photography, highly detailed, sharp focus, masterpiece
```

**Landscape:**
```
epic landscape with mountains, lake, forest, sunset light, 
oil painting style, dramatic lighting, ultra detailed
```

**Fantasía:**
```
a fantasy dragon on mountains, magical glow, cinematic lighting, 
concept art, highly detailed, sharp focus, artstation
```

**Objeto:**
```
a red apple on wooden table, professional product photography, 
sharp focus, high quality, intricate details
```

## Mejora de imágenes (img2img)

Transforma imágenes existentes añadiendo nuevos estilos o elementos.

### Paso a paso

#### 1. Ve a la pestaña "img2img"

#### 2. Carga una imagen

- Haz clic en el área de carga
- Selecciona una imagen (PNG, JPG, etc.)
- O arrastra y suelta la imagen

#### 3. Escribe un nuevo prompt

Describe cómo deseas que cambie la imagen:

```
turn this into an oil painting, van gogh style, vibrant colors
```

#### 4. Ajusta "Denoising Strength"

Este parámetro controla cuánto cambia la imagen:

| Valor | Efecto |
|-------|--------|
| 0.0 - 0.3 | Cambios muy sutiles, conserva la imagen original |
| 0.4 - 0.6 | Cambios moderados, mezcla imagen y prompt |
| 0.7 - 1.0 | Cambios drásticos, recrea casi completamente |

**Recomendación**: Empieza con 0.5 y ajusta según necesites

#### 5. Configura otros parámetros

Similar a txt2img, ajusta:
- Sampling steps (20-30 recomendado)
- CFG Scale (7-12 recomendado)
- Seed (para reproducibilidad)

#### 6. Genera

Haz clic en **"Generate"** y espera.

### Ejemplos de uso

**Cambiar estilo:**
- Original: Fotografía de una casa
- Prompt: `convert to a watercolor painting, soft colors, artistic`

**Mejorar calidad:**
- Original: Foto borrosa
- Prompt: `enhance this image, make it sharp, increase resolution, improve quality`

**Cambiar ambiente:**
- Original: Retrato en estudio
- Prompt: `place this person in a fantasy forest, magical lighting, mystical atmosphere`

## Edición local (Inpainting)

Edita solo partes específicas de una imagen mientras mantienes el resto.

### Paso a paso

#### 1. Ve a la pestaña "Inpainting"

#### 2. Carga la imagen

Haz clic en el área de carga y selecciona tu imagen.

#### 3. Dibuja el área a editar

- La zona de dibujo aparecerá sobre la imagen
- Dibuja con el ratón sobre el área que deseas editar (aparecerá en rojo)
- Usa el borrador si cometes un error
- Aumenta/disminuye el tamaño del pincel según necesites

#### 4. Escribe el prompt

Describe qué quieres que aparezca en esa área:

```
a red rose
```

#### 5. Configura parámetros

- Mask blur: Desenfoque de los bordes de la máscara (0-64)
- Inpaint padding: Área adicional alrededor de la máscara
- Sampling steps: 20-50 pasos
- CFG Scale: 7-12

#### 6. Genera

Haz clic en **"Generate"** y MIAU modificará solo esa área.

### Ejemplos

**Cambiar un objeto:**
- Imagen: Una mesa con un jarrón azul
- Máscara: Dibuja sobre el jarrón
- Prompt: `a golden vase with flowers`
- Resultado: El jarrón cambia de color

**Agregar elementos:**
- Imagen: Una habitación vacía
- Máscara: Dibuja en una esquina
- Prompt: `a comfortable red sofa`
- Resultado: Aparece el sofá donde dibujaste

**Eliminar objetos:**
- Imagen: Foto con una persona
- Máscara: Dibuja alrededor de la persona
- Prompt: (dejar vacío o describir el fondo)
- Resultado: La persona se reemplaza con el fondo

## Prompts efectivos

### Estructura recomendada

```
[Sujeto], [Atributos], [Acción], [Contexto], [Estilo], [Calidad]
```

### Ejemplos por categoría

**Naturaleza:**
```
majestic eagle flying over snow-covered mountains, dramatic lighting, 
golden hour, sharp focus, ultra detailed, masterpiece
```

**Personas:**
```
a 25-year-old woman with flowing blonde hair, wearing a red summer dress, 
smiling warmly, standing in a sunflower field, soft lighting, 
professional portrait photography
```

**Arquitectura:**
```
a futuristic glass and steel building, modern architecture, 
minimalist design, sunset lighting, wide angle shot, professional 
photography, sharp focus
```

**Animales:**
```
a majestic lion with a flowing mane, sitting on a rock, 
African savanna background, golden sunlight, ultra realistic, 
wildlife photography, national geographic style
```

### Técnicas de prompting

#### Uso de pesos

Enfatiza o reduce términos:

```
a (beautiful:1.5) woman wearing a (red:1.2) dress in a (garden:0.8)
```

- `(término:1.0)` = peso normal
- `(término:1.5)` = 50% más énfasis
- `(término:0.7)` = 30% menos énfasis

#### Negación en prompts

```
a woman, NOT wearing glasses, NOT bald, NOT old
```

#### Alternativas

```
a woman wearing {red|blue|green} dress
```

Genera variantes con diferentes colores.

#### Referencia a artistas

```
in the style of Caravaggio, dramatic lighting, classical painting
```

```
concept art by Artgerm, cinematic lighting, trending on artstation
```

### Palabras clave para calidad

- masterpiece
- high quality
- sharp focus
- highly detailed
- intricate details
- ultra realistic
- 8k
- HDR
- professional
- best quality

### Prompts negativos efectivos

```
deformed, distorted, ugly, bad anatomy, wrong anatomy, extra limbs, 
missing limbs, floating limbs, disconnected limbs, malformed hands, 
blur, blurry, low quality, pixelated, jpeg artifacts, watermark, 
text, caption, monochrome, oversaturated
```

## Parámetros avanzados

### Sampling methods

Diferentes algoritmos de generación:

| Método | Velocidad | Calidad | Mejor para |
|--------|-----------|---------|-----------|
| Euler | Rápido | Buena | Inicio |
| Euler Ancestral | Rápido | Muy buena | Variedad |
| DPM++ | Lento | Excelente | Máxima calidad |
| DDIM | Moderado | Buena | Consistencia |

**Recomendación**: Prueba con Euler o DPM++ para empezar.

### CFG Scale

Control de cuánto el modelo sigue tu prompt:

- **3-5**: Muy creativo, poco fiel al prompt
- **7-12**: Balance ideal (recomendado)
- **15-20**: Muy literal, menos creativo
- **20+**: Puede saturar la imagen

### Seed

Número para reproducir resultados exactos:

```
Seed: 12345
```

Usar el mismo seed con mismo prompt y parámetros = misma imagen

Para diferentes variaciones del mismo prompt:
```
Seed: -1 (aleatorio cada vez)
```

### Batch size y Batch count

- **Batch size**: Imágenes generadas simultáneamente (requiere más VRAM)
- **Batch count**: Cuántas tandas generar

Ejemplo: Batch size 2, Batch count 3 = 6 imágenes totales

### Resolution (Resolución)

Tamaños recomendados (múltiplos de 64):

- 512x512 (estándar, rápido)
- 512x768 (vertical)
- 768x512 (horizontal)
- 768x768 (alta calidad, lento)

**Nota**: Resoluciones más altas requieren más VRAM.

## Consejos y trucos

### Maximizar calidad

1. **Prompts descriptivos**: Sé específico y detallado
2. **Negativos efectivos**: Define claramente lo que NO quieres
3. **Parámetros balanceados**: CFG 7-12, Steps 25-35
4. **Modelos especializados**: Usa modelos específicos para temas concretos

### Optimizar velocidad

1. Reduce la resolución a 512x512
2. Disminuye los pasos a 15-20
3. Usa batch size 1
4. Desactiva preview en tiempo real si es muy lento

### Resolver problemas comunes

**Imágenes deformadas:**
- Añade "high quality" al prompt
- Reduce CFG Scale
- Aumenta los pasos de muestreo

**Colores incorrectos:**
- Sé más específico en el prompt: "bright red" en lugar de "red"
- Aumenta el peso del color: `(red:1.3) dress`

**Imágenes borrosas:**
- Añade "sharp focus" al prompt
- Aumenta los pasos a 30+
- Cambia el sampling method

**Falta de detalles:**
- Añade "highly detailed" o "intricate details"
- Aumenta CFG Scale (pero no demasiado)
- Usa prompts más detallados

### Flujo de trabajo recomendado

1. **Inicio**: Usa parámetros por defecto con prompt simple
2. **Iteración**: Guarda el seed del resultado que te guste
3. **Refinamiento**: Ajusta prompts y parámetros basándote en resultados
4. **Finalización**: Aumenta resolución y pasos para versión final

### Guardar configuraciones

- Los parámetros se guardan con cada imagen
- Haz clic en la imagen para cargar automáticamente los parámetros
- Arrastra la imagen a la zona de prompts para copiar metadatos

---

**Consejos finales:**
- Experimenta con diferentes prompts
- Guarda tus mejores resultados
- Mantén notas de qué funciona bien
- Participa en la comunidad compartiendo tus creaciones

¿Necesitas más ayuda? Consulta [README.md](README.md) o abre un issue en [GitHub](https://github.com/WolfArangr/gatimagenes/issues)
