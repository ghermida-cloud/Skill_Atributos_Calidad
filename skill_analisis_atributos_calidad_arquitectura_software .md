# Skill — Análisis de Atributos de Calidad a Nivel de Arquitectura de Software

## Propósito

Esta skill define cómo analizar un enunciado de un sistema de software a nivel de **Arquitectura de Software**, para distinguir requerimientos funcionales de requisitos de atributos de calidad, identificar atributos confirmados y posibles, resolver ambigüedades y construir **Quality Attribute Scenarios** fieles a *Software Architecture in Practice, 4th Edition*.

La cadena de trazabilidad debe ser:

**ENUNCIADO → EVIDENCIA → ATRIBUTO → JUSTIFICACIÓN → GENERAL SCENARIO → CONCRETE SCENARIO**

No clasificar por palabras aisladas ni inventar información.

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

La inferencia **no reemplaza** a “No especificado”. Ambos deben aparecer cuando corresponda:

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

Ejemplo: “rápido” puede sugerir Performance, pero debe analizarse qué debe ser rápido y por qué. “Seguro” puede corresponder a Security o Safety según el significado del requisito.

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

> “El sistema debe comprobar la seguridad en menos de 2 segundos.”

**Performance:** evidencia = “menos de 2 segundos”. Hay una restricción temporal explícita.

**Security:** evidencia = “comprobar la seguridad”. El objetivo de la operación está relacionado con seguridad.

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

# 10. “Afectar” no significa “ser requisito”

Que un atributo pueda verse afectado por una decisión no significa que el enunciado lo exija.

Por ejemplo, Security puede afectar Performance. Eso no convierte automáticamente Performance en requisito.

Distinguir:

> “Esto podría afectar Performance.”

vs.

> “El enunciado exige Performance.”

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

“Persona mayor” es el dato específico del sistema y “end user” es la opción/valor bibliográfico que corresponde a **Stimulus Source**.

Otro ejemplo:

> **Artifact:** Módulo de autenticación (**component**)

“Módulo de autenticación” es el dato específico del sistema y “component” es la opción/valor bibliográfico correspondiente a **Artifact**.

No escribir:

> **Módulo de autenticación (artifact)**

si “artifact” solamente identifica cuál de las seis partes se está completando. En ese caso, **Artifact** es el encabezado y dentro de los paréntesis debe aparecer la opción/valor que el libro propone para esa parte.

Esta convención se aplica consistentemente a las seis partes.

---

# 14. Regla de fidelidad a las tablas

Para construir cada escenario:

1. consultar el General Scenario del atributo en el libro;
2. mantener sus seis partes;
3. conservar el significado de sus categorías;
4. utilizar las posibles opciones del libro como guía;
5. particularizar únicamente con información del enunciado;
6. si falta información, escribir “No especificado” y, cuando el contexto permita una posible interpretación útil, agregar también **[INFERENCIA] Posible valor: ...** sin reemplazar el “No especificado”;
7. no inventar métricas ni condiciones.

La personalización puede hacer el escenario más claro y contextualizado, pero nunca debe reemplazar ni deformar la estructura de la bibliografía.

---

# 15. General Scenario — Availability

### Stimulus Source

Fuentes como personas, hardware, software, infraestructura física u otras fuentes internas/externas de faults.

### Stimulus

Un fault, incluyendo omission, crash, incorrect timing o incorrect response.

### Artifact

La parte del sistema afectada por el fault, por ejemplo procesadores, canales de comunicación, almacenamiento o procesos.

### Environment

Estados como normal operation, startup, shutdown, repair mode, degraded operation u overloaded operation.

### Response

Detectar, prevenir o recuperarse del fault; informar; registrar; reparar/enmascarar; continuar en modo degradado o realizar otra respuesta apropiada para mantener el servicio conforme a su especificación.

### Response Measure

Medidas de disponibilidad, tiempo/intervalo de disponibilidad, tiempo de detección o recuperación, o porcentaje de disponibilidad cuando corresponda.

---

# 16. General Scenario — Deployability

### Stimulus Source

Por ejemplo: developer, system administrator, operations personnel, product owner o fuente de un nuevo elemento/componente.

### Stimulus

Disponibilidad o solicitud de deployment de un nuevo elemento, versión, corrección, security patch, upgrade o rollback.

### Artifact

Componentes, módulos, plataforma, entorno, sistema o elementos que deban desplegarse.

### Environment

Por ejemplo staging o production, o un subconjunto controlado de estos.

### Response

Incorporar, desplegar, monitorear o hacer rollback del elemento.

### Response Measure

Tiempo, esfuerzo, costo, defectos introducidos, efectos sobre otros atributos y/o deployments fallidos, según lo que exija el escenario.

---

# 17. General Scenario — Energy Efficiency

Este atributo trata el uso eficiente de recursos computacionales para controlar el consumo de energía manteniendo la funcionalidad y las restricciones relevantes.

### Stimulus Source

Actor o agente que inicia la necesidad de gestionar/conservar energía.

### Stimulus

Solicitud o necesidad de modificar la utilización de recursos para conservar energía.

### Artifact

Recursos computacionales/dispositivos relevantes para el consumo.

### Environment

Runtime y condiciones relevantes, como dispositivos alimentados por batería o modos de conservación.

### Response

Monitorear consumo, asignar/liberar recursos, adaptar el uso de recursos o reducir consumo manteniendo el nivel requerido de funcionalidad.

### Response Measure

Consumo/energía utilizada, energía ahorrada, tiempo de funcionamiento u otra medida explícita del escenario.

No inventar un valor numérico.

---

# 18. General Scenario — Integrability

### Stimulus Source

Por ejemplo stakeholder, component marketplace, component vendor u otra fuente del elemento que se integrará.

### Stimulus

Agregar un componente, integrar una nueva versión o integrar componentes existentes de una nueva manera.

### Artifact

Sistema completo, conjunto de componentes, componente, configuración o elementos afectados.

### Environment

Development, integration, deployment o runtime, según corresponda.

### Response

Integrar, probar, desplegar y lograr la colaboración/intercambio correcto entre los elementos.

### Response Measure

Costo, esfuerzo o tiempo de integración y, cuando corresponda, número de componentes afectados, cantidad de cambios o efectos sobre otros atributos.

---

# 19. General Scenario — Modifiability

### Stimulus Source

Por ejemplo developer, end user, system administrator, product line owner u otro actor que solicita el cambio.

### Stimulus

Agregar, eliminar o modificar funcionalidad; cambiar un atributo de calidad; cambiar capacidad, plataforma, tecnología o ubicación de un servicio; agregar un producto; corregir un defecto, etc.

### Artifact

El artifact que debe modificarse: datos, interfaces, componentes, recursos, configuraciones, documentación, tests u otras partes del sistema.

### Environment

Design time, build time, compile time, initiation time o runtime, según corresponda.

### Response

Realizar, probar y desplegar/adaptar la modificación.

### Response Measure

Costo del cambio: cantidad/tamaño/complejidad de artifacts afectados, esfuerzo, tiempo, dinero, efectos sobre funciones/qualities, defectos introducidos, etc.

---

# 20. General Scenario — Performance

### Stimulus Source

Puede ser un usuario, múltiples usuarios, un sistema externo, un sensor u otra parte del sistema; también un timer para estímulos internos.

### Stimulus

Llegada de un evento: periódico, esporádico o estocástico. Puede ser una solicitud o una notificación.

### Artifact

Todo el sistema o una parte/componente del sistema.

### Environment

Normal mode, emergency mode, error correction mode, peak load, overload, degraded operation u otro modo pertinente.

### Response

Procesar el evento y responder; devolver un error; no responder; ignorar solicitudes bajo overload; cambiar modo/nivel de servicio; atender eventos de mayor prioridad, etc., según el escenario.

### Response Measure

Latency, deadline, throughput, jitter, miss rate, porcentaje/número de solicitudes satisfechas/no satisfechas o utilización de recursos, según corresponda.

Si el enunciado proporciona una medida concreta, conservarla. Si no, no inventar un valor.

---

# 21. General Scenario — Safety

### Stimulus Source

Por ejemplo sensor, software component, communication channel, dispositivo/fuente temporal o acción del usuario.

### Stimulus

Omission, commission, incorrect data o incorrect timing que pueda conducir a un estado inseguro.

### Artifact

Partes safety-critical del sistema.

### Environment

Normal operation, degraded operation o manual operation.

### Response

Prevenir un unsafe state, recuperarse, continuar de forma segura/degradada, realizar shutdown/fail safe, pasar a operación manual, cambiar a backup y/o reportar/loguear el estado inseguro.

### Response Measure

Cantidad/porcentaje de estados inseguros evitados o recuperables, reducción de exposición al riesgo, tiempo de transición a/desde modos seguros/degradados, tiempo apagado, etc.

### Distinción Safety vs Security

**Safety:** evitar daño o estados inseguros derivados del comportamiento/fallas del sistema.

**Security:** proteger datos, servicios y recursos frente a accesos o acciones no autorizadas/ataques.

No asumir que “seguridad” en lenguaje natural equivale automáticamente a Security.

---

# 22. General Scenario — Security

### Stimulus Source

Human o another system; puede estar dentro/fuera de la organización y ser conocido o desconocido.

### Stimulus

Ataque o intento no autorizado de visualizar, capturar, cambiar/eliminar datos, acceder a servicios, modificar comportamiento o reducir disponibilidad.

### Artifact

Servicios, datos, componentes, recursos o datos producidos/consumidos por el sistema.

### Environment

Online/offline, conectado/desconectado de la red, detrás de firewall/abierto a red, fully operational, partially operational o not operational, según corresponda.

### Response

Detectar, resistir y responder al ataque; proteger confidentiality, integrity y availability; identificar actores; registrar accesos/modificaciones/intentos; notificar; recuperar.

### Response Measure

Recursos comprometidos/asegurados, precisión de detección, tiempo hasta detectar, ataques resistidos, tiempo de recuperación o datos vulnerables, según el escenario.

---

# 23. General Scenario — Testability

### Stimulus Source

Unit testers, integration testers, system testers, acceptance testers, end users o herramientas de testing automatizadas.

### Stimulus

Inicio de un test o conjunto de tests para validar funciones/qualities o descubrir amenazas a la calidad.

### Artifact

La parte del sistema y la infraestructura necesaria para probarla: unidad, componente, subsistema, sistema completo o infraestructura de testing.

### Environment

Contexto de desarrollo/testing, por ejemplo después de completar un incremento, integrar un subsistema, completar la implementación, desplegar o entregar al cliente.

### Response

Ejecutar tests, capturar resultados, observar/controlar el estado y detectar/revelar faults.

### Response Measure

Esfuerzo para descubrir faults, cobertura, probabilidad de revelar un fault, tiempo de ejecución, tiempo/esfuerzo de preparación de infraestructura o reducción de risk exposure.

---

# 24. General Scenario — Usability

### Stimulus Source

Principalmente end user o end user en un rol especializado, como administrator.

### Stimulus

El usuario quiere usar el sistema eficientemente, aprender a utilizarlo, minimizar el impacto de errores, adaptar el sistema o configurarlo.

### Artifact

Por ejemplo GUI, command-line interface, voice interface, touch screen u otra interfaz pertinente.

### Environment

At runtime o at system configuration time, según corresponda.

### Response

Proporcionar las funcionalidades necesarias, anticipar necesidades, proporcionar feedback apropiado o permitir la interacción requerida.

### Response Measure

Task time, number of errors, learning time, relación learning time/task time, number of tasks accomplished, user satisfaction u otra medida respaldada por el escenario.

---

# 25. Cómo construir un Concrete Quality Attribute Scenario

Para cada atributo:

1. localizar su General Scenario en el libro;
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

> “rápidamente”

mantener:

> **No especificado**

y, si el contexto permite proponer una posible interpretación razonable:

> **[INFERENCIA] Posible valor: un tiempo de respuesta reducido / una respuesta dentro de un intervalo breve.**

La inferencia debe dejar claro que el enunciado no fija una medida concreta.

No convertir arbitrariamente “rápidamente” en “menos de 2 segundos”.

Si el enunciado dice:

> “menos de 2 segundos”

sí utilizar:

> **menos de 2 segundos**

como dato explícito.

Si la bibliografía indica una clase de medida pero el enunciado no da un valor:

> **No especificado (opción/medida bibliográfica correspondiente)**

y, cuando el contexto permita una interpretación razonable:

> **[INFERENCIA] Posible valor: ...**

Nunca presentar esa inferencia como si fuera un requisito explícito.

---

# 27. Justificación de atributos

## CONFIRMADO

**Atributo:** ...

**Estado:** CONFIRMADO

**Evidencia del enunciado:** “...”

**Correspondencia bibliográfica:** ...

**Justificación:** ...

## POSIBLE

**Atributo:** ...

**Estado:** POSIBLE

**Evidencia:** “...”

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
| ... | “...” | ... |

## 3. Atributos de calidad posibles

| Atributo | Evidencia | Por qué podría corresponder | Qué falta para confirmarlo |
|---|---|---|---|
| ... | “...” | ... | ... |

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
- [ ] Cuando fue útil, agregué una posible interpretación marcada como **[INFERENCIA]**, sin reemplazar “No especificado”.
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

### Ambigüedad

- [ ] Mostré ambos atributos cuando ambos son defendibles.
- [ ] Justifiqué cada uno.
- [ ] Comparé cuál es más específico.
- [ ] Construí ambos escenarios si ninguno podía descartarse.

---

# 31. Regla de oro

> **No inventar. No sobreinterpretar. No clasificar por palabras aisladas. Analizar en contexto. Mostrar las alternativas razonables. Priorizar el atributo más específico cuando la evidencia lo permita. Mantener las alternativas cuando continúen siendo defendibles. Seguir la estructura del General Scenario de la bibliografía. Marcar toda inferencia. Y conservar siempre la trazabilidad entre el enunciado, la bibliografía y el escenario.**

# 32. Distinciones y comparaciones entre atributos de calidad

Esta sección agrega distinciones útiles para resolver casos grises entre atributos. **No modifica la definición ni el procedimiento de las secciones anteriores**. Su función es servir como guía comparativa cuando dos conceptos puedan confundirse.

Cuando una distinción provenga del libro, indicarlo como **[BIBLIOGRAFÍA]**. Cuando corresponda específicamente a una explicación, criterio o convención de la cátedra y no a un atributo de la “A list” del libro, indicarlo como **[CÁTEDRA / CLASE]**. Si una explicación es una interpretación nuestra, marcarla como **[INFERENCIA]**.

---

## 32.1 Integrability vs. Modifiability

**[BIBLIOGRAFÍA]** El libro trata **Integrability** y **Modifiability** como atributos distintos dentro de su “A list”, y presenta Integrability específicamente alrededor de la integración de elementos. La relación entre ambos debe entenderse como una relación de alcance: la integración es un tipo particular de cambio/preocupación arquitectónica, pero el requisito puede estar expresando específicamente integración.

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

> “el sistema debe poder modificarse fácilmente”

→ **Modifiability**.

Si dice:

> “debe poder integrarse un nuevo componente/sistema/elemento”

→ **Integrability** puede ser el atributo más específico.

Si el cambio consiste precisamente en integrar algo, pueden ser defendibles ambos:

- **Modifiability** → preocupación general por el cambio.
- **Integrability** → preocupación específica por la integración.

En ese caso, mostrar ambos, justificar ambos y explicar cuál es más específico para el enunciado.

---

## 32.2 Portability vs. Interoperability

### Estado respecto de la bibliografía

**[BIBLIOGRAFÍA]** En la 4.ª edición, **Portability** e **Interoperability** no forman parte de los diez atributos de la “A list” desarrollados individualmente en los capítulos 4–13. El libro las trata dentro de su discusión de **otras listas/modelos de atributos de calidad** en el capítulo 14. En particular, al presentar ISO/IEC 25010, menciona Portability e Interoperability como características/subcaracterísticas de ese modelo. citeturn1search2turn1search5

Por lo tanto, si la cátedra utiliza Portability e Interoperability como atributos para analizar ejercicios, deben distinguirse de los diez atributos principales de la skill.

**[CÁTEDRA / CLASE]** Si estos conceptos fueron presentados explícitamente por la cátedra como categorías para clasificar requisitos, utilizarlos como categorías de análisis, pero mantener esta aclaración de procedencia.

### Portability

**[BIBLIOGRAFÍA]** El libro reproduce la definición de ISO/IEC 25010 según la cual Portability se refiere al grado en que un sistema, producto o componente puede ser transferido entre distintos entornos de hardware, software u otros entornos operativos/de uso. citeturn1search2

Pregunta guía:

> **¿El sistema puede trasladarse/adaptarse para funcionar en otro entorno?**

Ejemplos de pistas:

- funcionar en distintos sistemas operativos;
- trasladarse a otra plataforma;
- funcionar en diferentes entornos de operación;
- poder mover un componente/sistema de un entorno a otro con el esfuerzo requerido.

**[INFERENCIA]** Decir simplemente “que el sistema se pueda usar en otro lugar” puede ser demasiado ambiguo: hay que comprobar que el requisito realmente implique transferencia entre entornos y no simplemente otro tipo de reutilización o configuración.

### Interoperability

**[BIBLIOGRAFÍA]** En ISO/IEC 25010, que el libro presenta en el capítulo 14, Interoperability aparece como una subcaracterística de **Compatibility**: se relaciona con la capacidad de sistemas/productos para intercambiar información y utilizar esa información intercambiada. citeturn1search2

Pregunta guía:

> **¿El sistema necesita intercambiar información o colaborar con otro sistema/producto?**

Por lo tanto, **no definir Interoperability como “que el mismo sistema tenga distintos usos”**. Ese ejemplo de las distintas pólizas para dólares/pesos, por sí solo, no demuestra interoperabilidad.

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

**[INFERENCIA]** La oposición “desarrollo vs. runtime” puede servir como pista muy útil para los ejercicios de la cátedra, pero no debe utilizarse como criterio absoluto para descartar Integrability: el propio libro contempla **runtime** como uno de sus posibles entornos.

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

**[BIBLIOGRAFÍA]** La 4.ª edición trata Safety y Security como atributos distintos y les dedica capítulos separados, con sus propios General Scenarios. citeturn0search1turn0search2

### Safety

Pregunta guía:

> **¿El comportamiento, fallo u operación del sistema puede llevar a un estado inseguro o causar daño, y qué debe hacer el sistema para evitarlo o recuperarse?**

El foco está en prevenir estados inseguros, recuperarse de ellos o mantener una operación segura/degradada. La skill ya debe utilizar para Safety las categorías del General Scenario del libro, como estados inseguros, operación degradada, fail-safe, backup, etc.

**Importante:** no reducir Safety a “cuidar plata o activos”.

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

Si el lenguaje del enunciado dice simplemente “seguridad”, **no decidir por la palabra aislada**. Aplicar la regla general de contexto de esta skill.

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
