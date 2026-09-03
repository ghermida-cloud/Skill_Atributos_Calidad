# General Scenarios — Atributos de calidad

Este archivo contiene los **General Scenarios** de los diez atributos de calidad de la "A list" de *Software Architecture in Practice, 4th Edition* (secciones 15 a 24 de la skill).

Es la **única referencia de validación** para construir (Modo 1), verificar (Modo 2) y priorizar escenarios (Modo 3).

Para cada escenario concreto se debe consultar el General Scenario del atributo correspondiente y particularizarlo al sistema analizado, siguiendo la **Regla de fidelidad a las tablas** (sección 14) y la **Convención para personalizar escenarios** (sección 13) de la skill principal.

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

No asumir que "seguridad" en lenguaje natural equivale automáticamente a Security.

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
