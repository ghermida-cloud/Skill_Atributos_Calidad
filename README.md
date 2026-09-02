# Introduccion:

se pretende crear una Skill para agentes Ia que permita cumplir con lo siguiente:

En base a las experiencias anteriores y al material bibliográfico disponible, desarrolle una o
más skills (estilo Claude) para: i) generar atributos de calidad de acuerdo con los templates
de 6 partes del SEI, ii) chequear si un escenario dado está completo, y en caso de no estarlo
cómo podría completarse, y iii) elaborar un árbol de utilidad. Tener en cuenta que la skill debe
ser testeada con ejemplos conocidos.

# Trazabilidad o evolución del proyecto:

1. Se creo y perfeccionó la skill inical de creacion de escencarios respetando un formato presciso, informando de inferesncias y siendo completamente fiel a la bibliografía.

2. Se acondiciono para poder ser utilizada en opencode y se agregaron dos nuevos modos a la skill:
    1. description del frontmatter ahora dispara la skill también para verificación/corrección y árbol de utilidad (y lo corregí con comillas porque el YAML fallaba con los :).
    2. Tabla de "Modos de operación" tras el Propósito: qué pide el usuario da qué modo y a qué secciones va.
    3. Sección 33 — Modo 2 (Verificar y corregir): procedimiento de 8 pasos, 10 tipos de error codificados (E1–E10), formato de salida (veredicto, tabla de errores, escenario corregido, checklist) y reglas (no inventar para corregir, preservar trazabilidad).
    4. Sección 34 — Modo 3 (Árbol de utilidad): definición anclada a la bibliografía (sección 19.4 y cap. 20 ADD), estructura Utility → atributo → preocupación → escenario, priorización (Importancia, Dificultad) H/M/L durante consulta a fuentes, formato ASCII del árbol + tabla de escenarios, y reglas de fidelidad (las prioridades no son dato del enunciado).

    Los tres modos reusan transparencia, estados de atributos y fidelidad a los General Scenarios, por lo que se decide implementar los tres en una misma skill, habria que mejorar organizacion.

3. Al ver que quedo un archivo skill.me demasiado grande se trabajara en organizar y repartir las tareas dentro de la skill. (por ej, separar la parte de escenarios de cada atributo a otro archivo que sea usado como referencia solo cuando sea necesario).