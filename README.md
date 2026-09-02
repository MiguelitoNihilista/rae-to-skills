# RAE to Skills

Convierte manuales y guías de la Real Academia Española en Claude Code Skills reutilizables.

## Propósito

Este proyecto automatiza la creación de skills de Claude basados en contenido normativo de la RAE. Cada capítulo de un manual de la RAE se transforma en un skill independiente que el agente puede usar para aplicar esas normas.

## Estructura

```
.
├── manuals/              # Manuales completos en formato de entrada
│   └── ortografia/      # Ej: Manual de Ortografía
├── skills/              # Skills generados (uno por capítulo)
│   ├── skill_001_acentuacion.md
│   ├── skill_002_puntuacion.md
│   └── ...
├── generator/           # Script para generar skills
│   └── rae_skill_generator.py
└── README.md
```

## Flujo de Trabajo

1. **Cargar Manual**: Proporcionar el manual completo al agente
2. **Análisis de Capítulos**: El agente identifica capítulos y estructura
3. **Generación de Skills**: Para cada capítulo, se crea:
   - Definición del skill (nombre, descripción, propósito)
   - Reglas y normas formalizadas
   - Ejemplos de uso
   - Casos de borde
4. **Almacenamiento**: Los skills se guardan en `/skills/`

## Cómo Usar

1. Coloca el manual en `/manuals/`
2. Ejecuta el generador o proporciona el contenido al agente
3. El agente creará un skill por capítulo
4. Los skills están listos para usar en Claude Code

## Skills Disponibles

(Se actualizará a medida que se generen skills)
