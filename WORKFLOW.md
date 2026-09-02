# Workflow: De Manual RAE a Skills

## Fase 1: Preparación

1. **Proporciona el manual completo** (puede ser en texto, PDF transcrito, etc.)
2. **Define el manual** (ej: "Ortografía de la lengua española")
3. El sistema analiza la estructura y capítulos

## Fase 2: Análisis de Capítulos

El agente:
- Identifica títulos y estructura de capítulos
- Extrae las reglas normativas principales
- Agrupa contenido relacionado
- Prepara formato para skill

## Fase 3: Generación de Skills

Para cada capítulo:

1. **Crear archivo** en `/skills/` con nombre estándar:
   ```
   skill_XXX_[nombre_tema].md
   ```

2. **Usar plantilla** (`.github/SKILL_TEMPLATE.md`)

3. **Completar secciones**:
   - Metadata
   - Reglas normativas
   - Ejemplos
   - Casos especiales
   - Aplicación práctica

4. **Validar** que el skill sea autónomo y comprensible

## Fase 4: Almacenamiento y Documentación

- Guardar en repositorio
- Actualizar índice en `SKILLS_INDEX.md`
- Crear PR para revisión

## Ejemplo: Capítulo sobre Acentuación

**Entrada:**
```
Capítulo 3: Acentuación
3.1 Reglas de acentuación en palabras agudas...
3.2 Palabras llanas...
3.3 Palabras esdrújulas...
3.4 Diptongos e hiatos...
```

**Salida:**
- `skill_003_acentuacion.md` con todas las reglas formalizadas

---

## Comandos / Acciones

- **Para cargar manual**: Comparte el contenido conmigo
- **Para generar skill de un capítulo**: "Crea un skill del Capítulo X: [Nombre]"
- **Para revisar un skill**: "Revisa este skill y mejóralo"
- **Para generar todos los skills**: "Crea skills de todos los capítulos"
