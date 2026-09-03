---
name: skill-analisis-atributos-calidad
description: "Analiza sistemas a nivel de arquitectura de software siguiendo Software Architecture in Practice (4th ed.) en tres modos: (1) construir Quality Attribute Scenarios a partir de un enunciado, (2) verificar y corregir escenarios ya armados, y (3) construir el árbol de utilidad. Úsala ante ejercicios sobre atributos de calidad, escenarios de calidad, verificación o corrección de escenarios, árbol de utilidad, utility tree, o análisis arquitectónico de enunciados."
---

# Skill — Análisis de Atributos de Calidad a Nivel de Arquitectura de Software

## Propósito

Esta skill define cómo analizar un enunciado de un sistema de software a nivel de **Arquitectura de Software**, para distinguir requerimientos funcionales de requisitos de atributos de calidad, identificar atributos confirmados y posibles, resolver ambigüedades y construir **Quality Attribute Scenarios** fieles a *Software Architecture in Practice, 4th Edition*.

La cadena de trazabilidad debe ser:

**ENUNCIADO → EVIDENCIA → ATRIBUTO → JUSTIFICACIÓN → GENERAL SCENARIO → CONCRETE SCENARIO**

No clasificar por palabras aisladas ni inventar información.

---

## Modos de operación

La skill tiene **tres modos**. Antes de responder, identificar cuál aplicar según lo que pida el usuario:

| Modo | Nombre | Cuándo se usa | Secciones |
|---|---|---|---|
| 1 | Análisis y construcción de escenarios | El usuario entrega un enunciado y pide analizarlo: separar funcionalidad de calidad, identificar atributos y construir sus escenarios. | 1 a 31 |
| 2 | Verificación y corrección de escenarios | El usuario entrega escenarios **ya armados** y pide verificarlos, detectar errores y corregirlos. | 33 |
| 3 | Árbol de utilidad | El usuario pide construir, completar o priorizar el **árbol de utilidad** de un sistema. | 34 |

- Los tres modos comparten las reglas de transparencia (sección 3), los estados de los atributos (sección 4), la distinción funcional/calidad (sección 5) y la fidelidad a los General Scenarios (secciones 11 a 14 y 25 a 26; los General Scenarios de los atributos, secciones 15 a 24, viven en el archivo externo `references/general-scenarios.md`).
- Si la petición mezcla modos, aplicarlos en secuencia y separar claramente la salida de cada uno, indicando en qué modo se está trabajando.
- Si no se puede determinar el modo solicitado, preguntar al usuario antes de proceder.

---

# 1. Nivel de abstracción

El análisis debe permanecer en el nivel de **Arquitectura de Software**.

Foco:

**Sistema → contexto → requerimientos → atributos de calidad → escenarios de calidad → implicancias arquitectónicas.**

Esta skill NO incluye:

- programación orientada a objetos;
- clases, herencia, encapsulamiento o polimorfismo como conceptos de programación;
- código;
- patrones de programación;
- detalles de implementación que no sean relevantes para la arquitectura.

---

# 2. Bibliografía principal

La fuente principal es **Software Architecture in Practice, 4th Edition**.

Para los escenarios utilizar especialmente la sección **3.3 — Specifying Quality Attribute Requirements: Quality Attribute Scenarios** y los General Scenarios de los capítulos 4 a 13.

Los capítulos de atributos de calidad son:

1. Availability
2. Deployability
3. Energy Efficiency
4. Integrability
5. Modifiability
6. Performance
7. Safety
8. Security
9. Testability
10. Usability

Por lo tanto, en esta edición se trabajan **10 atributos**, no 9.

La bibliografía debe prevalecer sobre intuiciones o conocimiento general cuando se esté resolviendo el ejercicio.

---

# 3. Regla de transparencia

Distinguir siempre:

### Dato del enunciado

Está expresamente dicho. Se presenta como dato conocido.

### Dato de la bibliografía

Proviene del libro. Debe conservarse su terminología y significado.

### Inferencia

Es algo deducido que no está expresado literalmente. Marcarlo siempre como:

**[INFERENCIA]**

Las inferencias deben evitarse en lo posible.

### Información ausente

Si el enunciado no permite determinar un dato, conservar explícitamente:

**No especificado**

Pero, cuando el contexto del sistema permita formular una posible interpretación razonable, agregar además:

**[INFERENCIA] Posible valor: ...**

La inferencia **no reemplaza** a "No especificado". Ambos deben aparecer cuando corresponda:

- **No especificado:** lo que realmente puede afirmarse a partir del enunciado.
- **[INFERENCIA] Posible valor:** una posible forma de completar ese campo, deducida del contexto, pero que no está explícitamente especificada.

La inferencia debe ser prudente, estar justificada y nunca presentarse como un requisito explícito.

---

# 4. Estados de los atributos

## CONFIRMADO

El enunciado proporciona evidencia suficiente para afirmar que existe una exigencia relacionada con ese atributo.

## POSIBLE

El enunciado proporciona una pista razonable, pero no suficiente para confirmarlo.

Siempre indicar:

- evidencia;
- por qué podría corresponder;
- qué faltaría para confirmarlo.

## Sin evidencia

Los atributos que no sean confirmados ni posibles **no se mencionan**. No hace falta enumerar todos los atributos descartados.

---

# 5. Separar requerimientos funcionales de atributos de calidad

## Requerimiento funcional

Pregunta:

> ¿Qué debe hacer el sistema?

Ejemplos: registrar, consultar, calcular, generar informes, realizar una operación, enviar una notificación.

## Atributo de calidad

Pregunta:

> ¿Qué propiedad o restricción de calidad debe cumplir el sistema al realizar esa funcionalidad?

Ejemplos: responder en determinado tiempo, permanecer disponible, resistir ataques, permitir modificaciones con determinado esfuerzo, facilitar integración o permitir que un usuario aprenda a utilizarlo.

Una misma funcionalidad puede estar relacionada con más de un atributo de calidad.

---

# 6. Analizar el contexto antes de clasificar

Primero comprender el sistema completo:

- propósito;
- contexto;
- actores;
- funcionalidades;
- restricciones;
- tiempos;
- cargas;
- fallas;
- cambios;
- integración;
- seguridad;
- uso;
- testing;
- deployment;
- energía.

Después identificar los atributos.

Una palabra aislada no determina automáticamente el atributo.

Ejemplo: "rápido" puede sugerir Performance, pero debe analizarse qué debe ser rápido y por qué. "Seguro" puede corresponder a Security o Safety según el significado del requisito.

---

# 7. Ambigüedades entre atributos

Un mismo fragmento del enunciado puede respaldar dos atributos.

Cuando ocurra:

1. mostrar ambos atributos razonables;
2. citar la evidencia de cada uno;
3. explicar la correspondencia de cada uno con la bibliografía;
4. comparar cuál es más específico para el contexto;
5. si ambos continúan siendo defendibles, mantener ambos y construir ambos escenarios.

No elegir automáticamente el atributo cuya palabra aparezca en el texto.

### Criterio de especificidad

Buscar el atributo que describa de forma más específica lo que el requisito intenta lograr en el sistema.

Esto no autoriza a inventar contexto: la especificidad debe surgir de la evidencia disponible.

---

# 8. Ejemplo de ambigüedad: tiempo vs. propósito

Enunciado hipotético:

> "El sistema debe comprobar la seguridad en menos de 2 segundos."

**Performance:** evidencia = "menos de 2 segundos". Hay una restricción temporal explícita.

**Security:** evidencia = "comprobar la seguridad". El objetivo de la operación está relacionado con seguridad.

Analizar ambas dimensiones. Si el objetivo de seguridad es lo específico y el tiempo es una restricción sobre esa operación, Security puede ser la interpretación más específica, mientras Performance representa la restricción temporal. Si no puede descartarse ninguna sin inferir, mantener ambas.

---

# 9. Modifiability e Integrability

El libro presenta Integrability como una forma de planificación de Modifiability. Por eso pueden aparecer juntas.

### Modifiability

Se centra en cambios del sistema y en el costo/esfuerzo/tiempo e impacto de realizarlos.

### Integrability

Se centra específicamente en integrar elementos/componentes y en la distancia entre elementos que deben interactuar.

Si el enunciado habla de integrar un componente, Integrability puede ser el atributo más específico. Pero no aplicar una regla automática: comparar siempre el foco concreto del requisito con las definiciones del libro.

Si ambos son defendibles, mostrar ambos.

---

# 10. "Afectar" no significa "ser requisito"

Que un atributo pueda verse afectado por una decisión no significa que el enunciado lo exija.

Por ejemplo, Security puede afectar Performance. Eso no convierte automáticamente Performance en requisito.

Distinguir:

> "Esto podría afectar Performance."

vs.

> "El enunciado exige Performance."

---

# 11. Quality Attribute Scenarios

Según la bibliografía, un escenario de atributo de calidad tiene seis partes:

1. **Stimulus Source**
2. **Stimulus**
3. **Artifact**
4. **Environment**
5. **Response**
6. **Response Measure**

### Stimulus Source

Quién o qué genera el estímulo.

### Stimulus

El evento que llega al sistema o al proyecto.

### Artifact

El elemento o parte afectada por el estímulo.

### Environment

Las condiciones o estado en que ocurre el estímulo.

### Response

La respuesta que debe producirse.

### Response Measure

La medida que permite comprobar si la respuesta satisface el requisito.

---

# 12. General Scenario y Concrete Scenario

### General Scenario

Es independiente del sistema particular y describe el atributo en términos generales.

### Concrete Scenario

Es una instancia concreta del General Scenario para el sistema analizado.

Proceso:

**General Scenario del libro → particularización al sistema → Concrete Scenario**

No alterar el significado de las categorías del General Scenario.

---

# 13. Convención para personalizar escenarios

Aplicar esta convención **consistentemente en las seis partes**.

### Información concreta del sistema

Escribirla sin paréntesis.

### Opción o valor bibliográfico correspondiente

Escribirlo entre paréntesis.

**Importante:** lo que aparece entre paréntesis **NO es el nombre de la parte del escenario**. Es la **opción o valor que la bibliografía propone para completar esa parte del General Scenario**.

Las seis partes siguen siendo los encabezados:

- Stimulus Source
- Stimulus
- Artifact
- Environment
- Response
- Response Measure

Dentro de cada parte se debe escribir:

> **dato concreto del sistema (opción/valor bibliográfico correspondiente)**

Ejemplo:

> **Stimulus Source:** Persona mayor (**end user**)

"Persona mayor" es el dato específico del sistema y "end user" es la opción/valor bibliográfico que corresponde a **Stimulus Source**.

Otro ejemplo:

> **Artifact:** Módulo de autenticación (**component**)

"Módulo de autenticación" es el dato específico del sistema y "component" es la opción/valor bibliográfico correspondiente a **Artifact**.

No escribir:

> **Módulo de autenticación (artifact)**

si "artifact" solamente identifica cuál de las seis partes se está completando. En ese caso, **Artifact** es el encabezado y dentro de los paréntesis debe aparecer la opción/valor que el libro propone para esa parte.

Esta convención se aplica consistentemente a las seis partes.

---

# 14. Regla de fidelidad a las tablas

Para construir cada escenario:

1. consultar el General Scenario del atributo en el libro;
2. mantener sus seis partes;
3. conservar el significado de sus categorías;
4. utilizar las posibles opciones del libro como guía;
5. particularizar únicamente con información del enunciado;
6. si falta información, escribir "No especificado" y, cuando el contexto permita una posible interpretación útil, agregar también **[INFERENCIA] Posible valor: ...** sin reemplazar el "No especificado";
7. no inventar métricas ni condiciones.

La personalización puede hacer el escenario más claro y contextualizado, pero nunca debe reemplazar ni deformar la estructura de la bibliografía.

---

# 15 a 24. General Scenarios de los atributos (archivo externo)

Los **General Scenarios** de los diez atributos de calidad (Availability, Deployability, Energy Efficiency, Integrability, Modifiability, Performance, Safety, Security, Testability, Usability) —con sus seis partes y las opciones/valores bibliográficos de cada una— se encuentran en el archivo de referencia:

**`references/general-scenarios.md`**

**IMPORTANTE:** este archivo se encuentra junto a la skill y **no se inyecta automáticamente**. Para resolver cualquier ejercicio (Modos 1, 2 o 3) debes **leer `references/general-scenarios.md`** y usarlo como **única referencia de validación** de los General Scenarios.

Cada sección del archivo reproduce el General Scenario de un atributo con sus seis partes:

- Availability → sección 15
- Deployability → sección 16
- Energy Efficiency → sección 17
- Integrability → sección 18
- Modifiability → sección 19
- Performance → sección 20
- Safety → sección 21
- Security → sección 22
- Testability → sección 23
- Usability → sección 24

A lo largo de esta skill, toda mención a "secciones 15 a 24" o "el General Scenario del atributo" remite a dicho archivo.

---

# 25. Cómo construir un Concrete Quality Attribute Scenario

Para cada atributo:

1. localizar su General Scenario (secciones 15 a 24 del archivo `references/general-scenarios.md`);
2. mantener las seis partes;
3. extraer del enunciado los datos explícitos;
4. personalizar cada parte con la convención **dato concreto (opción/valor bibliográfico correspondiente)**;
5. si falta información, mantener **No especificado** y, cuando sea útil y razonable, agregar debajo **[INFERENCIA] Posible valor: ...**;
6. marcar como **[INFERENCIA]** cualquier conclusión no explícita;
7. verificar que Response Measure sea comprobable;
8. revisar que el escenario siga siendo fiel al General Scenario.

---

# 26. Response Measure

Nunca presentar una inferencia como si fuera un valor explícito del enunciado.

Si el enunciado dice:

> "rápidamente"

mantener:

> **No especificado**

y, si el contexto permite proponer una posible interpretación razonable:

> **[INFERENCIA] Posible valor: un tiempo de respuesta reducido / una respuesta dentro de un intervalo breve.**

La inferencia debe dejar claro que el enunciado no fija una medida concreta.

No convertir arbitrariamente "rápidamente" en "menos de 2 segundos".

Si el enunciado dice:

> "menos de 2 segundos"

sí utilizar:

> **menos de 2 segundos**

como dato explícito.

Si la bibliografía indica una clase de medida pero el enunciado no da un valor:

> **No especificado (opción/medida bibliográfica correspondiente)**

y, cuando el contexto permita una interpretación razonable:

> **[INFERENCIA] Posible valor: ...**

Nunca presentar esa inferencia como si fuera un requisito explícito.

---

## 26.1 Dato explícito, reformulación válida y métrica inventada

**No toda paráfrasis de un requisito es una inferencia problemática ni una métrica inventada.** Ante el fragmento de un enunciado, distinguir tres niveles:

- **Dato explícito del enunciado:** lo que el texto declara literalmente, sin agregados.
  - Ejemplo: "desplegarse **sin afectar** a los estudiantes".
- **Reformulación válida:** una paráfrasis que conserva el sentido del dato explícito sin introducir un valor ni condiciones que el enunciado no declara. Puede usarse como Response o como descripción de la medida sin marcarla como invención, aclarando que es una reformulación del requisito.
  - Ejemplo: "sin interrupción de los pagos en curso" reformula "sin afectar a los estudiantes que están realizando pagos".
  - La reformulación no equivale a fijar un umbral: no convierte "sin afectar" en "cero interrupciones" entendido como 0 segundos.
- **Métrica cuantitativa inventada:** un valor, porcentaje o umbral numérico que el enunciado no declara. Debe eliminarse o marcarse **[INFERENCIA]** y, salvo que el contexto aporte base, evitarse.
  - Ejemplo: "0 segundos de interrupción", "100% de deployments sin interrupción", "100% de los accesos rechazados".

### Criterio

- Si el enunciado da un valor concreto → usarlo como dato explícito.
- Si el enunciado da una condición observable pero no numérica (p. ej. "sin afectar a los estudiantes") → usar esa condición como Response y, en la medida, describirla sin inventar un número ("No especificado" + posibles **[INFERENCIA]** si son útiles). Una reformulación textual es aceptable; un valor numérico inventado no lo es.
- Si el enunciado usa un término vago ("rápidamente", "seguro", "disponible") → "No especificado" + **[INFERENCIA]** sin reemplazarlo por un número.

---

# 27. Justificación de atributos

## CONFIRMADO

**Atributo:** ...

**Estado:** CONFIRMADO

**Evidencia del enunciado:** "..."

**Correspondencia bibliográfica:** ...

**Justificación:** ...

## POSIBLE

**Atributo:** ...

**Estado:** POSIBLE

**Evidencia:** "..."

**Por qué podría corresponder:** ...

**Qué falta para confirmarlo:** ...

---

# 28. Formato para ambigüedades

| Aspecto | Atributo A | Atributo B |
|---|---|---|
| Evidencia del enunciado | ... | ... |
| Qué representa | ... | ... |
| Correspondencia bibliográfica | ... | ... |
| Especificidad contextual | ... | ... |
| Estado | ... | ... |

Después:

### Conclusión

Explicar cuál es más específico, por qué y si la otra alternativa sigue siendo válida.

Si ambos siguen siendo defendibles, construir ambos escenarios.

---

# 29. Formato de salida recomendado

# Análisis del sistema

## 1. Requerimientos funcionales

- RF1 — ...
- RF2 — ...

## 2. Atributos de calidad confirmados

| Atributo | Evidencia del enunciado | Justificación |
|---|---|---|
| ... | "..." | ... |

## 3. Atributos de calidad posibles

| Atributo | Evidencia | Por qué podría corresponder | Qué falta para confirmarlo |
|---|---|---|---|
| ... | "..." | ... | ... |

## 4. Ambigüedades

Analizar los fragmentos que puedan corresponder a más de un atributo.

## 5. Escenarios

### Atributo: ...

**Estado:** CONFIRMADO / POSIBLE

| Parte | Escenario concreto |
|---|---|
| Stimulus Source | ... (**opción/valor bibliográfico correspondiente**) |
| Stimulus | ... (**opción/valor bibliográfico correspondiente**) |
| Environment | ... (**opción/valor bibliográfico correspondiente**) |
| Artifact | ... (**opción/valor bibliográfico correspondiente**) |
| Response | ... (**opción/valor bibliográfico correspondiente**) |
| Response Measure | ... (**opción/valor bibliográfico correspondiente**) |

**Justificación:** ...

---

## 29.1. Entrega de archivos generados

Además de mostrar la respuesta en el chat, el agente debe generar automáticamente **dos archivos** con el análisis completo:

1. **`<nombre-del-sistema>.md`** — Archivo markdown con todo el análisis (requerimientos, atributos, ambigüedades, escenarios, checklist). Este archivo sirve como fuente editable.

2. **`<nombre-del-sistema>.html`** — Archivo HTML autónomo con CSS embebido que renderiza las tablas con bordes, colores alternados en filas, encabezados con fondo oscuro y tipografía legible. Se genera convirtiendo el `.md` con la librería `markdown` de Python, incluyendo la extensión `tables` y `fenced_code`, y envolviendo el resultado en un `<body>` con estilos CSS inline.

### Plantilla CSS mínima para el HTML

```css
body { font-family: 'Segoe UI', sans-serif; max-width: 1100px; margin: 40px auto; padding: 0 30px; line-height: 1.6; color: #222; background: #fafafa; }
h1 { color: #1a1a2e; border-bottom: 3px solid #16213e; padding-bottom: 10px; }
h2 { color: #16213e; border-bottom: 2px solid #0f3460; padding-bottom: 6px; margin-top: 35px; }
h3 { color: #0f3460; margin-top: 25px; }
table { width: 100%; border-collapse: collapse; margin: 15px 0; background: #fff; box-shadow: 0 1px 4px rgba(0,0,0,0.08); font-size: 0.92em; }
thead tr { background: #16213e; color: #fff; }
th { padding: 10px 12px; text-align: left; font-weight: 600; border: 1px solid #16213e; }
td { padding: 9px 12px; border: 1px solid #ccc; vertical-align: top; }
tbody tr:nth-child(even) { background: #f0f4f8; }
tbody tr:hover { background: #e2eaf3; }
```

### Procedimiento de generación

1. Escribir el análisis completo en formato markdown y guardarlo como `<nombre-del-sistema>.md`.
2. Leer el `.md` generado y convertirlo a HTML usando `markdown.markdown()` con `extensions=["tables", "fenced_code"]`.
3. Envolver el HTML resultante en una plantilla completa (`<!DOCTYPE html>`, `<head>` con charset y CSS, `<body>`).
4. Guardar como `<nombre-del-sistema>.html`.
5. Informar al usuario la ubicación de ambos archivos.

### Convención de nombres

El nombre del archivo debe ser descriptivo y en minúsculas con guiones, por ejemplo:

- `escenarios-atributos-calidad-monopatines.md`
- `escenarios-atributos-calidad-monopatines.html`

---

# 30. Checklist final

### Sistema

- [ ] Comprendí el contexto.
- [ ] Identifiqué funcionalidades.
- [ ] Separé funcionalidad de calidad.

### Atributos

- [ ] Cada confirmado tiene evidencia.
- [ ] Cada posible está marcado como POSIBLE.
- [ ] Expliqué por qué podría corresponder.
- [ ] No incluí atributos sin evidencia.
- [ ] Consideré ambigüedades.
- [ ] Busqué el atributo más específico.

### Transparencia

- [ ] Distinguí datos del enunciado y bibliografía.
- [ ] Marqué inferencias como **[INFERENCIA]**.
- [ ] Evité inferencias innecesarias.
- [ ] Marqué datos faltantes como No especificado.
- [ ] Cuando fue útil, agregué una posible interpretación marcada como **[INFERENCIA]**, sin reemplazar "No especificado".
- [ ] No inventé datos.

### Escenarios

- [ ] Usé las seis partes.
- [ ] Seguí el General Scenario del libro.
- [ ] Conservé el significado de las categorías.
- [ ] Personalicé al sistema.
- [ ] Datos concretos fuera de paréntesis.
- [ ] Entre paréntesis puse la opción/valor bibliográfico correspondiente a la parte, no el nombre de la parte.
- [ ] Response Measure verificable.
- [ ] No inventé métricas.
- [ ] Response Measure tiene trazabilidad directa con el enunciado: no se sustituyeron términos vagos (p. ej. "rápidamente") por valores concretos inventados (p. ej. "menos de 2 segundos"), y se distinguió dato explícito, reformulación válida y métrica cuantitativa inventada (sección 26.1).

### Ambigüedad

- [ ] Verifiqué explícitamente si el enunciado respalda más de un atributo (no lo di por resuelto).
- [ ] Mostré ambos atributos cuando ambos son defendibles.
- [ ] Justifiqué cada uno.
- [ ] Comparé cuál es más específico.
- [ ] Construí ambos escenarios si ninguno podía descartarse.
- [ ] En Modo 2, registré el análisis de ambigüedad en la sección 1.1 y señalé E9 si correspondía (una ambigüedad ignorada es error aunque las seis partes estén bien).

### Entrega de archivos (sección 29.1)

- [ ] Generé el archivo `<nombre-del-sistema>.md` con el análisis completo.
- [ ] Generé el archivo `<nombre-del-sistema>.html` con tablas renderizadas.
- [ ] El `.html` incluye CSS embebido y es autónomo (abre correctamente en el navegador).
- [ ] Informé al usuario la ubicación de ambos archivos.

### Modo 3 — Árbol de utilidad

- [ ] Cada atributo se verificó contra su General Scenario (paso 4 del procedimiento de la sección 34).
- [ ] Cada parte del escenario tiene trazabilidad directa con el enunciado o con categorías del GS (sección 34.2).
- [ ] No inventé artifacts, environments, sources ni responses que el enunciado no describe.
- [ ] No sobre-adapté el Artifact: en Availability no cambié "sistema/parte del sistema" al pago solo porque el estímulo lo afecta; el pago describe la Response, no el Artifact (sección 34.2, regla 3).
- [ ] No agregué contextos hipotéticos (peak load, temporadas, etc.) que el enunciado no menciona.
- [ ] No inventé detalles técnicos (tecnologías, patrones, mecanismos) para justificar prioridades.
- [ ] No usé vocabulario del General Scenario (fault, attack, overloaded operation, production, etc.) como contenido concreto del escenario. Lo que el enunciado no describe se marca "No especificado" (sección 34.2, regla 7).
- [ ] La dificultad de cada hoja es **No especificado** salvo que el enunciado proporcione evidencia explícita de complejidad técnica. No asigné H/M/L basándome en conocimiento general sobre atributos (sección 34.3).
- [ ] La importancia de cada hoja se apoya en evidencia **explícita de criticidad o impacto** del enunciado; **no** asigné H por el solo hecho de que el requisito use "debe". Cuando el enunciado no permite determinarla, escribí **No especificado** (sección 34.3).
- [ ] La justificación de prioridades tiene exactamente dos líneas: una para importancia, una para dificultad.
- [ ] Cada preocupación tiene evidencia del enunciado; no forcé subdivisiones innecesarias.
- [ ] "No especificado" aparece cuando el enunciado no proporciona un dato, sin ser reemplazado por inferencias.

---

# 31. Regla de oro

> **No inventar. No sobreinterpretar. No clasificar por palabras aisladas. Analizar en contexto. Mostrar las alternativas razonables. Priorizar el atributo más específico cuando la evidencia lo permita. Mantener las alternativas cuando continúen siendo defendibles. Seguir la estructura del General Scenario de la bibliografía. Marcar toda inferencia. Y conservar siempre la trazabilidad entre el enunciado, la bibliografía y el escenario.**

> **La bibliografía aporta la estructura del General Scenario (las seis partes y sus opciones), pero NO puede aportar valores concretos del escenario que el enunciado no proporciona. Lo que el enunciado no dice, se marca "No especificado". Lo que se infiere, se marca [INFERENCIA]. Lo que se inventa, se elimina.**

# 32. Distinciones y comparaciones entre atributos de calidad

Esta sección agrega distinciones útiles para resolver casos grises entre atributos. **No modifica la definición ni el procedimiento de las secciones anteriores**. Su función es servir como guía comparativa cuando dos conceptos puedan confundirse.

Cuando una distinción provenga del libro, indicarlo como **[BIBLIOGRAFÍA]**. Cuando corresponda específicamente a una explicación, criterio o convención de la cátedra y no a un atributo de la "A list" del libro, indicarlo como **[CÁTEDRA / CLASE]**. Si una explicación es una interpretación nuestra, marcarla como **[INFERENCIA]**.

---

## 32.1 Integrability vs. Modifiability

**[BIBLIOGRAFÍA]** El libro trata **Integrability** y **Modifiability** como atributos distintos dentro de su "A list", y presenta Integrability específicamente alrededor de la integración de elementos. La relación entre ambos debe entenderse como una relación de alcance: la integración es un tipo particular de cambio/preocupación arquitectónica, pero el requisito puede estar expresando específicamente integración.

### Modifiability

Pregunta guía:

> **¿Qué tan fácil es realizar un cambio en el sistema y cuál es el costo/impacto de ese cambio?**

Se centra en cambios como:

- agregar funcionalidad;
- eliminar funcionalidad;
- modificar funcionalidad;
- cambiar una tecnología o plataforma;
- corregir defectos;
- realizar otros cambios sobre artifacts del sistema.

### Integrability

Pregunta guía:

> **¿Qué tan fácil es integrar elementos/componentes para que trabajen juntos?**

El foco está específicamente en la incorporación/integración de elementos y en lograr que esos elementos interactúen correctamente.

### Regla práctica

Si el enunciado dice simplemente:

> "el sistema debe poder modificarse fácilmente"

→ **Modifiability**.

Si dice:

> "debe poder integrarse un nuevo componente/sistema/elemento"

→ **Integrability** puede ser el atributo más específico.

Si el cambio consiste precisamente en integrar algo, pueden ser defendibles ambos:

- **Modifiability** → preocupación general por el cambio.
- **Integrability** → preocupación específica por la integración.

En ese caso, mostrar ambos, justificar ambos y explicar cuál es más específico para el enunciado.

---

## 32.2 Portability vs. Interoperability

### Estado respecto de la bibliografía

**[BIBLIOGRAFÍA]** En la 4.ª edición, **Portability** e **Interoperability** no forman parte de los diez atributos de la "A list" desarrollados individualmente en los capítulos 4–13. El libro las trata dentro de su discusión de **otras listas/modelos de atributos de calidad** en el capítulo 14. En particular, al presentar ISO/IEC 25010, menciona Portability e Interoperability como características/subcaracterísticas de ese modelo.

Por lo tanto, si la cátedra utiliza Portability e Interoperability como atributos para analizar ejercicios, deben distinguirse de los diez atributos principales de la skill.

**[CÁTEDRA / CLASE]** Si estos conceptos fueron presentados explícitamente por la cátedra como categorías para clasificar requisitos, utilizarlos como categorías de análisis, pero mantener esta aclaración de procedencia.

### Portability

**[BIBLIOGRAFÍA]** El libro reproduce la definición de ISO/IEC 25010 según la cual Portability se refiere al grado en que un sistema, producto o componente puede ser transferido entre distintos entornos de hardware, software u otros entornos operativos/de uso.

Pregunta guía:

> **¿El sistema puede trasladarse/adaptarse para funcionar en otro entorno?**

Ejemplos de pistas:

- funcionar en distintos sistemas operativos;
- trasladarse a otra plataforma;
- funcionar en diferentes entornos de operación;
- poder mover un componente/sistema de un entorno a otro con el esfuerzo requerido.

**[INFERENCIA]** Decir simplemente "que el sistema se pueda usar en otro lugar" puede ser demasiado ambiguo: hay que comprobar que el requisito realmente implique transferencia entre entornos y no simplemente otro tipo de reutilización o configuración.

### Interoperability

**[BIBLIOGRAFÍA]** En ISO/IEC 25010, que el libro presenta en el capítulo 14, Interoperability aparece como una subcaracterística de **Compatibility**: se relaciona con la capacidad de sistemas/productos para intercambiar información y utilizar esa información intercambiada.

Pregunta guía:

> **¿El sistema necesita intercambiar información o colaborar con otro sistema/producto?**

Por lo tanto, **no definir Interoperability como "que el mismo sistema tenga distintos usos"**. Ese ejemplo de las distintas pólizas para dólares/pesos, por sí solo, no demuestra interoperabilidad.

**[INFERENCIA]** Si un sistema bancario puede manejar distintos tipos de pólizas porque está diseñado para admitir configuraciones o variaciones de negocio, eso podría apuntar a otra preocupación —por ejemplo Modifiability, configurabilidad u otra cualidad—, pero no alcanza por sí solo para afirmar Interoperability.

### Runtime vs. desarrollo: distinción de la cátedra

**[CÁTEDRA / CLASE]** Para el análisis de los ejercicios, la cátedra distingue además el **momento en el que aparece principalmente la preocupación**:

- **Integrability:** se considera principalmente una preocupación de **desarrollo/integración**, relacionada con incorporar e integrar elementos del sistema para que trabajen correctamente juntos.
- **Interoperability:** se considera principalmente una preocupación de **runtime/ejecución**, relacionada con que sistemas o componentes puedan **intercambiar información y utilizar la información intercambiada** durante su operación, por ejemplo mediante una red o una interacción entre sistemas.

Esta distinción es una **regla de análisis dada por la cátedra**, no debe presentarse como si fuera una definición literal adicional del libro.

**[BIBLIOGRAFÍA]** El libro permite que el escenario de Integrability tenga como Environment, según el caso, **development, integration, deployment o runtime**. Por lo tanto, no es correcto afirmar que Integrability *solamente* ocurre en desarrollo. La formulación más fiel es:

> **Integrability suele analizarse desde el desarrollo/integración, según la cátedra, pero el libro permite también escenarios de integración en runtime.**

En cambio, para **Interoperability**, la definición bibliográfica pone el foco en la capacidad de sistemas/productos para intercambiar información y utilizar la información intercambiada. Por eso, cuando el enunciado describe comunicación o intercambio de datos entre sistemas durante la operación, **Interoperability** es la opción específica.

### Regla práctica de la cátedra

Ante un enunciado que hable de integración o interacción:

- Si el foco está en **incorporar/integrar un elemento para que forme parte del sistema**, pensar primero en **Integrability**.
- Si el foco está en **sistemas que se encuentran en ejecución e intercambian información**, pensar primero en **Interoperability**.
- Si el enunciado solamente habla de que un sistema pueda funcionar en otro entorno, pensar en **Portability**, no en Interoperability.
- Si la situación permite defender más de un atributo, aplicar siempre la regla general de la skill: mostrar las alternativas, justificar cada una y determinar cuál es más específica.

**[INFERENCIA]** La oposición "desarrollo vs. runtime" puede servir como pista muy útil para los ejercicios de la cátedra, pero no debe utilizarse como criterio absoluto para descartar Integrability: el propio libro contempla **runtime** como uno de sus posibles entornos.

### Diferencia rápida

| | Portability | Interoperability |
|---|---|---|
| Pregunta central | ¿Puedo trasladar el sistema a otro entorno? | ¿Puede colaborar/intercambiar información con otro sistema? |
| Foco | Entorno de operación | Interacción entre sistemas/productos |
| Ejemplo | Ejecutar el sistema en distintos SO/plataformas | Intercambiar información correctamente con otro sistema |
| Procedencia en la 4.ª edición | [BIBLIOGRAFÍA — ISO/IEC 25010 presentado en cap. 14] | [BIBLIOGRAFÍA — ISO/IEC 25010 presentado en cap. 14] |

**No confundir:**

> **Portability ≠ distintos usos del sistema**

> **Interoperability ≠ simplemente tener distintas funcionalidades o configuraciones**

---

## 32.3 Safety vs. Security

**[BIBLIOGRAFÍA]** La 4.ª edición trata Safety y Security como atributos distintos y les dedica capítulos separados, con sus propios General Scenarios.

### Safety

Pregunta guía:

> **¿El comportamiento, fallo u operación del sistema puede llevar a un estado inseguro o causar daño, y qué debe hacer el sistema para evitarlo o recuperarse?**

El foco está en prevenir estados inseguros, recuperarse de ellos o mantener una operación segura/degradada. La skill ya debe utilizar para Safety las categorías del General Scenario del libro, como estados inseguros, operación degradada, fail-safe, backup, etc.

**Importante:** no reducir Safety a "cuidar plata o activos".

**[INFERENCIA / ACLARACIÓN]** Una pérdida económica puede ser consecuencia de un estado inseguro en determinados sistemas, pero la mera existencia de dinero o activos valiosos no convierte un requisito en Safety. Hay que analizar qué tipo de daño o estado inseguro se está intentando evitar.

### Security

Pregunta guía:

> **¿El sistema debe proteger información, servicios o recursos frente a accesos, acciones o ataques no autorizados?**

El foco incluye, según el escenario, propiedades como:

- confidentiality;
- integrity;
- availability;
- detección y respuesta ante ataques;
- protección frente a accesos o modificaciones no autorizadas.

### Diferencia rápida

| | Safety | Security |
|---|---|---|
| Pregunta central | ¿Cómo evitar estados inseguros/daños derivados del comportamiento o fallos del sistema? | ¿Cómo proteger el sistema, sus datos, servicios o recursos frente a acciones no autorizadas/ataques? |
| Amenaza típica | Fallo, dato incorrecto, timing incorrecto, comportamiento peligroso | Ataque, acceso no autorizado, modificación/captura de datos |
| Foco | Operación segura | Protección frente a amenazas/adversarios |
| Procedencia | [BIBLIOGRAFÍA — cap. 10] | [BIBLIOGRAFÍA — cap. 11] |

### Regla práctica

Si el enunciado habla de:

- evitar que un fallo produzca un estado peligroso;
- pasar a un estado seguro;
- fail-safe;
- proteger personas/entorno frente a consecuencias peligrosas del comportamiento del sistema;

→ analizar **Safety**.

Si habla de:

- ataques;
- hackers;
- accesos no autorizados;
- robo/captura de información;
- modificación maliciosa;
- confidencialidad, integridad o protección de recursos;

→ analizar **Security**.

Si el lenguaje del enunciado dice simplemente "seguridad", **no decidir por la palabra aislada**. Aplicar la regla general de contexto de esta skill.

---

## 32.4 Regla general para usar estas comparaciones

Estas distinciones no reemplazan el análisis del enunciado.

Ante un caso ambiguo:

1. identificar la evidencia textual;
2. identificar qué preocupación expresa realmente;
3. comparar con las definiciones bibliográficas/categorizaciones de la cátedra;
4. determinar si uno de los atributos es más específico;
5. si ambos siguen siendo defendibles, mostrar ambos;
6. si una distinción proviene de clase y no del libro, marcarla como **[CÁTEDRA / CLASE]**;
7. si se necesita completar información no explícita, conservar **No especificado** y agregar la posible interpretación como **[INFERENCIA]**.

La comparación debe servir para **afinar la clasificación**, no para forzar el enunciado a contener un atributo que no está realmente respaldado.

---

# 33. Modo 2 — Verificación y corrección de escenarios

## Objetivo

Dado un Quality Attribute Scenario **ya construido**, verificar si es fiel a la bibliografía y al enunciado, señalar los errores y devolver el escenario **corregido y completo**.

## Procedimiento

1. **Identificar el atributo** al que el escenario pretende corresponder. Si el escenario no lo declara, inferirlo de su contenido y marcarlo **[INFERENCIA]**.
2. **Recuperar el General Scenario** de ese atributo (secciones 15 a 24 del archivo `references/general-scenarios.md`) y usarlo como única referencia de validación.
3. **Verificar la presencia de las seis partes** en orden y con su nombre correcto (sección 11).
4. **Verificar cada parte contra el General Scenario** del atributo: la fuente, el estímulo, el artifact, el environment, la response y la response measure deben ser instancias válidas de las categorías del libro (secciones 15 a 24 de `references/general-scenarios.md`).
5. **Verificar la convención de paréntesis** (sección 13): entre paréntesis debe ir la **opción o valor bibliográfico** de esa parte, y **nunca** el nombre de la parte.
6. **Verificar la transparencia** (secciones 3 y 26): toda inferencia marcada **[INFERENCIA]**, todo dato ausente como **No especificado** (con la posible interpretación si corresponde, sin reemplazar el "No especificado"), y ninguna inferencia presentada como requisito.
7. **Verificar la ambigüedad de atributos** (secciones 7, 8 y 32): reanalizar el enunciado para detectar si el fragmento que dio origen al escenario respalda **más de un atributo** de calidad. Si existe una alternativa defendible, comprobar que el escenario la trate correctamente (p. ej. que el atributo elegido sea el más específico, que se justifique la decisión, y que si la alternativa sigue siendo válida se ofrezca —o se justifique por qué no— un escenario para ella). No dar la ambigüedad por resuelta ni ignorarla; si el escenario no la trata, es un error E9.
8. **Emitir el veredicto** y la lista de errores encontrados.
9. **Reescribir el escenario completo corregido** en el formato estándar de la sección 29.

## Tipos de error

| Código | Error | Criterio |
|---|---|---|
| E1 | Faltan partes | Deben aparecer las seis partes con sus nombres correctos (sección 11). |
| E2 | Nombre de parte usado dentro del paréntesis | Entre paréntesis va la opción/valor bibliográfico (p. ej. "end user", "component"), no el nombre de la parte (sección 13). |
| E3 | Opción bibliográfica que no corresponde al GS del atributo | La opción/valor entre paréntesis debe estar contemplada en el General Scenario del atributo (secciones 15 a 24 de `references/general-scenarios.md`). |
| E4 | Invención de datos (métrica, valor, condición, fuente) | Sólo se admite información del enunciado o de la bibliografía; lo demás es inferencia y debe marcarse como tal (sección 3). |
| E5 | Inferencia no marcada | Toda conclusión no explícita se marca **[INFERENCIA]** (sección 3). |
| E6 | Falta "No especificado" | Si el enunciado no determina el dato, se conserva "No especificado", con la posible interpretación si corresponde (secciones 3 y 26). |
| E7 | Deformación del General Scenario | El escenario debe ser una instancia fiel del GS particularizado al sistema, sin alterar el significado de sus categorías (secciones 12 y 14). |
| E8 | Response Measure no comprobable, inventada o sin trazabilidad con el enunciado | Debe ser verificable y derivarse del enunciado. Si el enunciado usa un término vago (p. ej. "rápidamente", "débilmente", "con alta disponibilidad"), **no sustituirlo por un valor numérico concreto** sin marca de inferencia. Sin valor del enunciado usar "No especificado" + posible **[INFERENCIA]** (secciones 26, 26.1 y 3). **No es E8** cuando se reformula con fidelidad un requisito observable (ver sección 26.1): reformular "sin afectar a los estudiantes" como "desplegar sin interrumpir los pagos en curso" es válido; inventar "0 segundos de interrupción" o "100% de deployments sin interrupción" es E8. |
| E9 | Ambigüedad no detectada o mal resuelta | Debe comprobarse si el fragmento del enunciado respalda más de un atributo. Si una alternativa es defendible (secciones 7 y 8), el escenario debe: elegir el atributo más específico y justificarlo, conservar la alternativa si sigue siendo válida (construyendo su escenario o explicando su descarte), y no presentar la ambigüedad como inexistente. El silencio sobre una ambigüedad relevante es también E9 (secciones 7, 8, 32 y procedimiento paso 7 del Modo 2). |
| E10 | Atributo mal identificado | Comparar el foco del requisito con la definición del atributo y evaluar alternativas más específicas (secciones 7 a 9 y 32). |

## Formato de salida del Modo 2

### 1. Veredicto

El escenario es **CORRECTO / PARCIALMENTE CORRECTO / INCORRECTO** (elegir uno y justificar en una línea).

### 1.1. Análisis de ambigüedad

Conducta obligatoria: comprobar si el enunciado respalda más de un atributo y evaluar cómo lo maneja el escenario.

| Aspecto | Atributo del escenario | Atributo(s) alternativo(s) |
|---|---|---|
| Evidencia del enunciado | ... | ... |
| Correspondencia bibliográfica | ... | ... |
| Especificidad contextual | ... | ... |
| ¿Maneja el escenario la ambigüedad? | Sí / No / Parcial | ... |
| Estado / conclusión | ... | ... |

Si existe una alternativa defendible que el escenario no contempló ni descartó con justificación, marcar **E9** en la tabla de errores y resolverla en el escenario corregido (mantener ambos escenarios si ambos son válidos, o justificar el descarte). Si no hay ambigüedad relevante, indicarlo explícitamente en una línea.

### 2. Errores encontrados

| # | Parte | Código (E#) | Problema | Corrección propuesta |
|---|---|---|---|---|
| 1 | Stimulus | E4 | Se inventó "menos de 2 segundos". | El enunciado no fija valor → "No especificado" + **[INFERENCIA] Posible valor: ...** |

### 3. Escenario corregido

Escenario completo reescrito con las seis partes en formato **dato concreto (opción/valor bibliográfico)** según la sección 29, incluyendo su **Justificación**.

### 4. Checklist aplicado

Marcar los ítems de la sección 30 que correspondan, señalando cuáles fallaban y qué corrección los resolvió.

## Reglas del Modo 2

- **No corregir sobre lo corregido:** la salida final es una sola versión íntegra del escenario.
- **No inventar para corregir:** si falta información no se rellena con supuestos; se completa con "No especificado" y, cuando sea útil, **[INFERENCIA] Posible valor: ...**.
- **Preservar la trazabilidad:** cada corrección debe poder justificarse con el enunciado y el General Scenario.
- **Verificar siempre la ambigüedad:** antes de dar el escenario por correcto, reanalizar el enunciado (secciones 7, 8 y 32) y registrar el resultado en la sección 1.1 del formato de salida. Una ambigüedad ignorada es un error E9, aunque todas las seis partes del escenario estén bien construidas.
- **Si el escenario viene sin atributo declarado**, determinar el atributo más específico con las secciones 7 a 9, dejar constancia de la decisión y verificar también las alternativas de atributo como parte del análisis de ambigüedad.

---

# 34. Modo 3 — Árbol de utilidad

## Definición de la bibliografía

**[BIBLIOGRAFÍA]** El **árbol de utilidad** es la técnica de la sección **19.4 (Capturing ASRs in a Utility Tree)** de *Software Architecture in Practice, 4th Edition*: un modelo descendente que el arquitecto usa para descomponer atributos de calidad abstractos en **escenarios concretos y priorizados** cuando otras fuentes de ASR (documentos, stakeholders) son insuficientes. También se usa en el capítulo 20 (**Attribute-Driven Design, ADD**) como insumo para seleccionar los drivers de cada iteración de diseño.

El árbol tiene cuatro niveles:

1. **Raíz:** **Utility** (la utilidad general del sistema).
2. **Segundo nivel — atributos de calidad:** los que el arquitecto considera importantes (en el ejemplo del libro: Performance, Modifiability, Availability, Security, etc.).
3. **Tercer nivel — refinamientos (preocupaciones):** aspectos concretos de cada atributo relevantes para el sistema (ejemplos del libro: para Performance, "latency" y "throughput"; para Modifiability, "new products" y "new platforms"; para Availability, "hardware failure").
4. **Hojas — escenarios:** requisitos arquitectónicamente significativos expresados como escenarios de calidad concretos.

**[BIBLIOGRAFÍA]** Cada hoja se evalúa con **dos criterios en escala H / M / L** (high / medium / low):

- **Importancia (business value):** cuánto le importa al negocio y a los stakeholders cumplir ese escenario; H = imprescindible, L = prescindible.
- **Dificultad / riesgo técnico (technical risk):** cuán difícil o incierto resulta lograrlo en la arquitectura; H = alto riesgo de no alcanzarlo, L = hay confianza en cómo hacerlo.

Se anota como par **`(Importancia, Dificultad)`**, por ejemplo `(H, H)` = alta importancia y alta dificultad. **[BIBLIOGRAFÍA]** Los escenarios `(H, H)` son los de mayor prioridad de análisis: alto valor y alto riesgo.

## 34.1. Regla crítica: qué puede y qué no puede aportar la bibliografía

**[BIBLIOGRAFÍA]** La bibliografía aporta:

- **Categorías estructurales** del General Scenario (las seis partes y sus opciones/valores posibles).
- **Definiciones** de los atributos de calidad.
- **Escalas y criterios** de evaluación (por ejemplo la escala H / M / L y los criterios de importancia y dificultad).

**La bibliografía NO puede aportar:**

- Valores concretos del escenario que el enunciado no proporciona.
- Contextos o condiciones que el enunciado no describe.
- Detalles de implementación, tecnología o infraestructura.
- Métricas o umbrales que el enunciado no fija.

**Ejemplo de error común:**

> El enunciado dice "búsqueda en menos de 2 segundos". El General Scenario de Performance incluye "peak load" como opción de Environment. **Esto NO autoriza a agregar "peak load en temporadas altas" al escenario**, porque el enunciado no menciona condiciones de carga alta ni temporadas. El Environment correcto es el que el enunciado describe (o "No especificado" si no describe ninguno).

La cadena de trazabilidad para cada dato del escenario debe ser:

**DATO DEL ESCENARIO → ENUNCIADO (o categorías del GS) → JUSTIFICACIÓN**

Si un dato no tiene trazabilidad con el enunciado, es invención y debe eliminarse o marcarse como **[INFERENCIA]** con la marca apropiada.

## 34.2. Regla para las partes del escenario en Modo 3

Las seis partes del escenario (secciones 11 a 14) se construyen en Modo 3 **con las mismas reglas que en Modo 1** (sección 25). Esto significa:

1. **Stimulus Source:** usar solamente fuentes presentes en el enunciado. Si el enunciado no especifica la fuente, escribir "No especificado" y, si el contexto lo permite, agregar una interpretación razonable como **[INFERENCIA]**. No inventar fuentes basándose en conocimiento general sobre el tipo de sistema.

2. **Stimulus:** usar solamente el evento o solicitud descrito en el enunciado. No agregar escenarios hipotéticos (por ejemplo "peak load", "múltiples usuarios simultáneos", "ataque DDoS") a menos que el enunciado los mencione.

3. **Artifact:** usar solamente el elemento del sistema mencionado o directamente implicado por el enunciado. No inferir artifacts específicos (por ejemplo "documentación", "diagramas", "base de datos") a partir de suposiciones sobre cómo se implementaría el sistema. Si el enunciado dice "comprender la arquitectura", el artifact es el sistema o sus componentes arquitectónicos — no la documentación. **No sobre-adaptar el Artifact a partir de lo que el estímulo afecta concretamente**, especialmente en Availability: si el enunciado habla de "el pago no debe perderse", eso describe la *Response* ("recuperar/preservar el pago"), no necesariamente el *Artifact*. El artifact de Availability suele ser **el sistema o la parte del sistema afectada por el fault** (p. ej. procesadores, almacenamiento, procesos); se personaliza cuando el enunciado **nombra explícitamente** un componente afectado. Si el enunciado no nombra un componente específico, usar el artifact más general coherente con el GS.

4. **Environment:** usar solamente el estado o condición descrito en el enunciado. Si el enunciado no describe condiciones de operación específicas, escribir "No especificado" o, si el contexto lo justifica, usar la opción más genérica del GS que sea coherente con el requisito. No agregar condiciones de carga, modos degradados u otros escenarios que el enunciado no plantea.

5. **Response:** la respuesta debe corresponder directamente a lo que el enunciado exige. No agregar pasos adicionales de implementación (por ejemplo "cifrar en reposo", "registrar accesos", "hacer rollback") que el enunciado no solicita.

6. **Response Measure:** aplicar estrictamente la sección 26 y la sección 26.1. Si el enunciado da un valor concreto, usarlo. Si dice "rápidamente", "seguro", "disponible" u otro término vago, escribir "No especificado" y, si es útil, agregar **[INFERENCIA] Posible valor: ...** sin reemplazar "No especificado". Si el enunciado da una condición observable pero no numérica (p. ej. "sin afectar a los estudiantes"), esa condición puede reformularse como Response (no como Response Measure inventada); ver sección 26.1.

7. **Distinción entre contenido del enunciado y vocabulario del GS:** En cada una de las seis partes, lo que se escribe como contenido concreto del escenario debe provenir **exclusivamente del enunciado**. Las categorías del General Scenario (por ejemplo "fault", "attack", "overloaded operation", "production") son **referencias bibliográficas** que van entre paréntesis y **no deben tratarse como hechos del sistema**. Si el enunciado no describe un fault, no escribir "un fault" como contenido; si no describe producción, no escribir "Producción". El contenido del enunciado y la categoría del GS deben mantenerse siempre separados.

## 34.3. Regla para las prioridades (Importancia, Dificultad)

**[BIBLIOGRAFÍA]** La escala H / M / L y los criterios de importancia y dificultad provienen del libro (sección 19.4). El arquitecto asigna estos valores como parte del análisis.

**Procedimiento para la Importancia:**

- **La prioridad NO se deriva de la obligatoriedad del requisito.** Que un requisito diga "debe" no implica automáticamente prioridad High: "debe" indica que es un requisito, no su importancia relativa. Ejemplo: "El sistema debe permitir cambiar el logo" es obligatorio pero no necesariamente de prioridad H.
- **Base principal:** el enunciado. La importancia debe derivarse de **indicaciones explícitas de criticidad, impacto o valor para el negocio/stakeholders** presentes en el enunciado o contexto (por ejemplo "es crítico", "es un riesgo muy alto", "afecta directamente al negocio", "es el propósito central del sistema"). Si el enunciado califica el requisito como menor o de baja prioridad, aplicar ese valor.
- **Si el enunciado destaca un contexto relevante** (p. ej. "gran cantidad de usuarios concurrentes durante la inscripción"), ese contexto puede sustentar la importancia **solo si se lo vincula explícitamente** al atributo; no por sí mismo.
- **Si el enunciado no permite determinar la importancia:** escribir **No especificado** y explicar brevemente qué información faltaría para determinarla (criterio de importancia que otorguen los stakeholders, clasificación del mantenimiento de negocio, etc.). No asignar un valor H/M/L por el solo hecho de que el requisito sea obligatorio, ni infiriéndolo del conocimiento general sobre el atributo o el dominio.
- **No inventar stakeholders, prioridades de negocio ni impactos financieros** que el enunciado no describe.

**Procedimiento para la Dificultad:**

- **No hay datos de dificultad en el enunciado.** El enunciado normalmente describe requisitos de calidad, no complejidades técnicas específicas de su logro.
- **La dificultad es siempre "No especificado" salvo que el enunciado proporcione evidencia explícita de complejidad técnica.** No asignar H/M/L a partir del conocimiento general sobre un atributo.
- Cuando el enunciado sí describe una complejidad técnica explícita y el arquitecto estima un nivel, entonces y solo entonces se puede marcar el valor como **"[INFERENCIA] / Decisión de análisis Y"** con justificación trazable al enunciado.
- **Prohibido justificar la dificultad con detalles técnicos inventados.** No agregar afirmaciones como "requiere redundancia", "necesita cifrado", "implica failover", "usa contenedores" ni otros detalles de implementación que el enunciado no menciona.
- **Prohibido inferir la dificultad a partir de la naturaleza general del atributo.** Afirmaciones como "proteger pagos es exigente" o "alta disponibilidad es complejo" son inferencias basadas en conocimiento general, no en evidencia del enunciado, y por sí solas no autorizan a asignar H/M/L.
- **Si el enunciado no proporciona evidencia suficiente para determinar la dificultad, la respuesta correcta es "No especificado".** No asignar un valor H/M/L basándose en el conocimiento general sobre las características de un atributo de calidad.
- **Una inferencia sobre la dificultad arquitectónica basada en el conocimiento general de un atributo NO es suficiente para asignar H/M/L.** Por ejemplo, decir "proteger pagos es exigente" o "alta disponibilidad es complejo" son inferencias razonables como explicación, pero de ellas no se desprende un valor H/M/L determinado. Si el enunciado no describe explícitamente una dificultad técnica concreta, mantener **No especificado**.

**Formato obligatorio en la justificación de prioridades:**

Para cada escenario, la justificación debe contener **dos líneas separadas**:

1. **Importancia (X):** justificación basada en el enunciado. Si el enunciado no permite determinar la importancia, escribir **No especificado** y explicar brevemente qué información faltaría.
2. **Dificultad (Y):** siempre **No especificado**, salvo que el enunciado proporcione evidencia explícita de la complejidad técnica. Cuando se asigne un valor H/M/L, marcarlo como **[INFERENCIA] / Decisión de análisis** y justificar con trazabilidad al enunciado.

Ejemplo correcto (importancia determinada, dificultad no determinada):

> **Importancia H:** El enunciado afirma explícitamente que "la seguridad de los pagos es crítica para el negocio", lo que es una indicación explícita de criticidad. (La palabra "debe" por sí sola NO justificaría H).
>
> **Dificultad No especificado:** El enunciado no proporciona evidencia sobre la complejidad técnica de proteger las transacciones. Faltaría información sobre los vectores de ataque, las normativas aplicables o las restricciones técnicas para determinar la dificultad.

Ejemplo: si el enunciado solo dijera que "el sistema debe permitir cambiar el logo", la justificación correcta sería:

> **Importancia No especificado:** El enunciado no proporciona indicación de criticidad, impacto o valor para el negocio más allá de declarar el requisito. Faltaría información sobre cuán importante es para los stakeholders para asignar H/M/L.

Ejemplo correcto (importancia y dificultad determinadas):

> **Importancia H:** El enunciado establece explícitamente una disponibilidad del 99,9%, lo que indica un requisito crítico.
>
> **Dificultad [INFERENCIA] / Decisión de análisis H:** El enunciado describe explícitamente el logro de ese objetivo como "difícil de alcanzar"/"de alta complejidad técnica", lo que constituye evidencia explícita de complejidad. La asignación de H se apoya en esa afirmación del enunciado, no en conocimiento general sobre Availability.

Ejemplo **incorrecto** (lo que NO se debe hacer):

> ~~**Dificultad H:** Lograr 99,9% implica apenas ~8,76 horas de inactividad al año. Requiere arquitectura con redundancia, failover, monitoreo y recuperación automática.~~

Esto es incorrecto porque introduce cálculos y decisiones técnicas no derivadas del enunciado.

Ejemplo **incorrecto** (lo que NO se debe hacer):

> ~~**Dificultad [INFERENCIA] / Decisión de análisis H:** Proteger transacciones de pago implica un objetivo exigente que requiere consideraciones arquitectónicas significativas.~~

Esto es incorrecto porque "proteger pagos es exigente" es una inferencia basada en el conocimiento general sobre Security, no en evidencia del enunciado. Sin evidencia explícita de complejidad técnica, la dificultad debe ser **No especificado**.

## Procedimiento

1. **Determinar la entrada:** atributos de calidad que vienen de un enunciado, de un análisis del Modo 1, o de escenarios verificados en el Modo 2. Si se parte del enunciado, aplicar primero las secciones 1 a 8 para separar funcionalidad de calidad e identificar atributos.
2. **Seleccionar la raíz:** "Utility".
3. **Segundo nivel → atributos:** listar los atributos CONFIRMADOS y los POSIBLES relevantes (sección 4). No incluir atributos sin evidencia cuando se trabaje desde un enunciado.
4. **Verificar cada atributo contra su General Scenario:** antes de confirmar un atributo, comparar el foco del requisito con la definición del atributo y las opciones de su General Scenario (secciones 15 a 24 de `references/general-scenarios.md`). Si la correspondencia no es directa, justificar explícitamente por qué el atributo elegido es el más específico (aplicar secciones 7 a 9 y 32).
5. **Tercer nivel → preocupaciones:** refinar cada atributo en **1 a 3 preocupaciones concretas** con evidencia del enunciado. **No inventar preocupaciones** basándose en conocimiento general sobre el dominio del sistema. Si el enunciado proporciona un solo requisito por atributo, una sola preocupación es suficiente; no forzar subdivisiones.
6. **Hojas → escenarios:** por cada preocupación, construir **al menos un escenario concreto** con las seis partes (secciones 11 a 14 y 25). Aplicar la sección 34.2: cada parte debe tener trazabilidad directa con el enunciado o con las categorías del General Scenario. Cada hoja es una instancia fiel del General Scenario del atributo.
7. **Priorizar cada hoja:** asignar `(Importancia, Dificultad)` con H / M / L aplicando la sección 34.3. La importancia se apoya en evidencia del enunciado (si la hay; en caso contrario, **No especificado**). La dificultad es **No especificado** salvo que el enunciado proporcione evidencia explícita de complejidad técnica; en ese caso, marcarla como **[INFERENCIA] / Decisión de análisis**.
8. **Presentar el árbol** con su tabla de escenarios y la justificación de prioridades.

## Formato de salida del Modo 3

### 1. Árbol de utilidad

```
UTILITY
├── Performance
│   ├── Latencia de datos
│   │   └── (H,M) Escenario: ...
│   └── Throughput de transacciones
│       └── (M,L) Escenario: ...
├── Modifiability
│   └── Nuevo producto
│       └── (H,H) Escenario: ...
├── Availability
│   └── Falla de hardware
│       └── (M,M) Escenario: ...
└── Security
    └── Acceso no autorizado
        └── (H,H) Escenario: ...
```

**Nota sobre la notación del árbol:** El ejemplo anterior ilustra la forma general `(Importancia, Dificultad)`. Cuando el enunciado no permite determinar una de las dos, se escribe **"No especificado"** en esa posición, por ejemplo `(H, No especificado)`; y cuando ambas no pueden determinarse, `(No especificado, No especificado)`. A diferencia de las hojas (que siempre tienen las seis partes del escenario), los valores de Importancia y Dificultad **no siempre tienen un valor H/M/L**: solo se escriben cuando el enunciado aporta evidencia para determinarlos (sección 34.3).

### 2. Tabla de escenarios priorizados

Para cada hoja, el escenario completo en el formato de la sección 29:

| Atributo | Preocupación | Prioridad (Imp., Df.) | Escenario (seis partes) | Justificación |
|---|---|---|---|---|
| Performance | Latencia de datos | (H,M) | ... | ... |

### 3. Justificación de prioridades

**Dos líneas por escenario**, en este formato exacto:

> **Importancia X:** justificación basada en el enunciado. Si el enunciado no permite determinarla, escribir **No especificado** y explicar qué información faltaría.
>
> **Dificultad Y:** escriba **No especificado** a menos que el enunciado proporcione evidencia explícita de complejidad técnica; en ese caso escriba **[INFERENCIA] / Decisión de análisis Y:** con justificación trazable al enunciado, sin detalles técnicos inventados.

**Nota sobre la priorización:** La escala H/M/L proviene de la bibliografía (sección 19.4), pero los valores concretos deben derivarse del enunciado. El enunciado puede fijar la **importancia** solo si usa lenguaje de criticidad o impacto explícito (p. ej. "es crítico", "es un riesgo muy alto", "afecta directamente al negocio", "es el propósito central del sistema"). La mera palabra **"debe" NO es indicación de importancia High**: solo declara que es un requisito. Si el enunciado no expresa criticidad explícita para ese atributo, la importancia es **No especificado**. La dificultad será normalmente **No especificado**, y solo se asigna un valor cuando el enunciado describe explícitamente la complejidad del logro del objetivo.

## Reglas de fidelidad del Modo 3

- **[BIBLIOGRAFÍA]** Mantener la notación *Utility → atributo → preocupación → escenario (Importancia, Dificultad)*. La raíz y los niveles se etiquetan como en el libro.
- Aplicar las reglas de transparencia (sección 3): distinguir dato del enunciado, dato de la bibliografía e inferencia; marcar **[INFERENCIA]** y conservar "No especificado" cuando corresponda.
- **Las prioridades no son datos del enunciado.** La importancia se apoya en evidencia **explícita de criticidad/impacto** del enunciado; la mera palabra "debe" no implica High. Cuando el enunciado no permite determinar la importancia, escribir **No especificado**. La dificultad es **No especificado** salvo evidencia explícita en el enunciado; nunca se infiere H/M/L a partir del conocimiento general sobre un atributo (sección 34.3).
- **El árbol no reemplaza los escenarios individuales:** cada hoja debe poder desarrollarse como un escenario completo del Modo 1.
- **Cada atributo debe justificarse contra su General Scenario** (paso 4 del procedimiento). No asumir que la clasificación es correcta solo porque la palabra del enunciado "coincida" con el nombre del atributo.
- **No inventar contenido de las partes del escenario:** aplicar la sección 34.2 estrictamente. Cada parte del escenario debe tener trazabilidad con el enunciado. El vocabulario del GS (fault, attack, overloaded operation, production, detect/recover, etc.) no debe convertirse en contenido concreto del escenario: va entre paréntesis como referencia bibliográfica. Lo que el enunciado no describe se marca "No especificado".
- **No inventar detalles técnicos para justificar prioridades:** aplicar la sección 34.3 estrictamente. No agregar tecnologías, patrones, mecanismos ni decisiones de implementación que el enunciado no menciona.
- Como guía de revisión: todos los atributos en alcance deben tener rama; cada preocupación debe tener al menos un escenario; cada hoja debe tener su escenario en forma completa y sus dos prioridades (que pueden ser **No especificado** cuando corresponda).