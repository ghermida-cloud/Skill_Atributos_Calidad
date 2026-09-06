# Ejemplos de testeos

Ejemplos utilizados para validar y mejorar la skill de análisis de atributos de calidad.

---

## Sistema de transporte público

**Archivo de salida:** `transporte-publico.md` / `transporte-publico.html`

**Enunciado:** Una aplicación muestra a los usuarios la ubicación de los colectivos en tiempo real. La información debe actualizarse continuamente. La aplicación debe poder incorporar información proveniente de nuevos operadores de transporte sin necesidad de modificar significativamente el sistema existente.

### Atributos identificados

| Atributo | Estado |
|---|---|
| Performance | Confirmado |
| Modifiability | Confirmado |
| Integrability | Posible |

### Mejoras que disparó

**Modos mejorados:** Modo 1 (Análisis y construcción de escenarios)

1. **Manejo de ambigüedad Modifiability vs. Integrability (Modo 1)** — Validó la sección 32.1: el enunciado respaldaba ambos atributos y la skill tuvo que comparar especificidad contextual, justificar la elección y construir ambos escenarios.
2. **Estado POSIBLE para Integrability (Modo 1)** — Probó que la skill puede manejar atributos que no están plenamente confirmados, indicando qué faltaría para confirmarlos.
3. **Múltiples atributos por fragmento (Modo 1)** — Un solo párrafo generó dos atributos confirmados (Performance + Modifiability) y uno posible (Integrability), validando que la skill no fuerza una única clasificación.
4. **Generación de archivos de salida (Modo 1)** — Confirmó que el flujo sección 29.1 (entrega de archivos) funciona: `.md` con el análisis completo y `.html` con CSS embebido y tablas renderizadas.

---

## Plataforma de comercio electrónico

**Modo utilizado:** Modo 2 (Verificación y corrección)

**Enunciado:** Plataforma de comercio electrónico. El sistema debe responder rápidamente cuando un usuario consulta un producto.

**Escenario a verificar:**

| Parte | Escenario propuesto |
|---|---|
| Stimulus Source | Usuario (end user) |
| Stimulus | Consulta de un producto (request for service) |
| Artifact | Servidor web (server) |
| Environment | Operación normal (normal operation) |
| Response | Mostrar el producto |
| Response Measure | Menos de 2 segundos |

### Errores detectados

| # | Parte | Código | Problema |
|---|---|---|---|
| 1 | Stimulus Source | E2 | Entre paréntesis dice "end user" (nombre de la parte en Usability/Modifiability), no la opción bibliográfica de Performance que es **user**. |
| 2 | Response Measure | E8 | El enunciado dice **"rápidamente"**, pero el escenario lo sustituyó por **"menos de 2 segundos"**, un valor numérico concreto que no existe en el enunciado. |

### Mejoras que disparó

1. **Ampliación de E8 (Modo 2)** — El error original de E8 solo cubría medidas "no comprobables o inventadas". "Menos de 2 segundos" parecía razonable y comprobable, por lo que pasó desapercibido. Se amplió E8 para incluir **trazabilidad con el enunciado**: ahora verifica que el Response Measure no sustituya términos vagos ("rápidamente") por valores concretos inventados.
2. **Nuevo ítem en checklist (Modo 1 y 2)** — Se agregó al checklist de la sección 30: *"Response Measure tiene trazabilidad directa con el enunciado: no se sustituyeron términos vagos por valores concretos inventados."* Aplica tanto a la construcción (Modo 1) como a la verificación (Modo 2).

---

## Sistema bancario online

**Modo utilizado:** Modo 2 (Verificación y corrección)

**Enunciado:** Sistema bancario online. Los clientes deben poder realizar transferencias bancarias. Ante una solicitud de transferencia, el sistema debe procesarla en menos de 2 segundos durante operación normal.

**Escenario a verificar:**

| Parte | Escenario propuesto |
|---|---|
| Stimulus Source | Cliente (end user) |
| Stimulus | Solicitud de una transferencia (request for service) |
| Artifact | Sistema bancario (system) |
| Environment | Operación normal (normal operation) |
| Response | Procesar la transferencia y devolver el resultado |
| Response Measure | Menos de 2 segundos |

### Errores detectados

| # | Parte | Código | Problema |
|---|---|---|---|
| 1 | Stimulus | E3 | Entre paréntesis dice "request for service", que no es una opción contemplada en el GS de Performance. El GS dice: *"Llegada de un evento... Puede ser una solicitud o una notificación"*. La opción bibliográfica más fiel es **"arrival of a request"**. |
| 2 | Response Measure | — | Faltaba el paréntesis con la opción bibliográfica correspondiente. El GS lista *"Latency, deadline, throughput..."* y "menos de 2 segundos" corresponde a **deadline / latency**. |

### Mejoras que disparó

1. **Rigor en opciones bibliográficas de Stimulus (Modo 2)** — "request for service" parecía razonable pero no aparece en el GS de Performance. Se reforzó que el paréntesis debe contener una opción **explícita del GS del atributo**, no una formulación genérica. Aplica a Modo 1 y 2.
2. **Paréntesis obligatorio en Response Measure (Modo 2)** — Un escenario sin paréntesis en Response Measure pasó desapercibido hasta la verificación. Se reforzó que toda parte debe incluir la convención dato concreto (opción/valor bibliográfico), incluso cuando el dato del enunciado es claro. Aplica a Modo 1 y 2.

---

## Sistema de pagos online

**Modo utilizado:** Modo 2 (Verificación y corrección)

**Enunciado:** Sistema de pagos online. Antes de aprobar una transacción, el sistema debe verificar que la operación sea legítima y debe completar la verificación en menos de 2 segundos.

**Escenario a verificar:**

| Parte | Escenario propuesto |
|---|---|
| Stimulus Source | Usuario |
| Stimulus | Solicitud de pago |
| Artifact | Sistema de pagos |
| Environment | Operación normal |
| Response | Verificar y aprobar la transacción |
| Response Measure | Menos de 2 segundos |

### Errores detectados

| # | Parte | Código | Problema |
|---|---|---|---|
| 1 | Response Measure | E2 | Entre paréntesis decía "medida bibliográfica correspondiente" (nombre de categoría) en lugar de la opción/valor del GS de Performance (**latency**). |
| 2 | (ambigüedad) | E9 | El enunciado respalda también **Security** ("verificar que la operación sea legítima"), pero el escenario no manejaba la ambigüedad; la skill la mencionó solo como nota al pasar, no como parte formal de la verificación. |

### Mejoras que disparó

**Modos mejorados:** Modo 2 (y checklist de la sección 30, compartido por Modos 1 y 3)

1. **Verificación de ambigüedad obligatoria en Modo 2** — Se agregó un paso nuevo al procedimiento del Modo 2 que reanaliza el enunciado en busca de atributos alternativos defendibles y comprueba que el escenario los maneje. Si no los trata, es error E9, aunque las seis partes estén bien construidas.
2. **E9 ampliado (Modo 2)** — Antes solo cubría ambigüedad "mal resuelta"; ahora incluye "no detectada" y aclara que el silencio sobre una ambigüedad relevante es también E9.
3. **Nueva sección 1.1 "Análisis de ambigüedad" (Modo 2)** — Obligatoria en el formato de salida, con tabla que compara el atributo del escenario vs. alternativas (evidencia, correspondencia bibliográfica, especificidad, ¿maneja la ambigüedad?, conclusión).
4. **Ítems de checklist (Modo 1, 2 y 3)** — Se agregaron ítems en la sección 30 para verificar explícitamente la ambigüedad y registrar E9 en Modo 2. El checklist es compartido, por lo que refuerza también Modo 1 y Modo 3.

---

## Aplicación educativa (Usability)

**Modo utilizado:** Modo 2 (Verificación y corrección)

**Enunciado:** Un estudiante que utiliza el sistema por primera vez debe poder aprender a utilizarlo sin capacitación previa y completar una inscripción a una materia.

**Escenario a verificar:**

| Parte | Escenario propuesto |
|---|---|
| Stimulus Source | Estudiante |
| Stimulus | Quiere utilizar el sistema |
| Artifact | Sistema |
| Environment | Primera utilización |
| Response | Permitir que el estudiante complete la inscripción |
| Response Measure | Menos de 30 segundos |

### Errores detectados

| # | Parte | Código | Problema |
|---|---|---|---|
| 1 | Artifact | E7 | Dice "Sistema" pero el GS de Usability especifica que el artifact es la interfaz (GUI, command-line interface, etc.), no el sistema genérico. |
| 2 | Response | E7 | Dice "Permitir que el estudiante complete la inscripción" pero la Response del GS se centra en cómo el sistema facilita la usabilidad (proporcionar feedback, anticipar necesidades, permitir interacción), no en la tarea en sí. |
| 3 | Response Measure | E4, E5, E8 | "Menos de 30 segundos" es un valor inventado sin trazabilidad con el enunciado. El enunciado no especifica ningún tiempo concreto. |
| 4 | Convención | — | Falta usar la convención de paréntesis: dato concreto (opción/valor bibliográfico). |

### Mejoras que disparó

**Modos mejorados:** Modo 2 (y checklist de la sección 30, compartido por Modos 1 y 3)

1. **Artifact en Usability (Modo 2)** — Validó que el GS de Usability define el artifact como la interfaz (GUI, voice interface, touch screen, etc.), no como "sistema" de forma genérica. Refuerza que el artifact debe corresponder a las opciones del GS específico del atributo. Aplica a Modo 1 y 2.
2. **Response en Usability vs. funcionalidad (Modo 2)** — Detectó confusión entre la Response del escenario de calidad (cómo el sistema facilita la usabilidad) y el requerimiento funcional (completar la inscripción). La Response debe enfocarse en la propiedad de calidad, no en la tarea. Aplica a Modo 1 y 2.
3. **Response Measure sin trazabilidad (Modo 2)** — Reafirmó que E8 cubre también valores "razonables" pero inventados: "menos de 30 segundos" parece plausible pero no tiene soporte en el enunciado. Refuerza que la trazabilidad es obligatoria. Aplica a Modo 1 y 2.

---

## Sistema de reservas de hoteles

**Modo utilizado:** Modo 3 (Árbol de utilidad)

**Enunciado:** Sistema de reservas de hoteles. (1) Disponible 99,9% del tiempo. (2) Búsqueda de habitaciones en < 2 segundos. (3) Datos de tarjetas de crédito no expuestos a accesos no autorizados. (4) Despliegue de nuevas versiones sin interrumpir servicio. (5) Nuevos desarrolladores comprenden rápidamente la arquitectura.

### Problemas detectados en la salida

| # | Problema | Modo afectado |
|---|---|---|
| 1 | **Invención de detalles técnicos para justificar dificultad.** La skill justificó "Dificultad H" para Availability con afirmaciones como "requiere redundancia, failover, monitoreo" — detalles de implementación no derivados del enunciado. | Modo 3 |
| 2 | **Invención de contenido en partes del escenario.** En Usability, inventó el artifact como "documentación arquitectónica, diagramas y código" cuando el enunciado solo dice "comprender la arquitectura". En Performance, agregó "peak load en temporadas altas" como Environment sin que el enunciado mencione condiciones de carga. En Security, agregó "cifrado en reposo, PCI-DSS" como parte de la Response. | Modo 3 (aplica a 1 y 2) |
| 3 | **Invención de Response Measure.** En Usability, el enunciado dice "rápidamente" sin valor concreto, pero la skill propuso "el tiempo que tarda es razonable" como posible valor, mezclando inferencia con la medida real del escenario. | Modo 3 (aplica a 1 y 2) |
| 4 | **Clasificación de atributo no justificada contra el GS.** La skill afirmó "No se identificaron atributos posibles ni ambiguos" sin justificar por qué Usability (en lugar de Modifiability u otro atributo) es la clasificación correcta para "comprender la arquitectura". | Modo 3 (aplica a 1 y 2) |
| 5 | **Prioridades presentadas como datos del enunciado.** Los pares (H,H), (H,M), etc. se presentaron sin marcar que la dificultad es una decisión de análisis. | Modo 3 |

### Mejoras que disparó

**Modo principal mejorado:** Modo 3. Algunas mejoras apuntan también a Modos 1 y 2.

1. **Nueva sección 34.1 — Regla crítica: qué puede y qué no puede aportar la bibliografía (Modo 3).** Establece que la bibliografía aporta estructura (categorías del GS, escalas) pero NO valores concretos, contextos, detalles técnicos ni métricas. Incluye el ejemplo de error común con "peak load". Influye en Modo 1 y 2 porque la distinción es general.

2. **Nueva sección 34.2 — Regla para las partes del escenario en Modo 3 (Modo 3).** Refuerza que cada parte del escenario en Modo 3 debe seguir las mismas reglas de trazabilidad que en Modo 1. Prohíbe inventar artifacts, environments, responses de implementación o fuentes no descritas. Aplica también a Modo 1 y 2.

3. **Nueva sección 34.3 — Regla para las prioridades (Modo 3).** Formaliza que la dificultad es siempre `[INFERENCIA] / Decisión de análisis`. Prohíbe justificarla con detalles técnicos inventados. Establece formato obligatorio de dos líneas (importancia + dificultad) con ejemplos correctos e incorrectos. Exclusivo de Modo 3.

4. **Paso 4 nuevo en el procedimiento — Verificar atributo contra su GS (Modo 3).** Obliga a justificar la clasificación de cada atributo comparándolo con su General Scenario antes de incluirlo en el árbol. Aborda el problema de clasificaciones no cuestionadas. Aplica a Modo 1 y 2.

5. **Checklist expandido — 9 ítems nuevos para Modo 3 (Modo 3).** Incluye verificaciones de trazabilidad en partes del escenario, prohibición de inventar contextos y detalles técnicos, formato de prioridades, y no forzar subdivisiones de preocupaciones.

6. **Regla de oro ampliada (Modos 1, 2 y 3).** Segundo párrafo que sintetiza: "Lo que el enunciado no dice, se marca 'No especificado'. Lo que se infiere, se marca [INFERENCIA]. Lo que se inventa, se elimina."

---

## Plataforma de comercio electrónico (Árbol de utilidad)

**Modo utilizado:** Modo 3 (Árbol de utilidad)

**Enunciado:** Plataforma de comercio electrónico. La empresa considera la seguridad de los pagos crítica; una caída en fechas de alta demanda es un riesgo muy alto; el tiempo de respuesta es importante pero con menor prioridad. Requisitos: (1) transacciones de pago protegidas contra accesos no autorizados; (2) permanecer disponible durante eventos de alta demanda; (3) consultas de productos en menos de 2 segundos; (4) nuevas versiones desplegables sin interrumpir el servicio; (5) desarrolladores que modifiquen reglas de descuentos con bajo esfuerzo.

### Problemas detectados en la salida

| # | Problema | Modo afectado |
|---|---|---|
| 1 | **Inferencia excesiva de dificultad (H/M).** La skill asignó (H,H) a Security y Availability, (M,M) a Performance, Deployability y Modifiability, aunque el enunciado solo permite fijar la **importancia** (H para Security/Availability, M para Performance) y **no dice nada de la dificultad técnica**. Frases como "requiere consideraciones arquitectónicas significativas" y "objetivo alcanzable sin complejidad extrema" razonaban sobre dificultad sin evidencia en el enunciado. | Modo 3 |
| 2 | **Contaminación del escenario con vocabulario del GS.** En Availability puso como Stimulus "un fault que afecte la disponibilidad" y como Response "detectar, prevenir o recuperarse del fault", cuando el enunciado solo afirma "permanecer disponible". Convertía categorías genéricas del General Scenario (fault, detect/recover) en hechos del sistema. | Modo 3 (aplica a 1) |
| 3 | **"Producción" como inferencia no marcada.** En Deployability usó Environment "Producción (production)" sin que el enunciado lo mencione; debería ser "No especificado" o marcarse como [INFERENCIA]. | Modo 3 (aplica a 1) |
| 4 | **Prioridades de dificultad presentadas como determinadas.** | Modo 3 |

### Mejoras que disparó

**Modo principal mejorado:** Modo 3.

1. **Regla de dificultad más estricta (Modo 3).** En la sección 34.3 se eliminó el "M por defecto" y la obligación de marcar siempre la dificultad como decisión de análisis. Nueva regla: la dificultad es **"No especificado"** salvo que el enunciado provea **evidencia explícita de complejidad técnica**; se prohíbe inferir H/M/L del conocimiento general del atributo ("proteger pagos es exigente", "alta disponibilidad es complejo"). Se agregó el ejemplo incorrecto que ilustra justamente este caso. La **importancia** también pasa a "No especificado" si el enunciado no permite determinarla (p. ej. Deployability y Modifiability sin prioridad explícita).
2. **Distinción contenido del enunciado vs. vocabulario del GS (Modo 3, aplica a Modo 1).** Nueva regla 7 en la sección 34.2: el contenido concreto de cada parte del escenario debe provenir **exclusivamente del enunciado**; las categorías del GS (fault, attack, overloaded operation, production, detect/recover) son referencias bibliográficas que van entre paréntesis y no deben tratarse como hechos del sistema. Corrige "Producción" y "un fault" como contenido.
3. **Formato de prioridades actualizado (Modo 3).** La justificación de dos líneas ahora permite "No especificado" en Importancia y/o Dificultad, con ejemplos correctos e incorrectos; la notación del árbol admite `(H, No especificado)`.
4. **Checklist del Modo 3 actualizado (Modo 3).** Ítems que verifican que la dificultad sea "No especificado" salvo evidencia explícita, y que no se use vocabulario del GS como contenido concreto.

**Salida esperable en este enunciado (Modo 3):** Security `(H, No especificado)`, Availability `(H, No especificado)`, Performance `(M, No especificado)`, Deployability `(No especificado, No especificado)`, Modifiability `(No especificado, No especificado)`.

---

## Sistema de pagos de una universidad

**Modos utilizados:** Modo 2 (Verificación y corrección) + Modo 3 (Árbol de utilidad)

**Enunciado:** Sistema de pagos de una universidad. Los estudiantes pagan matrículas u otros conceptos mediante tarjeta o transferencia bancaria; las operaciones deben ser seguras; durante el período de inscripción se espera una gran cantidad de usuarios concurrentes. Requisitos: (1) un estudiante puede realizar un pago; (2) procesar los pagos rápidamente; (3) transacciones protegidas contra accesos no autorizados; (4) si un servidor falla durante una operación el pago no debe perderse; (5) poder incorporar un nuevo proveedor de pagos en el futuro; (6) las nuevas versiones deben desplegarse sin afectar a los estudiantes que realizan pagos; (7) los administradores deben poder ejecutar pruebas antes de cada entrega.

**Cinco escenarios a verificar** (A–E: Performance, Security, Availability, Integrability, Deployability).

### Errores detectados (Modo 2)

| Escenario | Código | Problema |
|---|---|---|
| A Performance | E4/E8 | "Menos de 2 segundos" inventado; el enunciado dice solo "rápidamente". |
| B Security | E4 | Artifact "base de datos" no está en el enunciado; el requisito protege "las transacciones". |
| B Security | E4/E8 | "100% de los ataques" inventado. |
| C Availability | E7 | Response "continuar funcionando" no capta "el pago no debe perderse". |
| C Availability | E4/E8 | "99,99% de disponibilidad" inventado. |
| D Integrability | E4/E8 | "Un día de trabajo" inventado. |
| E Deployability | E6/INF | "Producción" no está explícito. |

### Mejoras que disparó

**Modos mejorados:** Modo 3 (principal), y las reglas nuevas armonizan Modos 1, 2 y 3.

1. **"Debe" no implica prioridad H (Modo 3).** Al priorizar, la skill asignó **H a los seis atributos** por el solo hecho de que cada requisito usa "debe". Se corrigió la sección 34.3: la obligatoriedad de un requisito NO determina su importancia; esta deriva de **indicaciones explícitas de criticidad/impacto** ("es crítico", "riesgo muy alto", "propósito central"). Sin esa evidencia → **No especificado**. Se agregó el contraejemplo del logo ("el sistema debe permitir cambiar el logo" es obligatorio pero no necesariamente H). En este testeo, solo Security (contexto "las operaciones deben ser seguras") sostiene H; el resto queda en No especificado.
2. **Distinción dato explícito / reformulación válida / métrica inventada (Modo 2 y 3, aplica a Modo 1).** En Deployability la skill marcó "cero interrupciones" como invención, cuando es una reformulación fiel de "sin afectar a los estudiantes". Se agregó la sección **26.1**: una reformulación que conserva el sentido del enunciado ("sin interrumpir los pagos en curso") NO es una inferencia problemática; sí lo es inventar un umbral numérico ("0 segundos", "100%"). Se actualizó el error **E8** para reflejarlo.
3. **No sobre-adaptar el Artifact de Availability (Modo 2 y 3, aplica a Modo 1).** La skill cambió el Artifact de "Sistema" a "el pago" porque "lo que no se pierde es el pago". Se aclaró en la sección 34.2 (regla 3): en Availability el Artifact suele ser **el sistema / la parte afectada por el fault**; "el pago" describe la **Response**, no el Artifact. Solo se personaliza si el enunciado nombra explícitamente un componente afectado.

---

## Sistema de monitoreo de radares

**Modo utilizado:** Modo 1 (Análisis y construcción)

**Archivo de salida:** `escenario-atributo-calidad-sistema-monitoreo-radares.md` / `.html`

**Enunciado:** Un sistema de monitoreo de radares debe soportar la incorporación de varios dispositivos (radares) con distinta tecnología para su monitoreo.

### Atributos identificados

| Atributo | Estado |
|---|---|
| Integrability | Confirmado |

### Ambigüedades identificadas (manejo correcto)

| # | Ambigüedad | Cómo la resolvió la skill |
|---|---|---|
| 1 | Integrability vs. Modifiability (sección 32.1) | El cambio del enunciado consiste precisamente en **incorporar/integrar** componentes (los radares). La skill mostró ambos atributos con su evidencia, justificó cada uno y eligió **Integrability** como el más específico (preocupación por integrar elementos), conservando Modifiability como lectura general válida del cambio. |
| 2 | Integrability vs. Interoperability (sección 32.2) | Aplicó la distinción [CÁTEDRA / CLASE] desarrollo/integración vs. runtime: el foco del enunciado es la **incorporación** de los radares para su monitoreo, no el intercambio de información entre sistemas en ejecución. Descartó Interoperability con justificación explícita (el monitoreo en runtime es la funcionalidad, no la preocupación condicionada). |

### Secciones validadas

Este testeo no disparó cambios a la skill: validó el comportamiento ya incorporado en la skill.

1. **Ambigüedad Integrability vs. Modifiability (Modo 1)** — Validó la sección 32.1: ante "incorporación de dispositivos (radares)", la skill no eligió por la palabra ni aplicó una regla automática; comparó el foco concreto del requisito con las definiciones del libro y determinó que Integrability es la preocupación más específica, sin descartar Modifiability.
2. **Ambigüedad Integrability vs. Interoperability (Modo 1)** — Validó la sección 32.2: la skill evaluó explícitamente si los radares de distinta tecnología implicaban intercambio de información en runtime y concluyó, con la regla práctica que distingue incorporar un elemento (Integrability) de colaborar/intercambiar en ejecución (Interoperability), que la preocupación es de integración.
3. **Generación de archivos de salida (Modo 1)** — Confirmó nuevamente el flujo de la sección 29.1 (`.md` con el análisis completo y `.html` con CSS embebido y tablas renderizadas).

---

## Aplicación móvil de e-commerce (Performance)

**Modo utilizado:** Modo 1 (Análisis y construcción)

**Archivo de salida:** `escenario-atributo-calidad-aplicacion-ecommerce.md` / `.html`

**Enunciado:** Una aplicación móvil para e-commerce debe ser capaz de realizar varias búsquedas geolocalizadas de forma rápida, especialmente en períodos de promociones.

### Atributos identificados

| Atributo | Estado |
|---|---|
| Performance | Confirmado |

### Ambigüedades identificadas (manejo correcto)

| Ambigüedad | Cómo la resolvió la skill |
|---|---|
| Performance vs. Availability | Descartó Availability: el contexto de promociones describe exigencia de respuesta (demanda), no fallas ni tolerancia a fallas. |
| Performance vs. Usability | Descartó Usability: "de forma rápida" refiere al tiempo de la búsqueda (restricción temporal), no a la facilidad de uso. |

### Modificaciones que disparó

**Modo mejorado:** Modo 1

1. **Nueva sección 25.1 — Tipo de evento de llegada en escenarios de Performance (Modo 1).** Es la **única** modificación que este testeo disparó. Al construir el escenario de Performance, la skill indicó el tipo de evento de llegada de forma orgánica (en el ejemplo: búsquedas a pedido de cada usuario). Para formalizarlo, se agregó la sección 25.1: cuando el atributo es Performance, el Stimulus debe declarar cuál de los tres tipos de evento de llegada del GS se ajusta mejor al escenario, en el formato "evento de llegada [periódico, esporádico o estocástico] + breve explicación", con su referencia rápida y la regla de "No especificado" / [INFERENCIA] si el enunciado no permite determinarlo.

---

## Alquiler de monopatines eléctricos

**Modo utilizado:** Modo 1 (Análisis y construcción)

**Archivo de salida:** `escenarios-atributos-calidad-monopatines.md` / `.html`

**Enunciado:** Empresa que lanza un negocio de alquiler de monopatines eléctricos en paradas de una ciudad capital. Requiere una app móvil para los usuarios y una app web para la gestión (mantenimiento y administración). Los monopatines se buscan y se dejan en paradas predefinidas; se activan por código QR y el viaje queda asociado a una cuenta vinculada a Mercado Pago, descontando crédito por tiempo de uso. La app no debe permitir finalizar un viaje salvo que el GPS del monopatín confirme que se encuentra en una parada permitida. Los monopatines cuentan con GPS para determinar su ubicación "en todo momento" y la app muestra un mapa interactivo con los monopatines cercanos. El Administrador gestiona monopatines, paradas y precios; el Encargado de Mantenimiento registra acciones de mantenimiento y se generan reportes de uso (kilómetros, tiempo con y sin pausas).

### Atributos identificados

| Atributo | Estado |
|---|---|
| Safety | Confirmado |
| Performance | Posible |
| Availability | Posible |
| Security | Posible |
| Usability | Posible |
| Integrability | Posible |
| Interoperability | Posible (alternativa a Integrability) |

### Comportamiento correcto detectado

1. **Detección correcta de atributos con justificación del porqué.** Identificó todos los atributos relevantes del enunciado (Safety, Performance, Availability, Security, Usability, Integrability) y justificó la presencia de cada uno con evidencia textual, correspondencia bibliográfica y trazabilidad con su General Scenario. No incluyó atributos sin evidencia (Deployability, Energy Efficiency, Testability) ni clasificó por palabras aisladas. Este comportamiento valida las secciones 4 a 9 y la regla de fidelidad al GS.
2. **Manejo correcto de las ambigüedades (secciones 7, 28 y 32).** GPS/fin de viaje (Safety vs. regla de negocio funcional), mapa/ubicación (Performance vs. Availability) y Mercado Pago (Integrability vs. Interoperability) se analizaron con la tabla comparativa, se mantuvieron las alternativas defendibles y se construyeron escenarios para cada una.

### Justificación del comportamiento (muchos POSIBLE y un solo CONFIRMADO)

1. **El enunciado es ambiguo y de baja especificidad.** La mayoría de los fragmentos expresa pistas razonables pero sin exigencias explícitas. Ante esa falta de especificidad, la skill aplicó correctamente la sección 4: no hay evidencia suficiente para afirmar una exigencia plena del atributo, por lo que corresponde POSIBLE y no CONFIRMADO. Confirmar Performance, Availability, Security, Usability o Integrability habría sido sobreinterpretar el enunciado.
2. **Los POSIBLE son pistas razonables, no atributos descartados.** En cada caso la skill marcó la evidencia, explicó por qué podría corresponder y qué faltaría para confirmarlo, sin confirmarlos ni eliminarlos por falta de datos. Es el comportamiento esperado de la sección 4 cuando el enunciado no decide.
3. **Ambigüedades correctamente mantenidas.** Como el enunciado es ambiguo (GPS → Safety/regla de negocio; mapa → Performance/Availability; Mercado Pago → Integrability/Interoperability), la skill conservó ambas lecturas y construyó ambos escenarios (secciones 7, 8, 28 y 32), en lugar de forzar una única clasificación.

### Secciones validadas

Este testeo no disparó cambios a la skill: validó el comportamiento ya incorporado.

1. **Estados de atributos (sección 4)** — Validó el criterio de confirmación: con un enunciado ambiguo y de baja especificidad, es correcto que predominen los POSIBLE y que solo se confirme lo que tiene exigencia inequívoca.
2. **"No especificado" en Response Measure (secciones 3 y 26)** — La abundancia de "No especificado" en las medidas no es un defecto: el enunciado no fija valores y la skill los conservó sin inventar métricas, manteniendo el estado del atributo coherente con la evidencia.
3. **Manejo de ambigüedades (secciones 7 a 9, 28 y 32)** — Las tres ambigüedades se resolvieron mostrando ambas alternativas y construyendo escenarios para cada una.
