# docs

Documentación del proyecto AI-SDOS. Dos niveles con convenciones de nombre distintas y deliberadas:

## Documentos fundacionales (raíz de `docs/`, `MAYÚSCULAS_CON_GUION_BAJO.md`)

La base de conocimiento del proyecto, en orden de jerarquía de fuentes (ver `tasks/shared/documentation-rules.md`):

1. [`PROJECT_STATE.md`](PROJECT_STATE.md) — fase actual, objetivos, roadmap.
2. [`FOUNDATION.md`](FOUNDATION.md) — propósito, visión, principios.
3. [`DOMAIN_DISCOVERY.md`](DOMAIN_DISCOVERY.md) — dominio, stakeholders, workflows.
4. [`UBIQUITOUS_LANGUAGE.md`](UBIQUITOUS_LANGUAGE.md) — vocabulario compartido y autoritativo.
5. [`DOMAIN_MODEL.md`](DOMAIN_MODEL.md) — modelo conceptual del dominio.
6. [`SYSTEM_ARCHITECTURE.md`](SYSTEM_ARCHITECTURE.md) — organización estructural del sistema.

## Vistas de arquitectura (`architecture/`, `kebab-case.md`)

Artefactos generados a partir de los documentos fundacionales por las Tasks en `tasks/architecture/`. Punto de entrada: [`architecture/architecture-index.md`](architecture/README.md).

## Material histórico (`legacy/`)

Insumos previos al framework DDS actual, conservados solo como referencia. Ver [`legacy/README.md`](legacy/README.md).

---

Ambas convenciones de nombre (MAYÚSCULAS para lo fundacional, kebab-case para las vistas generadas) se mantienen intencionalmente distintas y no deben mezclarse: distinguen a simple vista un documento fuente de un artefacto derivado.
