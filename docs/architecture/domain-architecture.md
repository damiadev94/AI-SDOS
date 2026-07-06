# DOMAIN_ARCHITECTURE

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

The Domain Architecture view describes the domain structure of AI-SDOS through the lens of Domain-Driven Design.

Its purpose is to identify the bounded contexts that partition the domain, define each context's responsibility, describe the aggregates and domain services within each context, and document the relationships between contexts.

This view complements the C4 structural views by revealing the conceptual domain organization independently of any implementation or deployment structure. Where the Container Architecture asks "what are the runtime units?", the Domain Architecture asks "what are the domain responsibilities and their boundaries?"

*(Source: TASK-ARCH-005)*

---

# 2. Domain Overview

AI-SDOS operates within the **AI Engineering** domain.

The domain is organized around the full software development lifecycle as managed by an AI-driven operating system: from project inception and documentation through specification, architecture, orchestration, and execution.

The domain is subdivided into six bounded contexts, each responsible for a coherent and non-overlapping area of domain knowledge. These contexts are derived directly from DOMAIN_MODEL.md and reflect the natural boundaries of domain responsibility rather than technical partitioning decisions.

| Bounded Context | Core Responsibility |
|---|---|
| Project Context | Project lifecycle and governance |
| Documentation Context | Project knowledge management |
| Specification Context | Engineering intent and acceptance criteria |
| Architecture Context | System structure and design decisions |
| Orchestration Context | Engineering workflow coordination |
| Execution Context | Transformation of specifications into deliverables |

*(Source: DOMAIN_MODEL.md — Domain Overview, Bounded Contexts)*

---

# 3. Bounded Context Catalog

---

## Project Context

**Responsibility:**
Manages the lifecycle and governance of a software project from creation to completion.

**Primary Aggregates:**
* Project (root aggregate) — owns documentation, specifications, workflows, architecture, and execution history.

**Primary Entities:**
* Project
* Human Actor

**Primary Value Objects:**
* Identifier
* Status
* Version
* Timestamp
* Metadata

**Domain Services:**
* (none defined at this level — lifecycle transitions are governed through the Project aggregate root)

**Context Relationships:**
* Supplies project identity and lifecycle state to all other contexts.
* Receives summary state updates from the Documentation, Specification, Architecture, Orchestration, and Execution contexts.

*(Source: DOMAIN_MODEL.md — Project Context, Project Aggregate)*

---

## Documentation Context

**Responsibility:**
Manages the creation, versioning, organization, and retrieval of all project knowledge artifacts.

**Primary Aggregates:**
* Documentation — owns documents, sections, revisions, and references.

**Primary Entities:**
* Document
* Revision

**Primary Value Objects:**
* Document Path
* Version
* Reference
* Tag
* Timestamp

**Domain Services:**
* Documentation Service — maintains documentation consistency; validates that new artifacts conform to established standards before acceptance.

**Context Relationships:**
* Receives documentation content from the Orchestration Context (when agents produce documents).
* Provides documentation artifacts to all other contexts as the primary knowledge source.
* Integrates with the Architecture Context for architecture-specific documentation.

*(Source: DOMAIN_MODEL.md — Documentation Context, Documentation Aggregate, Documentation Service)*

---

## Specification Context

**Responsibility:**
Defines, validates, and manages formal engineering specifications that drive implementation.

**Primary Aggregates:**
* Specification — owns requirements, constraints, acceptance criteria, and dependencies.

**Primary Entities:**
* Specification

**Primary Value Objects:**
* Acceptance Criteria
* Dependency
* Priority
* Status
* Version
* Identifier

**Domain Services:**
* Specification Service — validates and manages specifications; enforces that specifications are complete before they are approved for execution.

**Context Relationships:**
* Consumes project documentation from the Documentation Context to ensure specifications align with documented knowledge.
* Provides approved specifications to the Execution Context as the trigger for implementation.
* Informs the Orchestration Context about available and pending specifications.

*(Source: DOMAIN_MODEL.md — Specification Context, Specification Aggregate, Specification Service)*

---

## Architecture Context

**Responsibility:**
Describes the structure of the system, maintains architectural views, and records architectural decisions.

**Primary Aggregates:**
* (Architecture-level aggregates are expressed as Architecture Views and ADRs, owned by the Architecture Context)

**Primary Entities:**
* Architecture View
* Diagram
* ADR (Architecture Decision Record)

**Primary Value Objects:**
* Version
* Status
* Reference
* Timestamp

**Domain Services:**
* Architecture Service — maintains architectural coherence; validates that new architectural views are consistent with existing ones and with the ubiquitous language.

**Context Relationships:**
* Derives from and references the Documentation Context for foundational documentation.
* Provides architectural context to the Orchestration Context and Execution Context.
* Records decisions that constrain or guide all other contexts.

*(Source: DOMAIN_MODEL.md — Architecture Context, Architecture Service; UBIQUITOUS_LANGUAGE.md — Architecture, ADR)*

---

## Orchestration Context

**Responsibility:**
Coordinates all engineering activities by managing workflows, scheduling tasks, and delegating responsibilities to specialized agents.

**Primary Aggregates:**
* Workflow — owns tasks, execution order, and completion state.
* Task — owns objective, inputs, outputs, dependencies, and status.

**Primary Entities:**
* Workflow
* Task
* AI Agent

**Primary Value Objects:**
* Status
* Dependency
* Priority
* Identifier
* Timestamp

**Domain Services:**
* Workflow Service — coordinates engineering workflows; ensures tasks execute in the correct order with the correct dependencies.
* Orchestration Service — delegates responsibilities to specialized AI agents; manages assignment and collection of results.

**Context Relationships:**
* Reads specifications from the Specification Context to construct execution workflows.
* Reads documentation and architecture from the Documentation and Architecture Contexts to build agent context packages.
* Delegates tasks to the Execution Context by assigning them to specialized agents.

*(Source: DOMAIN_MODEL.md — Orchestration Context, Workflow and Task Aggregates, Workflow Service, Orchestration Service)*

---

## Execution Context

**Responsibility:**
Transforms approved specifications into validated project deliverables through coordinated agent execution.

**Primary Aggregates:**
* (Execution artifacts are transient within this context before they are accepted into the Documentation or Architecture Contexts)

**Primary Entities:**
* AI Agent (during execution)

**Primary Value Objects:**
* Status
* Acceptance Criteria
* Version
* Timestamp

**Domain Services:**
* Validation Service — verifies that produced artifacts satisfy their acceptance criteria before they are accepted into the Knowledge Repository.

**Context Relationships:**
* Receives task assignments from the Orchestration Context.
* Validates outputs against acceptance criteria from the Specification Context.
* Delivers approved artifacts to the Documentation Context and Architecture Context for persistence.
* Reports completion events back to the Orchestration Context.

*(Source: DOMAIN_MODEL.md — Execution Context, Validation Service)*

---

# 4. Context Map

| Source Context | Target Context | Integration Type | Information Exchanged |
|---|---|---|---|
| Project Context | All Contexts | Shared Kernel (identity) | Project identity and lifecycle state |
| Documentation Context | All Contexts | Published Language | Documentation artifacts, knowledge |
| Specification Context | Orchestration Context | Customer/Supplier | Approved specifications trigger workflows |
| Architecture Context | Orchestration Context | Published Language | Architectural context for agent tasks |
| Architecture Context | Documentation Context | Conformist | Architecture artifacts stored in Documentation |
| Orchestration Context | Execution Context | Customer/Supplier | Task assignments |
| Execution Context | Documentation Context | Conformist | Validated artifacts stored as documentation |
| Execution Context | Architecture Context | Conformist | Validated architectural views stored |
| Execution Context | Orchestration Context | Published Language | Completion events, validation outcomes |

Integration types use standard DDD Context Map terminology:
* **Shared Kernel** — both contexts share a common model element (project identity).
* **Customer/Supplier** — one context (customer) depends on another (supplier) for output.
* **Published Language** — one context exposes a well-defined model for others to consume.
* **Conformist** — one context adapts its model to another without negotiation.

*(Source: DOMAIN_MODEL.md — Relationships, Bounded Contexts)*

---

# 5. Context-to-Container Mapping

| Bounded Context | Primary Container(s) |
|---|---|
| Project Context | Knowledge Repository (Project Manager component) |
| Documentation Context | Knowledge Repository (Documentation Store component) |
| Specification Context | Knowledge Repository (Documentation Store — specification artifacts) |
| Architecture Context | Knowledge Repository (Architecture Repository component) |
| Orchestration Context | Orchestration Engine (Workflow Engine, Task Manager, Agent Orchestrator) |
| Execution Context | AI Agent Runtime + Execution Engine |

The Governance Module applies cross-cutting governance to all bounded contexts without belonging to any single one.

*(Source: container-architecture.md; component-architecture.md)*

---

# 6. Domain Invariants

The following invariants must hold across all bounded contexts:

* Every Project has exactly one authoritative documentation set (Documentation Context).
* Every Specification belongs to exactly one Project (Specification Context).
* Every Task belongs to one Workflow (Orchestration Context).
* Every Workflow belongs to one Project (Orchestration Context).
* Every ADR references an architectural decision (Architecture Context).
* Every implementation originates from an approved Specification (Execution Context).
* Documentation is updated before implementation changes become authoritative (Documentation Context).
* AI agents never become the authoritative source of project knowledge (Execution → Documentation flow, never direct agent write).

*(Source: DOMAIN_MODEL.md — Invariants)*

---

# 7. Domain Diagram

See: `docs/architecture/diagrams/domain-architecture.mmd`

The diagram shows all six bounded contexts as labeled subgraph regions, the primary aggregates within each context as nodes, and the context relationships as labeled edges.

---

# Related Documents

* PROJECT_STATE.md
* FOUNDATION.md
* DOMAIN_DISCOVERY.md
* UBIQUITOUS_LANGUAGE.md
* DOMAIN_MODEL.md
* SYSTEM_ARCHITECTURE.md
* container-architecture.md
* component-architecture.md
* Architecture Decision Records (ADRs) — none exist yet

---

# Change Log

| Version | Date       | Description                                                          |
| ------- | ---------- | -------------------------------------------------------------------- |
| v0.1    | 2026-07-05 | Initial Domain Architecture generated from DOMAIN_MODEL.md. |
