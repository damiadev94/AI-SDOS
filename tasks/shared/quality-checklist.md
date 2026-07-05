# Quality Checklist

## Propósito

Este documento establece el proceso oficial de validación para todas las Tasks ejecutadas dentro de AI-SDOS.

Su objetivo es garantizar que cualquier artefacto producido cumpla los estándares de calidad del proyecto antes de incorporarse a la documentación oficial.

Toda Task deberá completar esta validación antes de marcarse como finalizada.

---

# Alcance

Este checklist aplica a:

* Documentation Tasks
* Diagram Tasks
* Validation Tasks
* Cualquier otro tipo de Task definido en el sistema

---

# Principios

La validación deberá verificar que el resultado sea:

* correcto;
* consistente;
* completo;
* reutilizable;
* mantenible;
* reproducible.

El cumplimiento de una Task no depende únicamente de que el artefacto exista, sino de que satisfaga todos los criterios definidos.

---

# 1. Documentación

Verificar:

* □ Se utilizaron únicamente documentos oficiales como fuente.
* □ La jerarquía de fuentes fue respetada.
* □ No se introdujo información no documentada.
* □ No existen contradicciones con la documentación vigente.
* □ Se utilizó correctamente el Lenguaje Ubicuo.
* □ El alcance coincide con el objetivo de la Task.

---

# 2. Arquitectura

Verificar:

* □ No se modificaron decisiones arquitectónicas.
* □ El resultado refleja fielmente la arquitectura existente.
* □ No se agregaron conceptos nuevos.
* □ Se respetaron las ADRs existentes.
* □ Se mantuvo la coherencia con el resto del proyecto.

---

# 3. DDS

Verificar:

* □ Se reutilizaron exclusivamente Design Tokens.
* □ Se utilizaron únicamente Components oficiales.
* □ Se reutilizaron Patterns existentes.
* □ Se utilizaron Templates oficiales.
* □ Se utilizó la Diagram Library cuando correspondía.
* □ No se crearon componentes nuevos.

---

# 4. Diagramas

Aplicar únicamente cuando la Task genere documentación gráfica.

Verificar:

* □ Se seleccionó el tipo de diagrama adecuado.
* □ El diagrama responde una única pregunta arquitectónica.
* □ Los conectores representan relaciones reales.
* □ La organización visual es clara.
* □ Existen leyendas cuando son necesarias.
* □ Las notas agregan información útil.
* □ El diagrama puede comprenderse sin explicación adicional.

---

# 5. Calidad técnica

Verificar:

* □ HTML válido.
* □ SVG válido (cuando corresponda).
* □ Sin JavaScript.
* □ Sin estilos inline.
* □ Sin dependencias externas.
* □ Compatible con impresión A4.
* □ Diseño responsive.

---

# 6. Consistencia

Verificar:

* □ La terminología es uniforme.
* □ Los nombres son consistentes.
* □ No existen duplicaciones.
* □ El estilo coincide con el resto de la documentación.
* □ El resultado mantiene coherencia visual con el DDS.

---

# 7. Completitud

Verificar:

* □ Se generaron todos los artefactos esperados.
* □ No existen secciones incompletas.
* □ No existen marcadores temporales ("TODO", "FIXME", etc.).
* □ El contenido responde completamente al objetivo de la Task.

---

# 8. Trazabilidad

Verificar:

* □ Es posible identificar la documentación utilizada.
* □ Las decisiones están justificadas.
* □ El artefacto puede mantenerse en el tiempo.
* □ El resultado puede reproducirse ejecutando nuevamente la misma Task.

---

# Resultado de la validación

Toda Task deberá finalizar con uno de los siguientes estados.

## Completed

Todos los criterios obligatorios fueron cumplidos.

No existen observaciones relevantes.

---

## Completed with Warnings

La Task fue completada correctamente.

Existen observaciones menores que no afectan el resultado.

Todas las advertencias deberán documentarse.

---

## Requires Human Review

La Task produjo un resultado válido, pero existen decisiones o inconsistencias que requieren revisión humana antes de incorporarlo al proyecto.

---

## Blocked

La Task no puede completarse debido a:

* documentación insuficiente;
* contradicciones;
* dependencias faltantes;
* decisiones arquitectónicas pendientes.

La ejecución deberá detenerse hasta resolver el problema.

---

# Acciones ante incumplimientos

Cuando un criterio obligatorio no se cumpla, la Task deberá:

1. identificar el criterio afectado;
2. describir el problema;
3. indicar el impacto;
4. proponer la acción necesaria para resolverlo;
5. asignar el estado correspondiente.

Nunca deberá ignorar un incumplimiento.

---

# Criterios de aceptación

Una Task podrá considerarse finalizada únicamente cuando:

* todos los criterios obligatorios hayan sido evaluados;
* el estado final haya sido asignado correctamente;
* el resultado sea consistente con la documentación existente;
* el artefacto pueda incorporarse al proyecto sin modificaciones adicionales.

---

# Evolución

Este checklist constituye el estándar oficial de validación de AI-SDOS.

Toda nueva categoría de Task deberá utilizar este documento como base para su proceso de revisión.

Si en el futuro se incorporan nuevos tipos de artefactos o nuevas capacidades al sistema, este checklist podrá ampliarse manteniendo siempre la compatibilidad con los criterios existentes.
