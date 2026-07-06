# COMPONENT_ARCHITECTURE

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

The Component Architecture view decomposes each container identified in the Container Architecture into its major architectural components.

Its purpose is to describe the internal organization of each container — defining the responsibility, capabilities, dependencies, and collaborations of every component — while preserving the container boundaries established at Level 2.

This is the C4 Model Level 3 view for AI-SDOS. It refines the Container Architecture without introducing source code structure, implementation details, or infrastructure concerns.

*(Source: TASK-ARCH-004)*

---

# 2. Scope

All six containers documented in container-architecture.md are decomposed in this view.

Each container requires internal decomposition because its responsibilities are delivered through multiple coordinating architectural components. No container was identified as atomic at this level of analysis.

Components are derived exclusively from the SYSTEM_ARCHITECTURE.md (Core Architectural Components, Architectural Layers) and the DOMAIN_MODEL.md (Aggregates, Domain Services). No implementation details were introduced.

*(Source: container-architecture.md; SYSTEM_ARCHITECTURE.md — Core Architectural Components)*

---

# 3. Component Catalog

---

## Orchestration Engine

---

### Workflow Engine

| Field | Value |
|---|---|
| Container | Orchestration Engine |
| Responsibility | Defines, manages, and executes engineering workflows |
| Primary Capabilities | Workflow lifecycle management; phase sequencing; workflow state tracking; parallel workflow coordination |
| Owned Information | Workflow templates; active workflow instances; workflow state |
| Dependencies | Task Manager (creates tasks from workflows); Knowledge Repository (reads documentation context) |
| Collaborating Components | Task Manager, Agent Orchestrator |

---

### Task Manager

| Field | Value |
|---|---|
| Container | Orchestration Engine |
| Responsibility | Maintains executable task units and their dependency graph |
| Primary Capabilities | Task creation; dependency resolution; execution sequencing; task state tracking; progress reporting |
| Owned Information | Task instances; dependency graphs; task status; execution order |
| Dependencies | Workflow Engine (receives task blueprints from workflows); Agent Orchestrator (submits tasks for agent delegation) |
| Collaborating Components | Workflow Engine, Agent Orchestrator |

---

### Agent Orchestrator

| Field | Value |
|---|---|
| Container | Orchestration Engine |
| Responsibility | Assigns tasks to appropriate Specialized Agents and coordinates their execution |
| Primary Capabilities | Agent selection; task assignment; delegation tracking; result collection |
| Owned Information | Agent assignment records; delegation state |
| Dependencies | Task Manager (receives tasks to delegate); AI Agent Runtime (delegates to agents) |
| Collaborating Components | Task Manager |

*(Source: SYSTEM_ARCHITECTURE.md — Orchestration Layer, Core Architectural Components: Workflow Engine, Task Manager, Agent Orchestrator)*

---

## Knowledge Repository

---

### Project Manager

| Field | Value |
|---|---|
| Container | Knowledge Repository |
| Responsibility | Maintains project lifecycle information and project-level metadata |
| Primary Capabilities | Project identity management; lifecycle state tracking; roadmap maintenance; ownership governance |
| Owned Information | Project identity; lifecycle phase; roadmap; governance records |
| Dependencies | Governance Module (governance events); Documentation Store (project documentation) |
| Collaborating Components | Documentation Store, Architecture Repository |

---

### Documentation Store

| Field | Value |
|---|---|
| Container | Knowledge Repository |
| Responsibility | Stores and organizes all project documentation artifacts |
| Primary Capabilities | Document storage; document versioning; documentation hierarchy management; cross-reference maintenance; retrieval by artifact type |
| Owned Information | Foundation; Domain Discovery; Ubiquitous Language; Domain Model; System Architecture; Project State; all other documentation |
| Dependencies | Governance Module (artifacts validated before storage) |
| Collaborating Components | Architecture Repository, Project Manager |

---

### Architecture Repository

| Field | Value |
|---|---|
| Container | Knowledge Repository |
| Responsibility | Maintains architectural views, diagrams, and Architecture Decision Records |
| Primary Capabilities | Architecture view storage; ADR management; diagram management; architectural consistency tracking; architectural history |
| Owned Information | Architecture views (System Context, Container, Component, Domain, Information Flow, etc.); Mermaid diagrams; ADR catalog |
| Dependencies | Governance Module (architectural artifacts validated before storage); Documentation Store (cross-references to project documentation) |
| Collaborating Components | Documentation Store, Project Manager |

*(Source: SYSTEM_ARCHITECTURE.md — Knowledge Layer, Core Architectural Components: Project Manager, Knowledge Repository, Architecture Repository)*

---

## AI Agent Runtime

---

### Documentation Agent

| Field | Value |
|---|---|
| Container | AI Agent Runtime |
| Responsibility | Generates, updates, and reviews project documentation artifacts |
| Primary Capabilities | Document generation; document review; documentation gap analysis; documentation consistency checking |
| Owned Information | Transient generation context (derived from Knowledge Repository) |
| Dependencies | Knowledge Repository (context); Tool Integration Gateway (AI provider access) |
| Collaborating Components | Architecture Agent, Validation Agent |

---

### Architecture Agent

| Field | Value |
|---|---|
| Container | AI Agent Runtime |
| Responsibility | Produces and validates architectural views, diagrams, and architectural documentation |
| Primary Capabilities | Architecture view generation; diagram generation; architectural review; C4 view production |
| Owned Information | Transient architectural generation context |
| Dependencies | Knowledge Repository (project documentation and existing views); Tool Integration Gateway (AI provider access) |
| Collaborating Components | Documentation Agent, Validation Agent |

---

### Implementation Agent

| Field | Value |
|---|---|
| Container | AI Agent Runtime |
| Responsibility | Transforms validated specifications into implementation artifacts |
| Primary Capabilities | Code generation; implementation guidance; specification-to-code translation |
| Owned Information | Transient implementation context |
| Dependencies | Knowledge Repository (specifications and architectural context); Tool Integration Gateway (AI provider and IDE access) |
| Collaborating Components | Validation Agent |

---

### Testing Agent

| Field | Value |
|---|---|
| Container | AI Agent Runtime |
| Responsibility | Generates and coordinates test artifacts for validated specifications |
| Primary Capabilities | Test generation; acceptance criteria verification; test plan production |
| Owned Information | Transient test generation context |
| Dependencies | Knowledge Repository (specifications and acceptance criteria); Tool Integration Gateway (AI provider and CI/CD access) |
| Collaborating Components | Validation Agent |

---

### Analysis Agent

| Field | Value |
|---|---|
| Container | AI Agent Runtime |
| Responsibility | Performs analysis tasks such as impact assessment, gap analysis, and consistency checking |
| Primary Capabilities | Impact analysis; documentation gap detection; inconsistency detection; dependency analysis |
| Owned Information | Transient analysis context |
| Dependencies | Knowledge Repository (all project artifacts); Tool Integration Gateway (AI provider access) |
| Collaborating Components | Documentation Agent, Architecture Agent |

---

### Review Agent

| Field | Value |
|---|---|
| Container | AI Agent Runtime |
| Responsibility | Reviews generated artifacts for quality, correctness, and alignment with project standards |
| Primary Capabilities | Artifact review; quality assessment; consistency validation; terminology verification |
| Owned Information | Transient review context |
| Dependencies | Knowledge Repository (project standards, ubiquitous language, existing artifacts); Tool Integration Gateway (AI provider access) |
| Collaborating Components | Validation Agent |

---

### Validation Agent

| Field | Value |
|---|---|
| Container | AI Agent Runtime |
| Responsibility | Verifies that artifacts satisfy their documented acceptance criteria |
| Primary Capabilities | Acceptance criteria verification; artifact completeness checking; specification compliance validation |
| Owned Information | Transient validation context |
| Dependencies | Knowledge Repository (acceptance criteria and specifications); Execution Engine (delivers validated artifacts) |
| Collaborating Components | All other AI agents within the runtime |

*(Source: SYSTEM_ARCHITECTURE.md — AI Agent Layer; DOMAIN_DISCOVERY.md — AI Stakeholders)*

---

## Tool Integration Gateway

---

### AI Provider Adapter

| Field | Value |
|---|---|
| Container | Tool Integration Gateway |
| Responsibility | Manages communication with external AI model providers |
| Primary Capabilities | Model invocation; prompt delivery; response handling; provider abstraction |
| Owned Information | Provider configuration; connection state |
| Dependencies | AI Providers (external) |
| Collaborating Components | MCP Server Adapter, Version Control Adapter |

---

### Version Control Adapter

| Field | Value |
|---|---|
| Container | Tool Integration Gateway |
| Responsibility | Manages communication with version control platforms |
| Primary Capabilities | Artifact storage; history retrieval; change tracking |
| Owned Information | VCS connection configuration |
| Dependencies | Version Control Platform (external) |
| Collaborating Components | CI/CD Adapter |

---

### IDE Adapter

| Field | Value |
|---|---|
| Container | Tool Integration Gateway |
| Responsibility | Delivers context and specifications to development environments |
| Primary Capabilities | Context injection; specification delivery; IDE extension support |
| Owned Information | IDE connection configuration |
| Dependencies | Development Environments (external) |
| Collaborating Components | AI Provider Adapter |

---

### MCP Server Adapter

| Field | Value |
|---|---|
| Container | Tool Integration Gateway |
| Responsibility | Connects to MCP servers to access extended tool capabilities |
| Primary Capabilities | Tool capability invocation; result retrieval; MCP protocol handling |
| Owned Information | MCP server configuration and connection state |
| Dependencies | MCP Servers (external) |
| Collaborating Components | AI Provider Adapter |

---

### Issue Tracker Adapter

| Field | Value |
|---|---|
| Container | Tool Integration Gateway |
| Responsibility | Surfaces tasks and decisions in external issue tracking systems |
| Primary Capabilities | Task creation; status updates; decision surfacing |
| Owned Information | Issue tracker configuration |
| Dependencies | Issue Tracking Systems (external) |
| Collaborating Components | Version Control Adapter |

---

### CI/CD Adapter

| Field | Value |
|---|---|
| Container | Tool Integration Gateway |
| Responsibility | Integrates with CI/CD platforms for automated validation and build pipelines |
| Primary Capabilities | Pipeline trigger; validation result retrieval; build status tracking |
| Owned Information | CI/CD platform configuration |
| Dependencies | CI/CD Platforms (external) |
| Collaborating Components | Version Control Adapter |

*(Source: SYSTEM_ARCHITECTURE.md — Tool Integration Layer)*

---

## Execution Engine

---

### Artifact Producer

| Field | Value |
|---|---|
| Container | Execution Engine |
| Responsibility | Coordinates the production of project artifacts from validated AI agent outputs |
| Primary Capabilities | Artifact assembly; format normalization; output packaging |
| Owned Information | Artifact production records (transient) |
| Dependencies | AI Agent Runtime (receives raw outputs); Validation Engine (submits for validation) |
| Collaborating Components | Validation Engine |

---

### Validation Engine

| Field | Value |
|---|---|
| Container | Execution Engine |
| Responsibility | Verifies that produced artifacts satisfy documented acceptance criteria |
| Primary Capabilities | Acceptance criteria matching; specification compliance checking; validation outcome reporting; failure reporting |
| Owned Information | Validation criteria (derived from Knowledge Repository); validation outcomes |
| Dependencies | Knowledge Repository (acceptance criteria and specifications); Governance Module (validation policies); Tool Integration Gateway (CI/CD validation) |
| Collaborating Components | Artifact Producer |

*(Source: SYSTEM_ARCHITECTURE.md — Execution Layer, Core Architectural Components: Validation Engine)*

---

## Governance Module

---

### Policy Enforcer

| Field | Value |
|---|---|
| Container | Governance Module |
| Responsibility | Applies governance policies across all platform activities |
| Primary Capabilities | Policy definition; policy application; non-compliance detection and reporting |
| Owned Information | Active governance policies; policy versions |
| Dependencies | Applied cross-cutting to all containers |
| Collaborating Components | Approval Gate Manager, Audit Logger, Documentation Standards Validator |

---

### Documentation Standards Validator

| Field | Value |
|---|---|
| Container | Governance Module |
| Responsibility | Validates that documentation artifacts conform to DDS standards and project conventions |
| Primary Capabilities | Structural validation; terminology consistency checking; DDS compliance verification |
| Owned Information | Documentation standards definitions |
| Dependencies | Knowledge Repository (ubiquitous language and documentation standards) |
| Collaborating Components | Policy Enforcer, Approval Gate Manager |

---

### Approval Gate Manager

| Field | Value |
|---|---|
| Container | Governance Module |
| Responsibility | Manages approval workflows and gates for significant artifact transitions |
| Primary Capabilities | Gate definition; approval state tracking; human approval routing; gate outcome enforcement |
| Owned Information | Approval records; gate state; approval history |
| Dependencies | Human actors (approval decisions); Policy Enforcer |
| Collaborating Components | Policy Enforcer, Audit Logger |

---

### Audit Logger

| Field | Value |
|---|---|
| Container | Governance Module |
| Responsibility | Records significant state changes and events across the platform for auditability |
| Primary Capabilities | Event capture; audit log persistence; audit trail queries |
| Owned Information | Audit log |
| Dependencies | Applied cross-cutting — receives events from all containers |
| Collaborating Components | Policy Enforcer, Approval Gate Manager |

*(Source: SYSTEM_ARCHITECTURE.md — Governance Layer)*

---

# 4. Internal Collaboration

## Orchestration Engine

The Workflow Engine creates tasks from workflow definitions and passes them to the Task Manager. The Task Manager resolves dependencies and determines execution order. Ready tasks are submitted to the Agent Orchestrator, which selects the appropriate Specialized Agent and delegates the assignment. Results from the Agent Orchestrator feed back into the Task Manager to update task state and trigger downstream tasks.

## Knowledge Repository

The Project Manager governs project identity and lifecycle. The Documentation Store holds all documentation artifacts and maintains version history. The Architecture Repository holds all architectural views and ADRs. The three components cross-reference each other: the Architecture Repository references documentation from the Documentation Store; the Project Manager maintains pointers to lifecycle milestones in both stores. All writes pass through the Governance Module before being accepted.

## AI Agent Runtime

The Agent Orchestrator (in the Orchestration Engine container) assigns a task to a specific Specialized Agent. The agent reads context from the Knowledge Repository, invokes AI capabilities through the Tool Integration Gateway, and produces an artifact. The Review Agent and Validation Agent collaborate to assess quality before the artifact exits the runtime. Validated artifacts pass to the Execution Engine.

## Tool Integration Gateway

Adapters operate independently of each other. Each adapter abstracts a single external system category. The AI Provider Adapter and MCP Server Adapter are the most frequently invoked by the AI Agent Runtime. The CI/CD Adapter is primarily invoked by the Execution Engine. The Version Control Adapter and Issue Tracker Adapter support both execution and governance workflows.

## Execution Engine

The Artifact Producer receives raw outputs from the AI Agent Runtime and assembles them into production-ready artifacts. Assembled artifacts are submitted to the Validation Engine, which checks them against acceptance criteria from the Knowledge Repository and policies from the Governance Module. Approved artifacts proceed to the Knowledge Repository. Failed artifacts are returned with rejection reports to the Orchestration Engine.

## Governance Module

The Policy Enforcer maintains active policies and distributes them to other components. The Documentation Standards Validator applies DDS conventions to every documentation artifact. The Approval Gate Manager routes significant artifacts to human actors for approval and enforces outcomes. The Audit Logger records all state transitions and decisions. These four components collaborate to form a continuous governance loop across every platform activity.

---

# 5. Component Responsibilities

| Component | Container | Single Responsibility |
|---|---|---|
| Workflow Engine | Orchestration Engine | Manages engineering workflow lifecycle |
| Task Manager | Orchestration Engine | Maintains task units and dependency resolution |
| Agent Orchestrator | Orchestration Engine | Assigns tasks to Specialized Agents |
| Project Manager | Knowledge Repository | Maintains project identity and lifecycle state |
| Documentation Store | Knowledge Repository | Stores all documentation artifacts |
| Architecture Repository | Knowledge Repository | Stores all architectural views, diagrams, ADRs |
| Documentation Agent | AI Agent Runtime | Generates and reviews documentation |
| Architecture Agent | AI Agent Runtime | Generates and validates architectural views |
| Implementation Agent | AI Agent Runtime | Transforms specs into implementation artifacts |
| Testing Agent | AI Agent Runtime | Generates test artifacts |
| Analysis Agent | AI Agent Runtime | Performs analysis and consistency checking |
| Review Agent | AI Agent Runtime | Reviews artifact quality |
| Validation Agent | AI Agent Runtime | Verifies acceptance criteria compliance |
| AI Provider Adapter | Tool Integration Gateway | Manages AI model provider communication |
| Version Control Adapter | Tool Integration Gateway | Manages VCS communication |
| IDE Adapter | Tool Integration Gateway | Delivers context to IDEs |
| MCP Server Adapter | Tool Integration Gateway | Manages MCP server invocations |
| Issue Tracker Adapter | Tool Integration Gateway | Surfaces tasks in issue trackers |
| CI/CD Adapter | Tool Integration Gateway | Integrates with CI/CD pipelines |
| Artifact Producer | Execution Engine | Assembles production-ready artifacts |
| Validation Engine | Execution Engine | Validates artifacts against acceptance criteria |
| Policy Enforcer | Governance Module | Applies governance policies |
| Documentation Standards Validator | Governance Module | Validates DDS compliance |
| Approval Gate Manager | Governance Module | Manages approval workflows and gates |
| Audit Logger | Governance Module | Records platform events and state changes |

No two components share the same primary responsibility. Overlap is prevented by the explicit single-responsibility assignment per component.

---

# 6. Dependency Rules

**Permitted dependencies:**
* Components within a container may depend on sibling components within the same container.
* Containers may depend on the Knowledge Repository for context.
* Containers may depend on the Governance Module for policy and approval.
* The AI Agent Runtime may depend on the Tool Integration Gateway for external capabilities.
* The Execution Engine may depend on the Tool Integration Gateway for CI/CD.

**Prohibited dependencies:**
* Components must not directly access components in another container without passing through the container's defined interface.
* The Knowledge Repository must not depend on the Orchestration Engine, AI Agent Runtime, or Execution Engine — dependency flows are unidirectional: downstream containers read from the repository, not the reverse.
* AI Agents must not write directly to the Knowledge Repository — all writes flow through the Execution Engine and Governance Module.
* The Tool Integration Gateway must not initiate platform-internal workflows — it only responds to invocations.
* Governance Module components must not be bypassed — every state transition passes through the Governance Module.

*(Source: SYSTEM_ARCHITECTURE.md — Dependency Principles)*

---

# 7. Architectural Consistency

**Modularity:** Every component has a single, explicitly bounded responsibility. No component duplicates another's ownership. The Tool Integration Gateway's adapter pattern ensures external system changes require only adapter-level modifications.

**Cohesion:** Components related to the same container responsibility are co-located. All knowledge persistence components (Project Manager, Documentation Store, Architecture Repository) reside in the Knowledge Repository. All governance components (Policy Enforcer, Standards Validator, Approval Gate Manager, Audit Logger) reside in the Governance Module.

**Separation of Concerns:** Generation (AI Agent Runtime) is separated from validation (Execution Engine), which is separated from persistence (Knowledge Repository), which is separated from governance (Governance Module). This four-stage separation prevents unvalidated outputs from reaching the authoritative knowledge base.

**Traceability:** The Audit Logger in the Governance Module records every significant state change. The Architecture Repository maintains the complete history of all architectural views. The Documentation Store preserves all document revisions. Every artifact in the Knowledge Repository is traceable to its generating agent, its validation outcome, and its approving gate.

**Maintainability:** Specialized Agents in the AI Agent Runtime are independently extensible — new agent types can be added without modifying other components. External system changes are absorbed by individual adapters in the Tool Integration Gateway without affecting internal components.

*(Source: SYSTEM_ARCHITECTURE.md — Dependency Principles, Cross-Cutting Concerns, Evolution Strategy)*

---

# 8. Component Diagram

See: `docs/architecture/diagrams/component-architecture.mmd`

The diagram shows all 25 components grouped by their owning container, with directional dependencies labeled by purpose.

---

# Related Documents

* PROJECT_STATE.md
* FOUNDATION.md
* DOMAIN_DISCOVERY.md
* UBIQUITOUS_LANGUAGE.md
* DOMAIN_MODEL.md
* SYSTEM_ARCHITECTURE.md
* architecture-overview.md
* system-context.md
* container-architecture.md
* Architecture Decision Records (ADRs) — none exist yet

---

# Change Log

| Version | Date       | Description                                                             |
| ------- | ---------- | ----------------------------------------------------------------------- |
| v0.1    | 2026-07-05 | Initial Component Architecture generated from project documentation. |
