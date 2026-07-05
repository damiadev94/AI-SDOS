# ARCHITECTURE_OVERVIEW

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

AI-SDOS exists to provide a structured, documentation-driven operating system for AI-assisted software development. It transforms ideas into well-defined software systems through explicit specifications, architectural discipline, and orchestrated AI collaboration, while preserving human control over strategic decisions.

This document gives a reader an understanding of the platform as a whole — its major subsystems, their responsibilities, and how information flows between them — before consulting lower-level documentation such as the Domain Model or System Architecture.

*(Source: FOUNDATION.md — Purpose)*

---

# 2. Architectural Vision

AI-SDOS is designed as a documentation-driven orchestration platform. The architecture prioritizes documentation before implementation, explicit engineering workflows, separation of responsibilities, modular evolution, traceable decision-making, and collaboration between humans and specialized AI agents.

AI-SDOS follows a layered and modular architectural style: independent architectural capabilities collaborate through well-defined responsibilities rather than direct implementation coupling.

*(Source: SYSTEM_ARCHITECTURE.md — Architectural Vision, Architectural Style)*

---

# 3. Design Principles

The architecture is guided by the Core Philosophy and Design Principles defined in FOUNDATION.md:

* **Documentation First** — knowledge must be documented before it is implemented.
* **Architecture Before Code** — architectural decisions precede implementation decisions.
* **Specifications Drive Development** — every implementation originates from explicit specifications.
* **Human in the Loop** — humans retain responsibility for strategic decisions, validation, and governance.
* **Explicit Decisions** — important decisions must be documented and traceable.
* **Knowledge as an Asset** — documentation is a long-term project asset.
* **Continuous Evolution** — documentation and architecture evolve incrementally while preserving consistency.

These principles are reinforced by the platform's design qualities: Documentation-driven, Modular, Extensible, Scalable, Traceable, Reproducible, Technology-agnostic, Tool-independent, Observable, Maintainable, Consistent, Simple where possible.

*(Source: FOUNDATION.md — Core Philosophy, Design Principles)*

---

# 4. High-Level Building Blocks

AI-SDOS is organized into seven architectural layers, each with a single, non-overlapping responsibility.

## Human Layer
Represents every human actor interacting with AI-SDOS. Defines objectives, approves strategic decisions, validates outcomes, provides domain knowledge, and governs project evolution. Remains the final authority for all strategic decisions.

## Orchestration Layer
Coordinates the execution of engineering Workflows: workflow orchestration, task scheduling, dependency management, execution sequencing, and coordination between Specialized Agents. Delegates rather than performs engineering work directly.

## Knowledge Layer
Maintains the project's authoritative Knowledge: Documentation, Specifications, architectural artifacts, Project State, ADRs, the Ubiquitous Language, and historical traceability. Acts as the platform's primary source of truth.

## AI Agent Layer
Provides specialized engineering capabilities through Specialized Agents dedicated to documentation, architecture, implementation, testing, analysis, review, and validation. Each agent owns a single responsibility and operates using the Knowledge Layer as its context. AI agents never become the authoritative source of project knowledge.

## Tool Integration Layer
Connects AI-SDOS with external capabilities — version control systems, documentation platforms, IDEs, issue trackers, CI/CD systems, MCP servers, and AI model providers — abstracting external dependencies from the core platform.

## Execution Layer
Transforms approved Specifications into executable project artifacts: implementation, documentation generation, diagram generation, validation, testing, and artifact production. Only validated work progresses beyond this layer.

## Governance Layer
Preserves quality, consistency, and compliance across the platform: policy enforcement, documentation standards, architectural consistency, specification validation, review workflows, approval gates, and auditability. A cross-cutting concern applying to every other layer.

*(Source: SYSTEM_ARCHITECTURE.md — Architectural Layers)*

---

# 5. System Boundaries

## Inside AI-SDOS
Engineering knowledge, project Documentation, Specifications, Architecture, Orchestration, Workflows, governance, and decision traceability.

## Outside AI-SDOS
Business-specific logic, application runtime behavior, production infrastructure, customer-facing functionality, and organization-specific business processes — these belong to the software projects AI-SDOS manages, not to AI-SDOS itself.

## External Actors and Systems
* **Human Stakeholders** — Project Architect, Software Engineer, Technical Lead, Product Owner, Domain Expert, Quality Assurance Engineer, Project Maintainer.
* **External Systems** — version control platforms, documentation repositories, issue tracking systems, development environments, CI/CD platforms, AI providers, external tools and MCP servers. These systems provide capabilities but remain outside the domain boundary.

*(Source: DOMAIN_DISCOVERY.md — Domain Boundaries, Stakeholders, External Systems)*

---

# 6. Information Flow

At a conceptual level, information flows through the platform as follows:

1. Human stakeholders (Human Layer) define objectives.
2. Objectives are formalized as Documentation and Specifications.
3. The Knowledge Layer stores and organizes those artifacts.
4. The Orchestration Layer creates Workflows and Tasks.
5. Specialized Agents (AI Agent Layer) execute assigned responsibilities, using the Tool Integration Layer to reach external systems when needed.
6. Generated artifacts are validated (Execution Layer, under Governance).
7. Approved outputs become part of the Knowledge Layer.
8. Project knowledge continuously evolves while preserving traceability.

The Knowledge Layer remains central throughout the lifecycle; the Governance Layer applies across every step.

*(Source: SYSTEM_ARCHITECTURE.md — Information Flow)*

---

# 7. Architectural Characteristics

* **Modularity** — layers collaborate through well-defined responsibilities rather than direct coupling.
* **Extensibility** — new capabilities can be introduced with minimal coupling, per the Evolution Strategy.
* **Scalability** — layered separation allows independent evolution of each capability.
* **Traceability** — every artifact must be traceable to documented sources; ADRs justify architectural decisions.
* **Maintainability** — documentation-as-code discipline keeps knowledge consistent and reusable.
* **Human-in-the-loop** — strategic decisions require human approval; AI agents never become the authoritative source of knowledge.

*(Source: SYSTEM_ARCHITECTURE.md — Dependency Principles, Cross-Cutting Concerns; FOUNDATION.md — Design Principles)*

---

# 8. Key Architectural Decisions

No Architecture Decision Records (ADRs) currently exist for AI-SDOS (confirmed absent from the project tree). The architectural decisions reflected in this overview are those narratively documented in SYSTEM_ARCHITECTURE.md (Architectural Style, Dependency Principles, Architectural Constraints). This is recorded as a Known Gap in PROJECT_STATE.md — future architectural decisions should be captured as discrete ADRs rather than only narratively.

---

# 9. Overview Diagram

See: `docs/architecture/diagrams/architecture-overview.html`

The diagram is produced using the AI-SDOS-DDS Diagram Framework (HTML/SVG, Canvas/Node/Group/Connector primitives), per `diagram-rules.md`, and shows the seven architectural layers, the Human Stakeholders and External Systems actors, and the primary relationships between them, without implementation detail.

---

# Related Documents

* PROJECT_STATE.md
* FOUNDATION.md
* DOMAIN_DISCOVERY.md
* UBIQUITOUS_LANGUAGE.md
* DOMAIN_MODEL.md
* SYSTEM_ARCHITECTURE.md
* Architecture Decision Records (ADRs) — none exist yet

---

# Change Log

| Version | Date | Description |
| ------- | ---------- | ----------------------------------------------------------------------------- |
| v0.1 | 2026-07-05 | Initial Architecture Overview generated from Foundation, Domain Discovery, Ubiquitous Language, Domain Model, and System Architecture. |
