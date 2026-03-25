---
name: prompt-optimizer
description: |
  Activa esta skill cuando el usuario quiera optimizar un prompt antes de guardarlo.
  Se usa después del comando /prompt con la bandera "optimizar" o "optimiza".

  Ejemplos de activación:
  - "/prompt optimizar [contenido del prompt]"
  - "/prompt optimiza este prompt para mejorar los resultados"
  - "optimizar: [prompt]"

  Esta skill analiza prompts de generación de imagen y video (especialmente para Grok Imaging)
  y propone mejoras en estructura, detalle técnico, y efectividad antes de que el usuario
  lo guarde en su colección.
---

# Prompt Optimizer

Skill especializada en mejorar prompts de generación de imagen y video antes de su almacenamiento.

## Cuándo usar esta skill

- El usuario escribe `/prompt optimizar` seguido de un prompt
- El usuario quiere mejoras en un prompt antes de guardarlo
- El usuario menciona "optimiza este prompt" o variantes similares

## Flujo de trabajo

### 1. Detectar el tipo de contenido

Analiza el prompt para determinar:
- **Tipo principal**: `image` | `video` | `code`
- **Modelo objetivo**: Grok Imaging, Midjourney, DALL-E, Stable Diffusion, etc.
- **Subtipo**: basado en el contenido (selfies, photorealistic, portraits, etc.)

### 2. Analizar el prompt actual

Identifica:
- Qué elementos describe bien el prompt
- Qué elementos faltan o son vagos
- Qué términos podrían mejorarse para el modelo objetivo
- Si hay redundancias o contradicciones

### 3. Generar propuestas de optimización

Crea **3 versiones** del prompt optimizado:

#### Versión A: Enfocada en fotorrealismo
- Maximiza detalles texturales (piel, tela, materiales)
- Incluye especificaciones de iluminación natural
- Referencias a calidad DSLR/cinematográfica
- Términos: "photorealistic", "hyperrealistic", "RAW", "unretouched"

#### Versión B: Enfocada en estilo artístico/dirección creativa
- Enfatiza composición visual y storytelling
- Incluye referencias de estilo (cine, fotografía, arte)
- Términos de atmósfera y mood
- Especificaciones de color grading

#### Versión C: Enfocada en consistencia técnica
- Estructura clara para reproducibilidad
- Parámetros específicos del modelo
- Términos que mejor funcionan con el modelo objetivo
- Balance entre detalle y claridad

### 4. Estructura de salida

Presenta las propuestas en este formato:

```markdown
## Análisis del prompt original

**Tipo detectado:** {image|video}/{subtype}
**Modelo objetivo:** {Grok Imaging|Midjourney|etc.}
**Fortalezas:** {qué funciona bien}
**Oportunidades de mejora:** {qué puede mejorarse}

---

## Propuesta A: Fotorrealismo Máximo

```yaml
---
type: {type}
subtype: {subtype}
tags: [tag1, tag2, tag3]
camera:
  angle: {angle}
  shot_type: {shot_type}
subject:
  pose: {pose}
  orientation: {orientation}
---
```

**Prompt optimizado:**
[Contenido del prompt mejorado]

**Notas de uso:**
- Cuándo usar esta versión
- Qué resultados esperar
- Tips adicionales

---

## Propuesta B: Dirección Creativa
[Similar estructura]

---

## Propuesta C: Consistencia Técnica
[Similar estructura]

---

## Recomendación final

Basado en el análisis, recomiendo **Propuesta {A|B|C}** porque:
[Explicación de por qué esta versión es más adecuada para el caso de uso]

¿Quieres que guarde alguna de estas versiones con `/prompt`?
```

## Reglas específicas por tipo

### Para prompts de imagen (Grok Imaging)

**Optimizaciones clave:**
- Incluir "photorealistic" al inicio para fotorrealismo
- Especificar calidad de cámara: "DSLR quality", "Canon EOS R6 II", "Sony A7IV"
- Detallar iluminación: "soft natural lighting", "golden hour", "overcast day"
- Para retratos: mencionar textura de piel, poros visibles, autenticidad
- Usar "IGNORE all original textures..." cuando se quiere re-renderizar
- Incluir resolución: "4K", "8K", "high resolution"

**Patrones efectivos para Grok:**
```
"Transform this into a handheld and spontaneous amateur selfie, suggesting an authentic smartphone photo with DSLR-quality colour and detail, using an advanced upscaling algorithm comparable to the results from [CAMERA], based on this image, featuring the same [SUBJECT]."

"IGNORE all original textures, noise, and pixel data from the reference image. USE ONLY the spatial composition, depth map, and geometric structure. Re-render every surface from scratch..."
```

### Para prompts de video

**Optimizaciones clave:**
- Especificar ángulo de cámara explícitamente
- Describir movimiento: velocidad, dirección, dinamismo
- Incluir contexto ambiental para motion coherente
- Mencionar estabilización si aplica
- Para selfies: especificar posición de la cámara (altura, distancia)

### Para prompts de código

**Optimizaciones clave:**
- Ser específico sobre el lenguaje y versión
- Incluir requisitos de rendimiento si aplica
- Mencionar patrones o arquitecturas preferidas
- Especificar manejo de errores esperado

## Ejemplos de entrada y salida

### Ejemplo 1: Imagen de retrato

**Entrada:**
```
/prompt optimizar una foto de una mujer sonriendo, en el parque, luz natural
```

**Salida esperada:**
Tres propuestas:
- A: Fotorrealista con especificaciones DSLR, textura de piel, iluminación dorada
- B: Estilo editorial de moda con color grading específico
- C: Estructura técnica clara con parámetros reproducibles

### Ejemplo 2: Video selfie

**Entrada:**
```
/prompt optimizar video selfie caminando por la calle
```

**Salida esperada:**
Tres propuestas:
- A: Fotorrealista con especificaciones de movimiento natural
- B: Estilo cinematic con referencias de películas
- C: Técnica con ángulo, velocidad y estabilización específicas

## Notas importantes

1. **No guardar automáticamente**: Esta skill solo propone, el guardado se hace con el comando `/prompt` normal
2. **Mantener metadata completa**: Las propuestas deben incluir toda la estructura YAML requerida
3. **Explicar cambios**: Siempre explicar por qué se sugiere una mejora
4. **Respetar intención original**: No cambiar el concepto central, solo mejorar su expresión
5. **Adaptar al modelo**: Las optimizaciones deben considerar qué modelo usará el usuario (principalmente Grok Imaging)
