# Análisis de Atributos de Calidad — Sistema de Pagos de una Universidad

**Modos aplicados:** Modo 2 (verificación y corrección de escenarios) + Modo 3 (árbol de utilidad)
**Fuente:** *Software Architecture in Practice, 4th Edition* — General Scenarios de los atributos de calidad.
**Regla de transparencia:** dato del enunciado / dato de la bibliografía / [INFERENCIA] / No especificado.

> **Nota de re-ejecución:** este análisis se genera con la skill corregida. Cambios aplicados respecto de la ejecución anterior: la prioridad **no se asigna H por el solo "debe"** (sección 34.3); se distingue dato explícito / reformulación válida / métrica inventada (sección 26.1 y E8); y el Artifact de Availability no se sobre-adapta al "pago" (sección 34.2).

---

## 0. Contexto y datos de partida

### Datos del enunciado

- Sistema de pagos de una universidad.
- Los estudiantes pagan **matrículas** y **otros conceptos** mediante **tarjeta** o **transferencia bancaria**.
- "Las operaciones **deben ser seguras**."
- "Durante el **período de inscripción** se espera una **gran cantidad de usuarios concurrentes**."

### Requisitos del enunciado

| # | Requisito | Interpretación preliminar |
|---|---|---|
| 1 | Un estudiante debe poder realizar un pago. | Requisito funcional |
| 2 | El sistema debe procesar los pagos **rápidamente**. | Performance |
| 3 | Las transacciones deben estar **protegidas contra accesos no autorizados**. | Security |
| 4 | Si un servidor **falla** durante una operación, el pago **no debe perderse**. | Availability |
| 5 | El sistema debe poder **incorporar un nuevo proveedor de pagos** en el futuro. | Integrability |
| 6 | Las nuevas versiones deben poder **desplegarse sin afectar** a los estudiantes que están realizando pagos. | Deployability |
| 7 | Los **administradores** deben poder **ejecutar pruebas** sobre el sistema antes de cada entrega. | Testability |

---

## 1. Requerimientos funcionales

- RF1 — Un estudiante debe poder realizar un pago (requisito 1). "Qué debe hacer" el sistema; es la base funcional sobre la que recaen los atributos de calidad.

---

## 2. Atributos de calidad confirmados

| Atributo | Evidencia del enunciado | Justificación |
|---|---|---|
| Performance | Requisito 2: "debe procesar los pagos rápidamente". Contexto: gran cantidad de usuarios concurrentes durante la inscripción. | Restricción temporal sobre el procesamiento de pagos. |
| Security | Contexto: "Las operaciones deben ser seguras". Requisito 3: "las transacciones deben estar protegidas contra accesos no autorizados". | Protección de datos/servicios frente a accesos no autorizados. |
| Availability | Requisito 4: "Si un servidor falla durante una operación, el pago no debe perderse". | Respuesta ante un fault (falla del servidor) conservando el servicio. |
| Integrability | Requisito 5: "debe poder incorporar un nuevo proveedor de pagos en el futuro". | Integración de un nuevo elemento (proveedor) al sistema. |
| Deployability | Requisito 6: "las nuevas versiones deben poder desplegarse sin afectar a los estudiantes que están realizando pagos". | Despliegue de nuevas versiones sin interrumpir a los usuarios. |
| Testability | Requisito 7: "los administradores deben poder ejecutar pruebas sobre el sistema antes de cada entrega". | Ejecución de pruebas por parte de administradores. |

**Nota:** El requisito 7 (Testability) es un atributo confirmado del enunciado, aunque no figura entre los cinco escenarios propuestos para verificar. Se incluye en el árbol de utilidad porque es un escenario confirmado del sistema.

---

## 3. Atributos de calidad posibles

No se detectaron atributos con pista razonable insuficiente para confirmar que merezcan clasificación como POSIBLE en el alcance de este enunciado. Los seis atributos confirmados cubren los requisitos de calidad expresados.

---

## 4. Ambigüedades entre atributos

### 4.1. Disponibilidad (Availability) vs. Protección de integridad de datos

| Aspecto | Availability | Security (integridad) |
|---|---|---|
| Evidencia del enunciado | Req. 4: "Si un servidor falla durante una operación, el pago no debe perderse". | Req. 3: "las transacciones deben estar protegidas contra accesos no autorizados". |
| Qué representa | Respuesta ante la **falla** de un servidor conservando el pago (no perderlo). | Protección de los datos de la transacción frente a accesos **no autorizados**. |
| Correspondencia bibliográfica | GS Availability: fault (crash), detectar/recuperarse, mantener servicio. | GS Security: ataque/intento no autorizado, proteger integridad. |
| Especificidad contextual | El estímulo es una **falla del servidor**, propio de Availability. | La amenaza es un **acceso no autorizado**, propio de Security. |
| Conclusión | No hay conflicto real: el requisito 4 habla de **falla** (Availability); el requisito 3 de **acceso no autorizado** (Security). Son estímulos distintos. Ambos escenarios se mantienen. | |

### 4.2. Deployability vs. Availability para el requisito 6

| Aspecto | Deployability | Availability |
|---|---|---|
| Evidencia del enunciado | "Las nuevas versiones deben poder desplegarse sin afectar a los estudiantes que están realizando pagos". | El fragmento "sin afectar a los estudiantes que están realizando pagos" podría leerse como continuidad de servicio. |
| Qué representa | Despliegue de una **nueva versión** (nuevo elemento) sin interrumpir a los usuarios. | Mantener el servicio disponible. |
| Correspondencia bibliográfica | GS Deployability: desplegar nuevo elemento/versión, medida incluye "efectos sobre otros atributos"/"deployments fallidos". | GS Availability: continuar funcionando. |
| Especificidad contextual | El estímulo es la **nueva versión** y el foco es **no afectar a los estudiantes durante el despliegue**. Deployability es más específico: su Response Measure contempla explícitamente los efectos sobre los usuarios durante el despliegue. | |
| Conclusión | **Deployability** es el atributo más específico para el requisito 6. La continuidad de servicio se manifiesta aquí como **ausencia de interrupción al desplegar**, no como un fault que deba recuperarse. Se adopta Deployability. | |

---

# PARTE A — MODO 2: VERIFICACIÓN Y CORRECCIÓN DE ESCENARIOS

---

## A.1 Escenario A — Performance

### Veredicto

**PARCIALMENTE CORRECTO.** Las seis partes están presentes y correctamente etiquetadas, pero la Response Measure **inventa un valor** ("menos de 2 segundos") que el enunciado no establece.

### 1.1 Análisis de ambigüedad

| Aspecto | Performance | Alternativa |
|---|---|---|
| Evidencia del enunciado | Req. 2: "debe procesar los pagos rápidamente". | — |
| Correspondencia bibliográfica | GS Performance: respuesta a un evento, medida de latency/deadline. | — |
| Especificidad contextual | El requisito pide **rapidez en procesamiento**; es una restricción temporal clara. | No se identifica otra alternativa defendible. |
| Estado / conclusión | Sin ambigüedad relevante. El Environment "alta concurrencia" toma sustento del contexto ("gran cantidad de usuarios concurrentes" durante la inscripción). | |

### 2. Errores encontrados

| # | Parte | Código | Problema | Corrección |
|---|---|---|---|---|
| 1 | Response Measure | E4 / E8 | Se inventó "menos de 2 segundos"; el enunciado solo dice "rápidamente". | "No especificado" + [INFERENCIA] valor posible. |

### 3. Escenario corregido

| Parte | Escenario concreto |
|---|---|
| Stimulus Source | Estudiante (**user**) |
| Stimulus | Realiza un pago (**llegada de un evento / solicitud**) |
| Artifact | Sistema de pagos (**system**) |
| Environment | Alta concurrencia (**peak load**) |
| Response | Procesa el pago (**procesar el evento y responder**) |
| Response Measure | **No especificado** (**latency / deadline**). [INFERENCIA] Posible valor: un tiempo de procesamiento del pago dentro de un intervalo breve, sin que la concurrencia degrade la respuesta. |

**Justificación:** El enunciado exige procesar los pagos "rápidamente" (requisito 2) y el entorno de alta concurrencia surge del contexto (gran cantidad de usuarios concurrentes durante la inscripción). El enunciado **no fija un valor numérico**, por lo que "menos de 2 segundos" es inventado y se reemplaza por "No especificado".

---

## A.2 Escenario B — Security

### Veredicto

**PARCIALMENTE CORRECTO.** La estructura y las seis partes están bien, pero el **Artifact** ("base de datos") y la **Response Measure** ("100% de los ataques") son datos inventados no presentes en el enunciado.

### 1.1 Análisis de ambigüedad

| Aspecto | Security | Alternativa |
|---|---|---|
| Evidencia del enunciado | Contexto: "las operaciones deben ser seguras". Req. 3: "las transacciones deben estar protegidas contra accesos no autorizados". | Safety (solo una "seguridad" ambigua) |
| Correspondencia bibliográfica | GS Security: intento no autorizado de acceder a datos, proteger confidentiality/integrity. | GS Safety: evitar estados inseguros por fallas. |
| Especificidad contextual | La amenaza es un **acceso no autorizado** a una transacción → **Security**. No hay evidencia de estado inseguro por falla → Safety se descarta. | |
| Estado / conclusión | **Security** es el atributo específico. No hay ambigüedad pendiente de resolver. | |

### 2. Errores encontrados

| # | Parte | Código | Problema | Corrección |
|---|---|---|---|---|
| 1 | Artifact | E4 | "Base de datos" no está en el enunciado; el requisito protege "las transacciones". | Artifact = "las transacciones (datos)". |
| 2 | Response Measure | E4 / E8 | "100% de los ataques" es inventado; el enunciado no fija medida. | "No especificado" + [INFERENCIA]. |
| 3 | Environment | E6 | "Operación normal" no está explícito; conviene marcarlo. | Mantener "No especificado" con [INFERENCIA] posible "operación normal / fully operational". |

### 3. Escenario corregido

| Parte | Escenario concreto |
|---|---|
| Stimulus Source | Atacante (**human**) |
| Stimulus | Intenta acceder a una transacción sin autorización (**intento no autorizado de acceder a datos**) |
| Artifact | Las transacciones (**datos**) |
| Environment | **No especificado**. [INFERENCIA] Posible valor: operación normal / fully operational. |
| Response | Rechazar el acceso (**resistir y proteger la confidentiality/integrity**) |
| Response Measure | **No especificado** (**ataques resistidos**). [INFERENCIA] Posible valor: todos los accesos no autorizados rechazados. |

**Justificación:** El requisito 3 protege "las transacciones contra accesos no autorizados". El enunciado **no menciona base de datos** como artifact ni fija una **medida** ("100%"). Ambos valores se eliminan; el artifact pasa a ser las transacciones y la medida queda como "No especificado".

---

## A.3 Escenario C — Availability

### Veredicto

**PARCIALMENTE CORRECTO.** La Response Measure ("99,99% de disponibilidad") es **inventada** y la Response ("continuar funcionando") se aleja del requisito concreto ("el pago no debe perderse"). El Artifact, en cambio, **no se corrige** hacia "el pago": el "pago" describe la Response, y el Artifact sigue siendo el sistema afectado por el fault (sección 34.2).

### 1.1 Análisis de ambigüedad

| Aspecto | Availability | Alternativa |
|---|---|---|
| Evidencia del enunciado | Req. 4: "Si un servidor falla durante una operación, el pago no debe perderse". | Security (integridad) — ver sección 4.1. |
| Correspondencia bibliográfica | GS Availability: fault (crash), detectar/recuperarse, continuar conforme a especificación. | GS Security: acceso no autorizado. |
| Especificidad contextual | El estímulo es una **falla del servidor**; el requisito es de **recuperación/conservación**, propio de Availability. | La amenaza de acceso no autorizado pertenece a otro requisito (3). |
| Estado / conclusión | **Availability** es el atributo específico. La ambigüedad con Security se resuelve en la sección 4.1: son requisitos distintos. | |

### 2. Errores encontrados

| # | Parte | Código | Problema | Corrección |
|---|---|---|---|---|
| 1 | Response | E7 | "Continuar funcionando" no captura lo específico del requisito ("el pago no debe perderse"). | Response = "el pago no se pierde / la operación se recupera sin pérdida". |
| 2 | Response Measure | E4 / E8 | "99,99% de disponibilidad" es inventado; el enunciado no fija porcentaje. | "No especificado" + [INFERENCIA]. |
| 3 | Artifact | — | El propuesto ("sistema") era correcto. **No se sobre-adapta al "pago"**: el pago expresa la Response, no el Artifact (sección 34.2, regla 3). | Se mantiene "sistema / parte del sistema afectada por el fault (procesos de pago)". |

### 3. Escenario corregido

| Parte | Escenario concreto |
|---|---|
| Stimulus Source | Servidor (**fuente de un fault**) |
| Stimulus | Falla durante una operación (**crash / fault**) |
| Artifact | El sistema / la parte del sistema que procesa pagos (**parte del sistema afectada por el fault**) |
| Environment | Durante una operación de pago (**normal operation**) |
| Response | El pago no se pierde; la operación se recupera sin pérdida (**recuperarse / continuar conforme a la especificación**) |
| Response Measure | **No especificado** (**tiempo/intervalo de recuperación, porcentaje de disponibilidad**). [INFERENCIA] Posible valor: cero pagos perdidos ante la falla de un servidor. |

**Justificación:** El requisito 4 establece que ante la falla de un servidor "el pago no debe perderse". Esa es la **Response** correcta. El **Artifact** es el sistema (la parte afectada por el fault); el "pago" describe qué es lo que no debe perderse (Response). El enunciado **no fija 99,99%**, por lo que la medida se marca "No especificado".

---

## A.4 Escenario D — Integrability

### Veredicto

**PARCIALMENTE CORRECTO.** La Response Measure ("un día de trabajo") es **inventada**; también conviene revisar la Stimulus Source (el enunciado no la declara).

### 1.1 Análisis de ambigüedad

| Aspecto | Integrability | Modifiability |
|---|---|---|
| Evidencia del enunciado | Req. 5: "debe poder incorporar un nuevo proveedor de pagos en el futuro". | El cambio podría leerse como una modificación general del sistema. |
| Correspondencia bibliográfica | GS Integrability: agregar/integrar un componente; environment development/integration/deployment/runtime. | GS Modifiability: cambios del sistema y su costo/impacto. |
| Especificidad contextual | El foco es **integrar/incorporar un nuevo elemento** (proveedor) al sistema. Integrability es más específico. | Modifiability queda como preocupación general del cambio. |
| Estado / conclusión | **Integrability** es el atributo más específico (cátedra: preocupación de desarrollo/integración). El libro además admite environment "development". | |

### 2. Errores encontrados

| # | Parte | Código | Problema | Corrección |
|---|---|---|---|---|
| 1 | Stimulus Source | E4 / E6 | El enunciado no declara quién inicia; "equipo de desarrollo" es inferencia. | Marcar [INFERENCIA]; la fuente bibliográfica del elemento integrado es el proveedor (component vendor). |
| 2 | Response Measure | E4 / E8 | "Un día de trabajo" es inventado; el enunciado no fija tiempo/esfuerzo. | "No especificado" (tiempo/esfuerzo de integración) + [INFERENCIA]. |

### 3. Escenario corregido

| Parte | Escenario concreto |
|---|---|
| Stimulus Source | **No especificado**. [INFERENCIA] Posible valor: el nuevo proveedor de pagos (**component vendor**) / el equipo de desarrollo. |
| Stimulus | Incorporar un nuevo proveedor de pagos (**agregar/integrar un componente**) |
| Artifact | Sistema de pagos (**sistema completo / conjunto de componentes**) |
| Environment | Desarrollo (**development**) |
| Response | Integrar el proveedor y lograr la colaboración correcta con el sistema (**integrar, probar, desplegar y lograr el intercambio correcto**) |
| Response Measure | **No especificado** (**costo / esfuerzo / tiempo de integración**). [INFERENCIA] Posible valor: integrar el nuevo proveedor con un tiempo/esfuerzo acotado. |

**Justificación:** El requisito 5 exige incorporar un nuevo proveedor de pagos en el futuro. El enunciado **no fija una duración** ("un día de trabajo" es inventado), por lo que la medida queda "No especificado". La fuente de integración tampoco está declarada.

---

## A.5 Escenario E — Deployability

### Veredicto

**PARCIALMENTE CORRECTO.** La Response Measure estaba presentada como "cero interrupciones". Con la regla 26.1 corregida, "cero interrupciones" es una **reformulación válida** de "sin afectar a los estudiantes" y no una métrica cuantitativa inventada; no debe tratársela como invención problemática. El Environment "producción" no está explícito.

### 1.1 Análisis de ambigüedad

| Aspecto | Deployability | Availability |
|---|---|---|
| Evidencia del enunciado | Req. 6: "las nuevas versiones deben poder desplegarse sin afectar a los estudiantes que están realizando pagos". | "sin afectar a los estudiantes" como continuidad de servicio. |
| Correspondencia bibliográfica | GS Deployability: desplegar nueva versión; medida incluye efectos sobre otros atributos/users. | GS Availability: continuar funcionando. |
| Especificidad contextual | El foco es el **despliegue de una nueva versión** sin afectar a los usuarios. Deployability es más específico (ver sección 4.2). | La continuidad aquí se manifiesta como ausencia de interrupción al desplegar, no como recuperación de un fault. |
| Estado / conclusión | **Deployability** es el atributo más específico. No es una falla que recuperar, sino una operación de despliegue no disruptiva. | |

### 2. Errores encontrados

| # | Parte | Código | Problema | Corrección |
|---|---|---|---|---|
| 1 | Environment | E6 / [INFERENCIA] | "Producción" no está explícito en el enunciado. | Conservar "No especificado"; [INFERENCIA] posible valor "producción" (los estudiantes realizan pagos en operación). |
| 2 | Response Measure | — | "Cero interrupciones" NO es invención: es una reformulación válida de "sin afectar a los estudiantes" (sección 26.1). No se elimina ni se trata como métrica inventada. | Se mantiene como reformulación del requisito (no como umbral numérico "0 segundos"). |

### 3. Escenario corregido

| Parte | Escenario concreto |
|---|---|
| Stimulus Source | Administrador (**system administrator**) |
| Stimulus | Desplegar una nueva versión (**disponibilidad/solicitud de deployment de un nuevo elemento o versión**) |
| Artifact | Sistema (**system / entorno**) |
| Environment | **No especificado**. [INFERENCIA] Posible valor: producción (**production**), ya que la operación afecta a estudiantes realizando pagos. |
| Response | Desplegar la nueva versión sin afectar a los estudiantes que están realizando pagos (**desplegar el elemento**) |
| Response Measure | Sin interrupción de los pagos en curso (**reformulación válida** de "sin afectar a los estudiantes") / No especificado como métrica formal (**efectos sobre otros atributos / deployments fallidos**). No es "0 segundos" ni "100%", que sí serían invención. |

**Justificación:** El requisito 6 exige desplegar nuevas versiones sin afectar a los estudiantes que realizan pagos. "Sin interrupción de los pagos en curso" es una **reformulación fiel** del requisito (no una métrica cuantitativa inventada). El "producción" como environment se marca como inferencia.

---

# PARTE B — MODO 3: ÁRBOL DE UTILIDAD

**Regla de prioridad (sección 34.3 corregida):** "debe" **no** implica importancia H. La importancia solo se asigna H/M/L con indicación explícita de criticidad/impacto en el enunciado. Al no haberla específicamente por atributo, la importancia se marca **No especificado**.

> **Análisis de criticidad del enunciado:** El enunciado dice "Las operaciones **deben ser seguras**" y menciona "gran cantidad de usuarios concurrentes" durante la inscripción. El contexto legitima que **Security** tenga importancia **H** (la frase "deben ser seguras" + contexto de concurrencia, vinculado a riesgos de seguridad) — aunque en rigor es una lectura del contexto. Para el resto de los atributos no hay indicación explícita de criticidad diferencial, por lo que la importancia es **No especificado**. La **dificultad** es **No especificado** en todas las hojas (el enunciado no describe complejidad técnica).

---

## 1. Árbol de utilidad

```
UTILITY
├── Performance
│   └── Procesamiento rápido de pagos
│       └── (No especificado, No especificado) Escenario A — Pago procesado en alta concurrencia
├── Security
│   └── Protección de transacciones
│       └── (H, No especificado) Escenario B — Acceso no autorizado rechazado
├── Availability
│   └── Falla de servidor
│       └── (No especificado, No especificado) Escenario C — Pago no se pierde ante falla del servidor
├── Integrability
│   └── Nuevo proveedor de pagos
│       └── (No especificado, No especificado) Escenario D — Integración de nuevo proveedor
├── Deployability
│   └── Despliegue de nuevas versiones
│       └── (No especificado, No especificado) Escenario E — Despliegue sin afectar pagos en curso
└── Testability
    └── Pruebas antes de cada entrega
        └── (No especificado, No especificado) Escenario F — Administradores ejecutan pruebas
```

## 2. Tabla de escenarios priorizados

| Atributo | Preocupación | Prioridad (Imp., Df.) | Escenario (seis partes) | Justificación |
|---|---|---|---|---|
| Performance | Procesamiento rápido de pagos | (No esp., No esp.) | **Source:** estudiante (user). **Stimulus:** realiza un pago (evento/solicitud). **Artifact:** sistema de pagos (system). **Environment:** alta concurrencia (peak load). **Response:** procesa el pago (procesar y responder). **Measure:** No especificado (latency). [INF.] tiempo breve. | Requisito 2 ("rápidamente") + contexto de concurrencia. |
| Security | Protección de transacciones | (H, No esp.) | **Source:** atacante (human). **Stimulus:** intento no autorizado de acceder a una transacción (acceso no autorizado a datos). **Artifact:** las transacciones (datos). **Environment:** No especificado. [INF.] operación normal (fully operational). **Response:** rechazar el acceso (resistir/proteger). **Measure:** No especificado. [INF.] todos los accesos no autorizados rechazados. | Contexto "las operaciones deben ser seguras" + requisito 3. |
| Availability | Falla de servidor | (No esp., No esp.) | **Source:** servidor (fuente de fault). **Stimulus:** falla durante una operación (crash/fault). **Artifact:** el sistema / parte del sistema que procesa pagos (parte del sistema afectada por el fault). **Environment:** durante una operación de pago (normal operation). **Response:** el pago no se pierde; se recupera (recuperarse). **Measure:** No especificado. [INF.] cero pagos perdidos. | Requisito 4 ("el pago no debe perderse"). |
| Integrability | Nuevo proveedor de pagos | (No esp., No esp.) | **Source:** No especificado. [INF.] nuevo proveedor (component vendor). **Stimulus:** incorporar un nuevo proveedor (agregar componente). **Artifact:** sistema de pagos (sistema/subconjunto). **Environment:** desarrollo (development). **Response:** integrar el proveedor (integrar y lograr colaboración). **Measure:** No especificado (tiempo/costo de integración). | Requisito 5 ("incorporar un nuevo proveedor"). |
| Deployability | Despliegue de nuevas versiones | (No esp., No esp.) | **Source:** administrador (system administrator). **Stimulus:** desplegar una nueva versión (deployment de nueva versión). **Artifact:** sistema (system). **Environment:** No especificado. [INF.] producción (production). **Response:** desplegar sin afectar a los estudiantes que realizan pagos (desplegar). **Measure:** sin interrupción de los pagos en curso (reformulación válida). | Requisito 6 ("desplegarse sin afectar a los estudiantes"). |
| Testability | Pruebas antes de cada entrega | (No esp., No esp.) | **Source:** administrador (system administrator / tester). **Stimulus:** inicio de pruebas antes de cada entrega (inicio de un test). **Artifact:** sistema (sistema completo / infraestructura de testing). **Environment:** antes de cada entrega (contexto de desarrollo/release). **Response:** ejecutar las pruebas y revelar faults (ejecutar, capturar resultados, detectar faults). **Measure:** No especificado (esfuerzo/cobertura/probabilidad de revelar fault). | Requisito 7 ("ejecutar pruebas ... antes de cada entrega"). |

## 3. Justificación de prioridades

**Performance (Escenario A)**
- **Importancia No especificado:** El enunciado dice "debe procesar los pagos rápidamente" (obligatorio), pero **no** indica criticidad diferencial ni impacto para el negocio más allá de la obligatoriedad. El contexto de concurrencia podría sugerir importancia, pero no establece un vínculo explícito con la prioridad de este atributo. Faltaría una indicación de criticidad/impacto para asignar H/M/L.
- **Dificultad No especificado:** El enunciado no describe la complejidad técnica de lograr el procesamiento rápido.

**Security (Escenario B)**
- **Importancia H:** El contexto declara "las operaciones deben ser seguras" y el requisito 3 es explícito ("deben estar protegidas contra accesos no autorizados"), en un sistema que maneja transacciones de pago con gran cantidad de usuarios concurrentes. La protección de transacciones financieras es el propósito de seguridad central explícito del sistema; se lee criticidad explícita de negocio. (Este H se apoya en esa lectura del contexto; si se considera que el enunciado no la hace explícita, la importancia sería No especificado.)
- **Dificultad No especificado:** El enunciado no describe la complejidad técnica de proteger las transacciones.

**Availability (Escenario C)**
- **Importancia No especificado:** El requisito 4 es obligatorio ("el pago no debe perderse"), pero el enunciado no indica criticidad diferencial de este atributo frente a los demás. Faltaría una indicación explícita de impacto para asignar H/M/L.
- **Dificultad No especificado:** El enunciado no describe la complejidad técnica de no perder pagos ante la falla del servidor.

**Integrability (Escenario D)**
- **Importancia No especificado:** El requisito 5 es obligatorio ("debe poder incorporar un nuevo proveedor"), pero sin indicación explícita de criticidad/impacto en el enunciado. Faltaría una indicación para asignar H/M/L.
- **Dificultad No especificado:** El enunciado no describe la complejidad técnica de integrar un nuevo proveedor.

**Deployability (Escenario E)**
- **Importancia No especificado:** El requisito 6 es obligatorio ("deben poder desplegarse sin afectar a los estudiantes"), pero sin indicación explícita de criticidad en el enunciado. Faltaría una indicación para asignar H/M/L.
- **Dificultad No especificado:** El enunciado no describe la complejidad técnica de desplegar sin afectar los pagos en curso.

**Testability (Escenario F)**
- **Importancia No especificado:** El requisito 7 es obligatorio ("los administradores deben poder ejecutar pruebas ... antes de cada entrega"), pero sin indicación explícita de criticidad en el enunciado. Faltaría una indicación para asignar H/M/L.
- **Dificultad No especificado:** El enunciado no describe la complejidad técnica de ejecutar las pruebas.

---

## 4. Checklist final

- [x] Comprendí el contexto del sistema de pagos.
- [x] Separé funcionalidad (RF1) de atributos de calidad.
- [x] Cada atributo confirmado tiene evidencia del enunciado.
- [x] Distinguí dato del enunciado, dato de la bibliografía e [INFERENCIA].
- [x] Marqué datos faltantes como "No especificado".
- [x] No inventé métricas: "menos de 2 segundos", "100% de los ataques", "99,99% de disponibilidad" y "un día de trabajo" fueron detectados y corregidos.
- [x] Distinguí dato explícito / reformulación válida / métrica inventada (sección 26.1): "sin interrupción de los pagos en curso" se conservó como reformulación válida del requisito 6, no como métrica inventada.
- [x] Verifiqué las seis partes de cada escenario contra su General Scenario.
- [x] No sobre-adapté el Artifact de Availability: "el pago" describe la Response; el Artifact es el sistema/parte del sistema afectada por el fault (sección 34.2, regla 3).
- [x] Usé la convención de paréntesis (opción/valor bibliográfico, no el nombre de la parte).
- [x] Analicé ambigüedades (Availability/Security en sec. 4.1; Deployability/Availability en sec. 4.2).
- [x] Construí el árbol de utilidad con todos los escenarios confirmados.
- [x] **No asigné prioridad H por el solo "debe".** La importancia es H solo para Security (apoyada en el contexto "deben ser seguras") y **No especificado** para el resto. La dificultad es "No especificado" en todas las hojas.
