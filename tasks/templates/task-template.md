# Task Template

## Objetivo

Describe de forma clara y concreta el propósito de la Task.

Debe responder:

* ¿Qué artefacto debe producirse?
* ¿Qué problema resuelve?
* ¿Cuál es el alcance de esta ejecución?

La Task debe tener una única responsabilidad.

---

# Tipo de Task

Indicar una de las siguientes categorías:

* Documentation Task
* Diagram Task
* Validation Task
* Analysis Task
* Review Task
* Migration Task
* Otro (especificar)

---

# Entradas requeridas

Enumerar toda la documentación necesaria para ejecutar correctamente la Task.

Ejemplo:

* Foundation
* Domain Discovery
* Ubiquitous Language
* Domain Model
* System Architecture
* ADRs
* Glossary

No deberá ejecutarse la Task si falta información crítica.

---

# Dependencias

Indicar otros artefactos que deban existir previamente.

Ejemplos:

* Documentation Rules
* Diagram Rules
* Output Format
* Quality Checklist
* Diagram Library
* Documentation Templates

---

# Artefactos de salida

Especificar exactamente qué archivos deberán generarse.

Ejemplo:

```text
docs/system-architecture.md

docs/diagrams/system-context.html

docs/diagrams/system-context.svg
```

Cada Task deberá generar únicamente los artefactos definidos en esta sección.

---

# Objetivos específicos

Describir los resultados esperados.

Ejemplo:

* representar correctamente la arquitectura;
* documentar el flujo de ejecución;
* visualizar las dependencias del sistema.

---

# Alcance

Describir claramente qué incluye la Task.

Todo aquello que no esté expresamente indicado se considera fuera de alcance.

---

# Fuera de alcance

Enumerar explícitamente aquello que esta Task no debe realizar.

Ejemplos:

* modificar documentación existente;
* cambiar la arquitectura;
* crear nuevos componentes del DDS;
* introducir decisiones no documentadas.

---

# Procedimiento

La ejecución deberá seguir el siguiente flujo:

## 1. Preparación

* identificar las entradas;
* verificar dependencias;
* validar disponibilidad de la documentación.

---

## 2. Análisis

* comprender el objetivo;
* identificar conceptos relevantes;
* detectar restricciones;
* identificar inconsistencias.

---

## 3. Diseño

Definir la estructura del artefacto antes de implementarlo.

Cuando corresponda:

* estructura documental;
* tipo de diagrama;
* nodos;
* relaciones;
* jerarquía;
* agrupaciones.

---

## 4. Implementación

Generar el artefacto utilizando exclusivamente:

* Design Tokens;
* Components;
* Patterns;
* Diagram Library;
* Templates oficiales.

---

## 5. Validación

Aplicar íntegramente el documento:

`tasks/shared/quality-checklist.md`

---

# Reglas obligatorias

La Task deberá cumplir:

* Documentation Rules
* Diagram Rules (cuando corresponda)
* Output Format
* Quality Checklist

No deberán duplicarse estas reglas dentro de la Task.

---

# Restricciones

Nunca:

* inventar información;
* asumir decisiones arquitectónicas;
* modificar el DDS;
* crear componentes nuevos;
* utilizar tecnologías no aprobadas;
* ignorar contradicciones documentales.

---

# Criterios de aceptación

La Task se considerará completada cuando:

* se hayan generado todos los artefactos definidos;
* se hayan respetado las reglas compartidas;
* el resultado haya superado la validación;
* el estado final sea **Completed** o **Completed with Warnings**.

---

# Estado final

La Task deberá finalizar con uno de los siguientes estados:

* Completed
* Completed with Warnings
* Requires Human Review
* Blocked

El estado deberá justificarse cuando no sea **Completed**.

---

# Observaciones

Registrar:

* limitaciones encontradas;
* decisiones pendientes;
* recomendaciones para futuras iteraciones;
* información que deba revisarse posteriormente.

---

# Historial

| Campo                | Valor |
| -------------------- | ----- |
| Task ID              |       |
| Versión              |       |
| Fecha de creación    |       |
| Última actualización |       |
| Autor                |       |
| Estado               |       |
| Artefactos generados |       |

---

# Plantilla mínima

Toda nueva Task deberá mantener, como mínimo, la siguiente estructura:

```text
Objetivo

Tipo de Task

Entradas requeridas

Dependencias

Artefactos de salida

Objetivos específicos

Alcance

Fuera de alcance

Procedimiento

Reglas obligatorias

Restricciones

Criterios de aceptación

Estado final

Observaciones

Historial
```

No deberán eliminarse secciones de esta plantilla. Si alguna no aplica, deberá indicarse explícitamente el motivo.
