# tasks/architecture

Las 12 Tasks que produjeron toda la documentación en `docs/architecture/`. Cada Task declara su ID (`TASK-ARCH-NNN`), sus entradas, sus dependencias y su artefacto de salida exacto — ver el estado de cumplimiento de cada una en [`docs/architecture/architecture-validation.md`](../../docs/architecture/architecture-validation.md).

Subdividida por sub-dominio arquitectónico, no por tipo de artefacto (ver [`tasks/README.md`](../README.md) para el porqué):

| Subcarpeta | Tasks | Vistas que produce |
|---|---|---|
| [`structure/`](structure/README.md) | TASK-ARCH-001, 002, 003, 004, 009 | Architecture Overview, System Context, Container, Component, Deployment |
| [`behavior/`](behavior/README.md) | TASK-ARCH-006, 007, 008 | Information Flow, Agent Integration, Sequence Architecture |
| [`domain/`](domain/README.md) | TASK-ARCH-005 | Domain Architecture |
| [`decision/`](decision/README.md) | TASK-ARCH-011 | Decision Traceability |
| [`governance/`](governance/README.md) | TASK-ARCH-010, 012 | Architecture Index, Architecture Validation |

Orden de lectura y dependencias entre vistas: [`docs/architecture/architecture-index.md`](../../docs/architecture/architecture-index.md), sección 5.
