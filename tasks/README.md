# Tasks

## Propósito

Las **Tasks** son unidades de trabajo ejecutables utilizadas para producir artefactos de documentación dentro de AI-SDOS.

A diferencia de las **SPEC**, cuyo objetivo es construir o modificar el sistema, una Task utiliza la infraestructura existente para generar contenido.

Las Tasks permiten transformar conocimiento previamente definido en documentación consistente, reutilizable y verificable.

---

# Filosofía

El sistema de Tasks sigue los mismos principios que el resto del proyecto:

* Documentation as Code
* Specs First
* Single Source of Truth
* Reproducibility
* Human in the Loop
* Consistency over Convenience
* Reuse Before Creation

Toda Task debe producir resultados determinísticos a partir de la documentación existente.

---

# Relación con las SPEC

Las SPEC y las Tasks cumplen responsabilidades diferentes y complementarias.

| SPEC                      | TASK                                     |
| ------------------------- | ---------------------------------------- |
| Construye infraestructura | Produce artefactos                       |
| Implementa código         | Genera documentación                     |
| Modifica el sistema       | Utiliza el sistema                       |
| Vive en AI-SDOS-DDS       | Vive en AI-SDOS                          |
| Su resultado es software  | Su resultado es conocimiento documentado |

Las Tasks nunca implementan funcionalidades.

Las SPEC nunca generan documentación del proyecto.

---

# Relación con AI-SDOS-DDS

Las Tasks consumen el Design Documentation System (DDS).

El DDS proporciona:

* Design Tokens
* Components
* Patterns
* Diagram Framework
* Diagram Library
* Templates
* Export System

Las Tasks utilizan estos elementos para producir documentación sin modificar el framework.

---

# Objetivos

El sistema de Tasks busca:

* estandarizar la producción documental;
* garantizar consistencia visual y conceptual;
* evitar duplicación de criterios;
* facilitar la ejecución por personas o agentes de IA;
* producir documentación reproducible;
* mantener una única fuente de verdad.

---

# Arquitectura

```text
Knowledge
        ↓
Task
        ↓
Analysis
        ↓
Documentation
        ↓
Validation
        ↓
Artifact
```

Las Tasks representan la capa de ejecución entre el conocimiento del proyecto y los artefactos finales.

---

# Ciclo de vida

Toda Task sigue el mismo flujo de trabajo:

1. Leer la documentación requerida.
2. Validar la consistencia de la información.
3. Identificar el objetivo del artefacto.
4. Aplicar las reglas compartidas.
5. Generar el resultado.
6. Validar el resultado.
7. Entregar los archivos finales.

Si durante el proceso existe información insuficiente o contradictoria, la Task debe detenerse e informar el problema antes de continuar.

---

# Estructura del directorio

```text
tasks/
│
├── README.md
│
├── shared/
│   ├── documentation-rules.md
│   ├── diagram-rules.md
│   ├── output-format.md
│   └── quality-checklist.md
│
├── templates/
│   └── task-template.md
│
├── architecture/
│   ├── structure/     (TASK-ARCH-001, 002, 003, 009)
│   ├── behavior/       (TASK-ARCH-006, 007, 008)
│   ├── domain/          (TASK-ARCH-005)
│   ├── decision/        (TASK-ARCH-011)
│   └── governance/      (TASK-ARCH-010, 012)
│
├── diagrams/     (reservado — Diagram Tasks futuras que no pertenezcan a una categoría existente)
│
├── documents/    (reservado — Documentation Tasks futuras que no pertenezcan a una categoría existente)
│
└── validation/   (reservado — Validation Tasks futuras que no pertenezcan a una categoría existente)
```

`architecture/` es, por ahora, la única categoría de Tasks del proyecto y se subdivide internamente por sub-dominio arquitectónico (`structure`, `behavior`, `domain`, `decision`, `governance`) en lugar de por tipo de artefacto, porque esa subdivisión refleja mejor las dependencias entre vistas (ver `docs/architecture/architecture-index.md`, sección 5). `diagrams/`, `documents/` y `validation/` quedan reservadas para cuando exista una categoría de Tasks fuera de `architecture/` (por ejemplo, Domain Discovery o Specification) que no amerite su propia subcarpeta por sub-dominio.

---

# Tipos de Tasks

## Documentation Tasks

Generan documentos técnicos.

Ejemplos:

* Foundation
* Domain Discovery
* Ubiquitous Language
* Domain Model
* ADR
* Glossary

---

## Diagram Tasks

Generan documentación gráfica.

Ejemplos:

* Context Diagram
* Container Diagram
* Component Diagram
* Sequence Diagram
* Event Flow
* Roadmap
* Timeline

---

## Validation Tasks

Verifican la calidad y consistencia de la documentación existente.

Ejemplos:

* Terminology Review
* Documentation Consistency
* Broken References
* Diagram Validation

---

# Reglas generales

Toda Task debe:

* respetar la documentación existente;
* reutilizar el DDS sin modificarlo;
* utilizar únicamente componentes oficiales;
* mantener consistencia terminológica;
* producir resultados reproducibles;
* seguir el formato de salida oficial;
* completar la validación antes de finalizar.

Una Task nunca debe:

* inventar información;
* modificar decisiones arquitectónicas;
* crear componentes nuevos del DDS;
* alterar Design Tokens;
* cambiar Templates oficiales;
* ignorar contradicciones documentales.

---

# Dependencias compartidas

Todas las Tasks deben utilizar los documentos ubicados en `shared/`.

Estos documentos contienen las reglas comunes del sistema y constituyen la fuente de verdad para:

* producción documental;
* producción gráfica;
* formato de salida;
* validación de calidad.

Las Tasks específicas deben referenciar estas reglas en lugar de duplicarlas.

---

# Plantillas

Toda nueva Task deberá crearse utilizando la plantilla oficial ubicada en:

```text
tasks/templates/task-template.md
```

Esto garantiza una estructura uniforme y facilita la automatización futura.

---

# Convenciones

* Una Task debe tener una única responsabilidad.
* Cada archivo debe producir un único artefacto principal.
* Las Tasks deben ser idempotentes: ejecutarlas múltiples veces con la misma entrada debe producir el mismo resultado.
* Los nombres deben ser descriptivos y utilizar *kebab-case*.
* Toda Task debe indicar claramente sus entradas, salidas y criterios de aceptación.

---

# Evolución

Las Tasks podrán ampliarse con nuevos tipos de producción documental a medida que evolucione AI-SDOS.

La incorporación de nuevas Tasks no deberá requerir modificaciones en el DDS, sino únicamente reutilizar las capacidades que este ya proporciona.

De este modo, el sistema mantiene una separación clara entre la infraestructura documental (AI-SDOS-DDS) y la producción de conocimiento (AI-SDOS).
