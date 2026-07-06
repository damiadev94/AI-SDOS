# AI-SDOS

**AI Software Development Operating System** — un sistema operativo documental para el desarrollo de software asistido por IA.

Este repositorio contiene el conocimiento del proyecto: documentación fundacional, vistas de arquitectura, y las Tasks que producen esos artefactos. AI-SDOS sigue el principio *Documentation First*: la documentación precede y gobierna la implementación.

---

## Dónde está cada cosa

| Carpeta | Contenido |
|---|---|
| [`docs/`](docs/README.md) | Documentación fundacional del proyecto (Foundation, Domain Model, Ubiquitous Language, etc.) y las vistas de arquitectura en `docs/architecture/`. |
| [`tasks/`](tasks/README.md) | Unidades de trabajo ejecutables que producen los artefactos de `docs/`, junto con las reglas compartidas y templates que deben cumplir. |
| [`assets/`](assets/README.md) | Design Tokens y estilos CSS reutilizados por los diagramas HTML del Documentation Framework. |

---

## Documentation Framework

Este proyecto utiliza **AI-SDOS-DDS** (ubicado en `../AI-SDOS-DDS`, sibling repo) como framework oficial para la producción documental. Ver [`documentation-framework.md`](documentation-framework.md) para el detalle de qué provee ese framework.

Toda documentación se produce mediante las Tasks definidas en [`tasks/`](tasks/README.md), que reutilizan:

- Documentation Rules
- Diagram Rules
- Output Format
- Quality Checklist
- Templates
- Diagram Library

definidos en AI-SDOS-DDS.

---

## Por dónde empezar a leer

1. [`docs/PROJECT_STATE.md`](docs/PROJECT_STATE.md) — fase actual del proyecto y roadmap.
2. [`docs/FOUNDATION.md`](docs/FOUNDATION.md) — por qué existe AI-SDOS.
3. [`docs/architecture/architecture-index.md`](docs/architecture/architecture-index.md) — punto de entrada navegable a toda la documentación de arquitectura.
