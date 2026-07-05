# Output Format

## Propósito

Este documento define el formato oficial de salida para todas las Tasks de AI-SDOS.

Su objetivo es garantizar que todos los artefactos generados mantengan una estructura uniforme, sean fácilmente revisables y puedan incorporarse al proyecto sin modificaciones adicionales.

Toda Task deberá entregar sus resultados siguiendo exactamente este formato.

---

# Principios

El formato de salida deberá ser:

* consistente;
* reproducible;
* verificable;
* fácilmente auditable;
* independiente del agente que ejecute la Task.

El contenido podrá variar según el objetivo de la Task, pero la estructura general deberá permanecer constante.

---

# Estructura general

Toda Task deberá entregar la información en el siguiente orden.

## 1. Task Summary

Resumen breve del objetivo de la Task.

Debe responder:

* ¿Qué se generó?
* ¿Para qué sirve?
* ¿Cuál es su alcance?

---

## 2. Inputs

Listado de toda la documentación utilizada.

Por ejemplo:

* Foundation
* Domain Discovery
* Ubiquitous Language
* Domain Model
* System Architecture
* ADRs

Si alguna fuente requerida no estuvo disponible, deberá indicarse explícitamente.

---

## 3. Analysis

Descripción del análisis realizado antes de generar el resultado.

Debe incluir:

* información relevante encontrada;
* conceptos involucrados;
* dependencias identificadas;
* restricciones detectadas;
* posibles inconsistencias.

---

## 4. Decisions

Listado de las decisiones tomadas durante la generación.

Cada decisión deberá estar respaldada por documentación existente.

No deberán existir decisiones arbitrarias.

---

## 5. Artifact Specification

Descripción estructurada del artefacto generado.

Dependiendo del tipo de Task podrá incluir:

* objetivo;
* tipo de documento;
* tipo de diagrama;
* estructura;
* secciones;
* nodos;
* relaciones;
* leyenda;
* notas.

Esta sección constituye la especificación del resultado antes de su implementación.

---

## 6. Generated Artifacts

Listado completo de los archivos generados.

Por ejemplo:

```text
docs/system-architecture.md

docs/diagrams/system-context.html

docs/diagrams/system-context.svg
```

Deberá indicarse claramente la ubicación de cada archivo.

---

## 7. Implementation

Contenido final del artefacto.

Dependiendo de la Task podrá incluir:

* Markdown
* HTML
* SVG
* CSS (cuando corresponda)

No deberá incluir archivos ajenos al alcance de la Task.

---

## 8. Validation

Resultado de la validación realizada.

Deberá verificarse:

* consistencia documental;
* cumplimiento de las reglas compartidas;
* reutilización del DDS;
* cumplimiento del alcance;
* ausencia de contradicciones.

Toda validación deberá ser explícita.

---

## 9. Issues

Listado de problemas encontrados durante la ejecución.

Ejemplos:

* documentación incompleta;
* referencias inexistentes;
* contradicciones;
* dependencias pendientes.

Si no existen problemas, deberá indicarse explícitamente.

---

## 10. Completion Status

Estado final de la Task.

Valores posibles:

* Completed
* Completed with Warnings
* Blocked
* Requires Human Review

Toda Task deberá finalizar con uno de estos estados.

---

# Reglas

La salida deberá:

* seguir siempre el mismo orden;
* ser fácilmente legible;
* separar claramente análisis, decisiones e implementación;
* permitir auditoría posterior;
* facilitar futuras automatizaciones.

---

# Restricciones

Nunca:

* omitir secciones obligatorias;
* mezclar análisis con implementación;
* ocultar problemas detectados;
* asumir información no documentada;
* marcar una Task como completada cuando existan bloqueos críticos.

---

# Adaptación por tipo de Task

Algunas secciones podrán variar en profundidad según el objetivo.

Ejemplos:

## Documentation Task

Mayor énfasis en:

* estructura documental;
* contenido generado;
* referencias.

---

## Diagram Task

Mayor énfasis en:

* especificación gráfica;
* nodos;
* relaciones;
* HTML;
* SVG.

---

## Validation Task

Mayor énfasis en:

* hallazgos;
* inconsistencias;
* recomendaciones;
* estado de cumplimiento.

La estructura general permanecerá inalterada.

---

# Criterios de aceptación

Una salida cumple este estándar cuando:

* respeta completamente la estructura definida;
* identifica claramente entradas y salidas;
* documenta las decisiones tomadas;
* entrega los artefactos generados;
* registra los problemas encontrados;
* informa correctamente el estado final de la Task.

---

# Evolución

Este documento constituye el estándar oficial de salida para todas las Tasks de AI-SDOS.

Las nuevas categorías de Tasks deberán adaptar sus contenidos a esta estructura sin modificar su organización general.

De esta forma, cualquier resultado generado por una Task mantiene un formato uniforme, independientemente del agente o herramienta que lo produzca.
