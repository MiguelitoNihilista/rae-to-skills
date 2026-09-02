# Workflow: De Manuales RAE a Skills

## Visión General

Este workflow procesa múltiples manuales de la RAE (Gramática, Sintaxis, Estilo y Redacción) y genera skills inteligentemente, decidiendo la granularidad óptima (por capítulo o por libro).

---

## Fase 1: Preparación y Carga de Manuales

### Paso 1.1: Organizar Manuales

Coloca los manuales numerados en `/manuals/`:

```
manuals/
├── 01_gramatica.md              # Manual de Gramática
├── 02_sintaxis.md               # Manual de Sintaxis
├── 03_estilo_redaccion.md       # Manual de Estilo y Redacción
└── [adicionales si hay]
```

**Formato esperado:**
- Archivo en markdown o texto plano
- Incluir estructura clara: capítulos, secciones, subsecciones
- Puede incluir ejemplos y notas

### Paso 1.2: Solicitar Análisis

Comando:
```
"Analiza los manuales 01, 02, 03. 
Genera reportes de estructura y recomendaciones de granularidad."
```

---

## Fase 2: Análisis Inteligente de Manuales

El agente:

### 2.1 Lee cada manual
- Extrae título, autor, descripción
- Identifica número de capítulos
- Mapea estructura jerárquica

### 2.2 Analiza contenido
- **Autonomía**: ¿Cada capítulo es independiente o requiere contexto de otros?
- **Tamaño**: ¿Es el capítulo demasiado grande o pequeño para un skill?
- **Interdependencias**: ¿Hay referencias cruzadas entre capítulos?
- **Cohesión temática**: ¿Los temas son relacionados o dispersos?

### 2.3 Decide granularidad

**Criterios de decisión:**

| Situación | Recomendación | Ejemplo |
|-----------|---------------|---------|
| Capítulo autónomo, ~2-5 páginas | 1 skill por capítulo | "Clases de Palabras" → skill_gramatica_001 |
| Capítulo muy grande, múltiples subtemas | Dividir en skills por subtema | "Sintaxis de la Oración" → skill_sintaxis_001, 002, 003 |
| Capítulos pequeños y muy relacionados | 1 skill por grupo temático | "Uso de Tildes" + "Acentuación" → skill_gramatica_acentuacion |
| Libro completo coherente | 1 skill por libro | Si cada manual es breve y compacto |
| Temas transversales | Referencias cruzadas | Vincular skills con "Ver también:" |

### 2.4 Genera reportes

Crea archivos en `/analysis/`:

```
analysis/
├── 01_gramatica_analysis.md
├── 02_sintaxis_analysis.md
└── 03_estilo_redaccion_analysis.md
```

**Contenido de cada reporte:**
```markdown
# Análisis: [Nombre Manual]

## Metadata
- Título Original: [...]
- Número de Capítulos: [...]
- Páginas Aprox: [...]

## Estructura
- Capítulo 1: [Nombre] → Recomendación: [por capítulo/por tema/agrupado]
- Capítulo 2: [Nombre] → Recomendación: [...]
- ...

## Decisiones de Granularidad
- [Razonamiento para cada decisión]

## Interdependencias
- [Capítulos A y B están relacionados, vincularlos]
- [Capítulo C requiere contexto de...]

## Skills Recomendados
| Skill ID | Basado en | Contenido |
|----------|-----------|----------|
| skill_gramatica_001 | Cap 1 | [...] |
| ... | ... | ... |
```

---

## Fase 3: Generación de Skills

### 3.1 Crear estructura de directorios

```
skills/
├── gramatica/
├── sintaxis/
└── estilo_redaccion/
```

### 3.2 Usar plantilla estándar

Todos los skills usan: `.github/SKILL_TEMPLATE.md`

### 3.3 Generar skills

Para cada unidad decidida:

1. **Crear archivo** con nombre:
   ```
   skill_[libro]_[numero]_[tema].md
   
   Ejemplos:
   - skill_gramatica_001_clases_palabras.md
   - skill_sintaxis_002_oracion_compleja.md
   - skill_estilo_001_claridad_expresion.md
   ```

2. **Completar secciones:**
   - **Metadata**: skill_id, source, chapter, title
   - **Descripción**: Propósito del skill
   - **Reglas Normativas**: Cada regla con:
     - Definición
     - Ejemplos correctos
     - Ejemplos incorrectos
     - Casos especiales
   - **Aplicación Práctica**: Casos de uso reales
   - **Notas**: Referencias cruzadas, excepciones

### 3.4 Validar skills

- ¿Es autónomo y comprensible sin leer el manual?
- ¿Los ejemplos son claros?
- ¿Las reglas están bien formalizadas?
- ¿Están vinculados otros skills relacionados?

---

## Fase 4: Documentación y Tracking

### 4.1 Actualizar SKILLS_INDEX.md

```markdown
| ID | Título | Libro | Capítulo | Estado | Basado en | Fecha |
|----|--------|-------|----------|--------|-----------|-------|
| skill_gramatica_001 | Clases de Palabras | Gramática | 1 | ✅ | Cap 1 | 2026-09-02 |
```

### 4.2 Crear reportes finales

En `/reports/`:
```
01_gramatica_report.md
02_sintaxis_report.md
03_estilo_redaccion_report.md
```

Cada reporte incluye:
- Resumen de análisis
- Decisiones de granularidad tomadas
- Lista de skills generados
- Estadísticas

### 4.3 Documentar interdependencias

Crear archivo: `SKILLS_RELATIONSHIPS.md`

```markdown
## Relaciones entre Skills

- skill_gramatica_001 → skill_sintaxis_001 (La sintaxis depende de clases de palabras)
- skill_estilo_001 → skill_gramatica_002 (Claridad requiere conocer...)
- ...
```

---

## Fase 5: Integración en DSH

### 5.1 Descargar skills

```
Descargar:
- /skills/gramatica/
- /skills/sintaxis/
- /skills/estilo_redaccion/
```

### 5.2 Colocar en DSH

```
DSH/
└── .agent/
    └── skills/
        ├── manuals/              ← Colocar manuales originales
        │   ├── 01_gramatica.md
        │   ├── 02_sintaxis.md
        │   └── 03_estilo_redaccion.md
        ├── gramatica/            ← Skills de gramática
        ├── sintaxis/             ← Skills de sintaxis
        └── estilo_redaccion/     ← Skills de estilo
```

### 5.3 Usar en Claude Code

El agente en DSH tendrá acceso a todos los skills:
- Consulta reglas normativas
- Aplica análisis gramatical
- Mejora redacción

---

## Comandos Rápidos

```bash
# Analizar todos los manuales
"Analiza los manuales 01, 02, 03"

# Generar un skill específico
"Crea skill de [Capítulo X] del manual [Número]"

# Generar todos los skills
"Genera todos los skills recomendados"

# Revisar un skill
"Revisa y mejora skill_gramatica_001"

# Ver reportes
"Muestra el análisis de 01_gramatica"
```

---

## Checklist Final

- [ ] Manuales en `/manuals/` (01, 02, 03)
- [ ] Reportes de análisis en `/analysis/`
- [ ] Skills generados en `/skills/`
- [ ] SKILLS_INDEX.md actualizado
- [ ] SKILLS_RELATIONSHIPS.md creado
- [ ] Reportes finales en `/reports/`
- [ ] Skills descargados a DSH
- [ ] Manuales en DSH/.agent/skills/manuals/
- [ ] Skills en carpetas apropiadas en DSH
- [ ] Listo para usar en Claude Code
