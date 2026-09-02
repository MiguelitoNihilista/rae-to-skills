# RAE to Skills

Convierte manuales y guías de la Real Academia Española en Claude Code Skills reutilizables.

## Propósito

Este proyecto automatiza la creación de skills de Claude basados en contenido normativo de la RAE. Permite procesar múltiples manuales (Gramática, Sintaxis, Estilo y Redacción) y generar skills por capítulo o por libro según sea más viable.

## Estructura

```
.
├── manuals/              
│   ├── 01_gramatica.md          # Manual de Gramática
│   ├── 02_sintaxis.md           # Manual de Sintaxis
│   ├── 03_estilo_redaccion.md   # Manual de Estilo y Redacción
│   └── [adicionales]
├── analysis/             
│   ├── 01_gramatica_analysis.md         # Análisis de estructura
│   ├── 02_sintaxis_analysis.md
│   └── 03_estilo_redaccion_analysis.md
├── skills/              
│   ├── gramatica/
│   │   ├── skill_001_clases_palabras.md
│   │   ├── skill_002_genero_numero.md
│   │   └── ...
│   ├── sintaxis/
│   │   ├── skill_001_oracion_simple.md
│   │   ├── skill_002_oracion_compleja.md
│   │   └── ...
│   └── estilo_redaccion/
│       ├── skill_001_claridad.md
│       ├── skill_002_precision.md
│       └── ...
├── reports/
│   ├── 01_gramatica_report.md      # Reporte de análisis
│   ├── 02_sintaxis_report.md
│   └── 03_estilo_redaccion_report.md
└── README.md
```

## Flujo de Trabajo

### Fase 1: Carga de Manuales

Coloca los manuales numerados en `/manuals/`:
```
01_gramatica.md
02_sintaxis.md
03_estilo_redaccion.md
```

### Fase 2: Análisis Automático

El agente:
1. **Lee cada manual** (01, 02, 03, etc.)
2. **Identifica estructura**: capítulos, secciones, reglas
3. **Extrae metadatos**: títulos, temas, conceptos clave
4. **Genera reporte de análisis** en `/analysis/`
5. **Decide granularidad**: ¿skill por capítulo o por libro?

### Fase 3: Decisión de Granularidad

El sistema evalúa:
- ¿Es el capítulo autónomo y comprensible?
- ¿Tiene múltiples sub-temas relacionados?
- ¿Necesita referencia a otros capítulos?

**Recomendación**:
- **Skills por capítulo**: Si cada capítulo es independiente
- **Skills por libro/tema**: Si los capítulos son muy pequeños o altamente interdependientes
- **Hybrid**: Combinación según sea necesario

### Fase 4: Generación de Skills

Para cada unidad (capítulo o libro):
1. Crear archivo en `/skills/[libro]/`
2. Usar plantilla (`.github/SKILL_TEMPLATE.md`)
3. Completar secciones con reglas, ejemplos, casos especiales
4. Validar autonomía del skill

### Fase 5: Documentación y Tracking

- Actualizar `SKILLS_INDEX.md` con todos los skills generados
- Crear reportes en `/reports/` con análisis de cada manual
- Documentar decisiones de granularidad

## Convención de Nombres

```
skill_[libro]_[numero]_[tema_corto].md

Ejemplos:
- skill_gramatica_001_clases_palabras.md
- skill_sintaxis_002_oracion_compleja.md
- skill_estilo_001_claridad_expresion.md
```

## Cómo Usar

1. **Coloca los manuales numerados** en `/manuals/`:
   ```
   01_gramatica.md
   02_sintaxis.md
   03_estilo_redaccion.md
   ```

2. **Solicita análisis**:
   ```
   "Analiza los manuales 01, 02, 03 y genera reporte de estructura"
   ```

3. **El agente genera**:
   - Reportes de análisis en `/analysis/`
   - Recomendaciones de granularidad
   - Skills en `/skills/[libro]/`

4. **Los skills están listos** para usar en Claude Code

## Skills Disponibles

(Se actualizará a medida que se generen skills)

### Gramática
- (Por completar)

### Sintaxis
- (Por completar)

### Estilo y Redacción
- (Por completar)
