# Skill — Análisis de Atributos de Calidad

Skill para agentes de IA que analiza sistemas a nivel de arquitectura de software siguiendo *Software Architecture in Practice, 4th Edition*.

## Funcionalidades

1. **Construir escenarios de calidad** a partir de un enunciado (6 partes SEI).
2. **Verificar y corregir** escenarios ya construidos.
3. **Construir el árbol de utilidad** con priorización.

## Modos de operación

| Modo | Descripción |
|---|---|
| 1 — Análisis | Enunciado → separar funcionalidad de calidad → identificar atributos → construir escenarios |
| 2 — Verificación | Escenario existente → verificar fidelidad a la bibliografía → detectar errores → corregir |
| 3 — Árbol de utilidad | Atributos → preocupaciones → escenarios priorizados (Importancia, Dificultad) |

## Estructura del repositorio

```
.opencode/skills/skill-analisis-atributos-calidad/
├── SKILL.md                    # Skill principal
└── references/
    └── general-scenarios.md    # General Scenarios de los 10 atributos
ejemplos-de-testeos.md          # Ejemplos testeados y mejoras que dispararon
```

Los análisis generados se guardan en la raíz del repositorio como `<sistema>.md` y `<sistema>.html`.

## ¿Por qué una sola skill y no tres separadas?

Se eligió implementar las tres funcionalidades (análisis, verificación y árbol de utilidad) como **modos de una misma skill** en lugar de tres skills independientes, porque comparten el mismo núcleo metodológico:

- **Mismas reglas de transparencia** (sección 3), estados de atributos (sección 4) y distinción funcional/calidad (sección 5).
- **El mismo General Scenario** de cada atributo (archivo `references/general-scenarios.md`) valida tanto la construcción (Modo 1) como la verificación (Modo 2) y el árbol (Modo 3).
- **Salida encadenada:** el árbol de utilidad (Modo 3) se alimenta directamente de los escenarios verificados en el Modo 2, y ambos del análisis del Modo 1; separarlos obligaría a duplicar estas reglas comunes y fragmentaría la trazabilidad enunciado → escenario → prioridad.

Una única skill mantiene estas reglas en un solo lugar y permite encadenar modos (p. ej. verificar y luego construir el árbol) sin redefinir criterios, lo que reduce la inconsistencia entre etapas. Se buscó modularidad **interna** (secciones y un archivo de referencia común) en lugar de dividir en skills, porque la clave del dominio es justamente que los tres modos aplican un mismo marco de fidelidad a la bibliografía.

## Evolución del proyecto

| # | Cambio |
|---|---|
| 1 | Creación de la skill con formato de 6 partes y reglas de transparencia |
| 2 | Adaptación para opencode: Modo 2 (verificación, E1–E10) y Modo 3 (árbol de utilidad) |
| 3 | Generación automática de archivos `.md` y `.html` como salida (sección 29.1) |
| 4 | Modularización: los General Scenarios se separaron a `references/general-scenarios.md` |
| 5 | Testeo y correción de skill mediante diversos ejemplos. |
| 6 | Documentación de los ejemplos de testeo en `ejemplos-de-testeos.md` (enunciado, errores detectados y mejoras disparadas por cada prueba). |