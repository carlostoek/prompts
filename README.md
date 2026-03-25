# 🎯 Sistema de Gestión de Prompts

Sistema organizado para guardar, categorizar y buscar prompts de código, imágenes y video.

## 🚀 Optimización de Prompts (Nuevo)

Antes de guardar un prompt, puedes pedir optimizaciones para mejorar sus resultados:

### Comando
```
/prompt optimizar [tu prompt aquí]
```

### Qué hace
Genera **3 propuestas diferentes**, cada una enfocada en un aspecto:

| Propuesta | Enfoque | Ideal para |
|-----------|---------|------------|
| **A** | Fotorrealismo máximo | Retratos, texturas de piel, calidad DSLR |
| **B** | Dirección creativa | Estilo visual, mood, referencias cinematográficas |
| **C** | Consistencia técnica | Reproducibilidad, parámetros claros, estructura |

### Características incluidas en cada propuesta
- ✅ Metadata YAML completa (type, subtype, tags, camera, subject)
- ✅ Prompt optimizado para el modelo (principalmente Grok Imaging)
- ✅ Notas de uso específicas
- ✅ Explicación de por qué se sugiere cada mejora

### Ejemplo de uso
```
/prompt optimizar selfie caminando por la calle con ángulo bajo
```

**Resultado:**
- **Propuesta A**: Enfatiza fotorrealismo, textura natural de piel, iluminación dorada, especificaciones tipo DSLR
- **Propuesta B**: Enfatiza estilo cinematográfico, referencias de películas, color grading específico
- **Propuesta C**: Estructura técnica clara con ángulo exacto, velocidad de movimiento, parámetros reproducibles

Después de revisar, guarda la que prefieras con `/prompt [texto]`.

---

## 🗝️ Palabra Clave: PUMAS

- **Sin "Pumas"**: El sistema interpreta tu mensaje como un prompt para guardar
- **Con "Pumas"**: Modo conversación directa (normal)

## 📁 Estructura

```
prompts/
├── code/              # Prompts de programación
│   ├── python/
│   ├── javascript/
│   ├── sql/
│   └── general/
├── image/             # Prompts de generación de imagen
│   ├── photorealistic/
│   ├── artistic/
│   ├── characters/
│   └── landscapes/
├── video/             # Prompts de video (tu especialidad)
│   ├── selfies/       # Selfies con diferentes ángulos
│   ├── mirror/        # Frente al espejo
│   ├── poses/         # Poses estáticas
│   ├── movements/     # Movimientos dinámicos
│   └── camera-angles/ # Énfasis en ángulos específicos
└── index.md           # Índice buscable
```

## 🎬 Categorías de Video (Más Usadas)

### Selfies
- Ángulos: desde arriba, desde abajo, nivel de ojos
- Orientaciones: frontal, perfil, tres cuartos
- Framing: closeup, medio cuerpo

### Frente al Espejo
- Ángulos: directo, ligeramente lateral
- Orientaciones: frontal, espalda (mirando por encima del hombro)
- Reflejos: completos, parciales

### Poses
- Estáticas: parado, sentado, agachado
- Dinámicas: caminando, saltando, girando
- Por orientación: de frente, de perfil, de espaldas, 3/4

### Ángulos de Cámara (Prioridad Alta)
- **Low angle**: Desde abajo, potencia presencia
- **High angle**: Desde arriba, perspectiva dominante
- **Eye level**: Nivel de ojos, natural
- **Dutch angle**: Inclinado, dramático
- **Bird's eye**: Vista cenital total
- **Worm's eye**: Contrapicado extremo

## 📝 Formato de Prompts

Cada prompt incluye metadata YAML:

```yaml
---
id: abc123
type: video
subtype: selfies
tags: [selfie, angulo_bajo, perfil, urbano]
camera:
  angle: low_angle      # ángulo de cámara
  shot_type: selfie     # tipo de toma
subject:
  pose: parado          # pose del sujeto
  orientation: perfil   # orientación corporal
  framing: medio        # encuadre
created: 2025-01-30
usage_count: 0
---

# Título del Prompt

[Contenido del prompt aquí]

## Notas de uso
- Funciona mejor con luz natural
- Ideal para escenas urbanas
```

## 🔍 Búsquedas

Puedes pedir búsquedas como:
- "Busca prompts de selfies de perfil"
- "Muestrame prompts con ángulo bajo"
- "Prompts de espejo de espaldas"
- "Busca saltos dinámicos"

## 💡 Ejemplos de Uso

### Guardar un prompt
```
Selfie tomada desde ángulo bajo, persona de perfil caminando,
efecto de movimiento dinámico, fondo urbano desenfocado
```
→ Se guarda automáticamente en `video/selfies/`

### Optimizar un prompt antes de guardar
```
/prompt optimizar una foto de una mujer sonriendo en el parque con luz natural
```
→ Genera 3 propuestas mejoradas:
   - **Propuesta A**: Enfocada en fotorrealismo (texturas DSLR, iluminación natural)
   - **Propuesta B**: Enfocada en dirección creativa (estilo, mood, color grading)
   - **Propuesta C**: Enfocada en consistencia técnica (estructura clara, parámetros)

Después de revisar las propuestas, puedes guardar la que prefieras:
```
/prompt [pega la propuesta que te gustó]
```

### Conversación normal
```
Pumas, ayúdame a entender cómo funciona esto
```
→ Modo conversación, no guarda nada

### Buscar
```
Busca mis prompts de espejo de espaldas
```
→ Muestra resultados filtrados
# prompts
