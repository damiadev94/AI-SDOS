# ARCHITECTURE_INDEX

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

The Architecture Index is the single navigable entry point for all architecture documentation in AI-SDOS.

Its purpose is to let any reader — regardless of background — understand what architecture documentation exists, where to find it, how the views relate to each other, and which views to read for a given purpose.

This document does not duplicate content from other architecture documents. It indexes and organizes them.

*(Source: TASK-ARCH-010)*

---

# 2. Architecture Views Inventory

| Document | Location | Purpose | View Type / C4 Level | Depends On |
|---|---|---|---|---|
| architecture-overview.md | `docs/architecture/` | High-level orientation to the platform — major subsystems, architectural vision, design principles, information flow summary | Architecture Overview (pre-C4) | Foundational docs |
| system-context.md | `docs/architecture/` | System boundary, human actors, external systems, high-level interactions | C4 Level 1 — System Context | architecture-overview.md |
| container-architecture.md | `docs/architecture/` | Major runtime containers, responsibilities, relationships, data ownership | C4 Level 2 — Container | system-context.md |
| component-architecture.md | `docs/architecture/` | Internal components of each container, responsibilities, dependencies, dependency rules | C4 Level 3 — Component | container-architecture.md |
| domain-architecture.md | `docs/architecture/` | Bounded contexts, aggregates, domain services, context relationships, context-to-container mapping | Domain Architecture (DDD) | container-architecture.md |
| information-flow.md | `docs/architecture/` | Primary information flows, Knowledge Repository centrality, governance intersections | Behavioral — Information Flow | component-architecture.md |
| agent-integration.md | `docs/architecture/` | Specialized Agent catalog, assignment model, context consumption, tool invocation, output lifecycle | Behavioral — Agent Integration | component-architecture.md |
| sequence-architecture.md | `docs/architecture/` | Key operational sequences with temporal ordering, participant interactions, governance gates | Behavioral — Sequence | information-flow.md |
| deployment-architecture.md | `docs/architecture/` | Logical deployment environments, container-to-environment mapping, constraints, known gaps | C4 Deployment View | container-architecture.md |
| decision-traceability.md | `docs/architecture/` | Extracted architectural decisions, ADR template, decision dependency map, known gaps | Governance — Decision Traceability | All architecture views |
| architecture-validation.md | `docs/architecture/` | Validation of all architecture documentation against acceptance criteria, consistency check, overall outcome | Governance — Validation | All architecture views |

---

# 3. Diagram Inventory

| File | Location | Associated View | Diagram Type |
|---|---|---|---|
| architecture-overview.html | `docs/architecture/diagrams/` | architecture-overview.md | HTML/SVG (DDS Framework) |
| system-context.mmd | `docs/architecture/diagrams/` | system-context.md | Mermaid — Graph LR |
| container-architecture.mmd | `docs/architecture/diagrams/` | container-architecture.md | Mermaid — Graph LR |
| component-architecture.mmd | `docs/architecture/diagrams/` | component-architecture.md | Mermaid — Graph LR |
| domain-architecture.mmd | `docs/architecture/diagrams/` | domain-architecture.md | Mermaid — Graph LR |
| information-flow.mmd | `docs/architecture/diagrams/` | information-flow.md | Mermaid — Flowchart LR |
| agent-integration.mmd | `docs/architecture/diagrams/` | agent-integration.md | Mermaid — Graph LR |
| deployment-architecture.mmd | `docs/architecture/diagrams/` | deployment-architecture.md | Mermaid — Graph LR |
| seq-001-documentation-generation.mmd | `docs/architecture/diagrams/sequences/` | sequence-architecture.md | Mermaid — sequenceDiagram |
| seq-002-architecture-view-generation.mmd | `docs/architecture/diagrams/sequences/` | sequence-architecture.md | Mermaid — sequenceDiagram |
| seq-003-specification-creation.mmd | `docs/architecture/diagrams/sequences/` | sequence-architecture.md | Mermaid — sequenceDiagram |
| seq-004-agent-task-execution.mmd | `docs/architecture/diagrams/sequences/` | sequence-architecture.md | Mermaid — sequenceDiagram |

---

# 4. ADR Inventory

**Status: No ADRs exist yet.**

As recorded in PROJECT_STATE.md, architectural decisions made so far are documented narratively in SYSTEM_ARCHITECTURE.md rather than as discrete ADRs. This is a known gap.

The decision-traceability.md document catalogs these narrative decisions and provides the ADR template for future formal records.

When ADRs are created, they will be stored in `docs/architecture/adrs/` and listed here.

| ADR ID | Title | Status | Date |
|---|---|---|---|
| — | *No ADRs exist yet* | — | — |

---

# 5. View Dependency Map

Architecture views must be read in dependency order. The following dependency chain applies:

```
Foundational Documents
(PROJECT_STATE · FOUNDATION · DOMAIN_DISCOVERY · UBIQUITOUS_LANGUAGE · DOMAIN_MODEL · SYSTEM_ARCHITECTURE)
    ↓
architecture-overview.md
    ↓
system-context.md
    ↓
container-architecture.md
    ↓
component-architecture.md          domain-architecture.md
    ↓                                       ↓
information-flow.md ◄──────────────────────┘
    ↓
agent-integration.md
    ↓
sequence-architecture.md
    ↓
deployment-architecture.md
    ↓
decision-traceability.md
    ↓
architecture-validation.md
```

**Notes:**
* domain-architecture.md depends on container-architecture.md (context-to-container mapping).
* information-flow.md benefits from both component-architecture.md and domain-architecture.md.
* deployment-architecture.md depends primarily on container-architecture.md.
* decision-traceability.md and architecture-validation.md are governance views that require all prior views to exist.

---

# 6. Reading Guide

---

## For a First-Time Reader

**Goal:** Understand what AI-SDOS is and how it is organized.

1. [architecture-overview.md](architecture-overview.md) — start here for the big picture.
2. [system-context.md](system-context.md) — understand who uses the platform and what it connects to.
3. [container-architecture.md](container-architecture.md) — understand the major structural units.
4. [domain-architecture.md](domain-architecture.md) — understand the domain concepts and responsibilities.

---

## For a Project Architect

**Goal:** Understand structural organization, decisions, and governance.

1. [architecture-overview.md](architecture-overview.md)
2. [system-context.md](system-context.md)
3. [container-architecture.md](container-architecture.md)
4. [component-architecture.md](component-architecture.md)
5. [decision-traceability.md](decision-traceability.md)
6. [architecture-validation.md](architecture-validation.md)

---

## For a Software Engineer

**Goal:** Understand where code fits, what components exist, and how to implement from specifications.

1. [architecture-overview.md](architecture-overview.md)
2. [container-architecture.md](container-architecture.md)
3. [component-architecture.md](component-architecture.md)
4. [agent-integration.md](agent-integration.md)
5. [sequence-architecture.md](sequence-architecture.md)

---

## For a New Contributor

**Goal:** Orient to the project, its knowledge model, and its architecture.

1. [architecture-overview.md](architecture-overview.md)
2. [domain-architecture.md](domain-architecture.md)
3. [system-context.md](system-context.md)
4. [information-flow.md](information-flow.md)
5. [architecture-index.md](architecture-index.md) (this document — revisit to navigate)

---

# 7. Documentation Maturity

| Document | Status | Version | Notes |
|---|---|---|---|
| architecture-overview.md | Complete | v0.1 | Initial version |
| system-context.md | Complete | v0.1 | Initial version |
| container-architecture.md | Complete | v0.1 | Initial version |
| component-architecture.md | Complete | v0.1 | Initial version |
| domain-architecture.md | Complete | v0.1 | Initial version |
| information-flow.md | Complete | v0.1 | Initial version |
| agent-integration.md | Complete | v0.1 | Initial version |
| sequence-architecture.md | Complete | v0.1 | 4 key sequences documented |
| deployment-architecture.md | Complete (conceptual) | v0.1 | Infrastructure decisions pending ADRs |
| decision-traceability.md | Complete | v0.1 | No formal ADRs yet — narrative decisions extracted |
| architecture-validation.md | Complete | v0.1 | Initial validation report |
| ADRs | Not started | — | Known gap — see decision-traceability.md |

**Overall phase status:** Architecture Views phase — Substantially Complete.

The architecture documentation covers all required C4 levels (System Context, Container, Component, Deployment), all behavioral views (Information Flow, Agent Integration, Sequences), the Domain Architecture, and the governance views (Decision Traceability, Validation). Remaining work is captured as known gaps in deployment-architecture.md and decision-traceability.md.

---

# Related Documents

* PROJECT_STATE.md
* All documents listed in the Architecture Views Inventory above.

---

# Change Log

| Version | Date       | Description                                                   |
| ------- | ---------- | ------------------------------------------------------------- |
| v0.1    | 2026-07-05 | Initial Architecture Index. Covers all TASK-ARCH-001 through TASK-ARCH-011 outputs. |
