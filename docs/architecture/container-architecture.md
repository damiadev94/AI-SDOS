# CONTAINER_ARCHITECTURE

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

The Container Architecture view describes the major runtime containers that compose AI-SDOS.

Its purpose is to identify each container, define its responsibility, describe the information it owns, and explain how containers collaborate to deliver the platform's capabilities.

This is the C4 Model Level 2 view for AI-SDOS. It refines the System Context by decomposing the platform into its principal structural units without exposing their internal components.

*(Source: TASK-ARCH-003)*

---

# 2. Architectural Scope

This view covers all runtime containers inside the AI-SDOS system boundary.

The System Context (system-context.md) established that boundary. This view reveals what is inside it — the major containers and how they collaborate — while preserving the same external actors and external systems identified at Level 1.

No internal components, source code structure, APIs, or deployment details appear in this view.

*(Source: system-context.md — System Boundary)*

---

# 3. Container Overview

AI-SDOS is organized into six containers, each aligned with a major architectural responsibility defined in SYSTEM_ARCHITECTURE.md.

| Container | Responsibility |
|---|---|
| Orchestration Engine | Coordinates workflows, tasks, and agent delegation |
| Knowledge Repository | Stores and organizes all authoritative project artifacts |
| AI Agent Runtime | Executes specialized engineering capabilities |
| Tool Integration Gateway | Connects the platform to external systems |
| Execution Engine | Transforms validated specifications into project artifacts |
| Governance Module | Enforces policies, standards, and audit trails |

The Governance Module is a cross-cutting container — its responsibilities apply across every other container.

*(Source: SYSTEM_ARCHITECTURE.md — Architectural Layers, Core Architectural Components)*

---

# 4. Container Catalog

---

## Orchestration Engine

**Responsibility:**
Coordinates the execution of engineering workflows across the platform.

**Primary Capabilities:**
* orchestrate multi-step engineering workflows;
* manage task dependencies and sequencing;
* schedule and assign tasks to Specialized Agents;
* resolve execution order across concurrent activities;
* delegate responsibilities to the AI Agent Runtime.

**Owned Information:**
* Workflow definitions;
* Task instances and their state;
* Dependency graphs;
* Execution history.

**Dependencies:**
* Knowledge Repository — reads project documentation, specifications, and architectural artifacts to build workflow context;
* AI Agent Runtime — delegates engineering tasks;
* Governance Module — submits workflows to governance gates.

**Interactions:**
* Receives workflow instructions from human actors (via the Human Layer).
* Reads knowledge artifacts from the Knowledge Repository to construct task context.
* Delegates tasks to the AI Agent Runtime.
* Routes outputs for governance review before persisting them.

*(Source: SYSTEM_ARCHITECTURE.md — Orchestration Layer; DOMAIN_MODEL.md — Workflow, Task aggregates)*

---

## Knowledge Repository

**Responsibility:**
Maintains the authoritative knowledge of every managed project.

**Primary Capabilities:**
* store and organize documentation artifacts;
* maintain specifications and architectural views;
* preserve project state and lifecycle history;
* provide artifact retrieval to all containers;
* maintain the Ubiquitous Language and ADR catalog.

**Owned Information:**
* Project documentation (Foundation, Domain Discovery, Ubiquitous Language, Domain Model, System Architecture);
* Specifications (SPECs);
* Architectural views and diagrams;
* Architecture Decision Records (ADRs);
* Project State;
* Historical traceability records.

**Dependencies:**
* Governance Module — every artifact stored passes through governance validation.

**Interactions:**
* Supplies context and artifacts to the Orchestration Engine for workflow construction.
* Supplies context to the AI Agent Runtime for agent task execution.
* Receives validated artifacts from the Execution Engine after governance approval.
* Exposes artifacts to human actors for review, validation, and approval.

*(Source: SYSTEM_ARCHITECTURE.md — Knowledge Layer; DOMAIN_MODEL.md — Documentation, Specification, Architecture Context aggregates)*

---

## AI Agent Runtime

**Responsibility:**
Provides the execution environment for Specialized AI Agents.

**Primary Capabilities:**
* execute Specialized Agents for specific engineering capabilities;
* invoke AI model providers for language model capabilities;
* receive task assignments from the Orchestration Engine;
* produce engineering artifacts (documentation, diagrams, specifications, analysis);
* pass generated outputs to the Execution Engine for validation.

**Owned Information:**
* Agent execution context (derived from Knowledge Repository, not stored independently);
* Active task assignments;
* Intermediate generation outputs.

**Dependencies:**
* Knowledge Repository — reads project artifacts as agent context;
* Orchestration Engine — receives task assignments;
* Tool Integration Gateway — accesses external tools and AI providers;
* Execution Engine — delivers outputs for validation.

**Interactions:**
* Receives task assignments from the Orchestration Engine.
* Reads current project knowledge from the Knowledge Repository.
* Invokes AI Providers and MCP Servers through the Tool Integration Gateway.
* Delivers generated artifacts to the Execution Engine.

*(Source: SYSTEM_ARCHITECTURE.md — AI Agent Layer; DOMAIN_MODEL.md — Orchestration Context)*

---

## Tool Integration Gateway

**Responsibility:**
Connects AI-SDOS to external systems and capabilities.

**Primary Capabilities:**
* provide adapters for external systems (version control, AI providers, IDEs, issue trackers, CI/CD, documentation platforms, MCP servers);
* abstract external dependencies from platform internals;
* translate platform requests into external system interactions;
* surface external results back into the platform.

**Owned Information:**
* Integration configuration;
* External system connection state.

**Dependencies:**
* All external systems identified in the System Context.

**Interactions:**
* Serves the AI Agent Runtime by providing access to AI providers and MCP servers.
* Serves the Execution Engine by providing access to version control and CI/CD systems.
* Serves the Orchestration Engine by providing access to issue tracking systems.
* Ensures external systems remain loosely coupled to the platform core.

*(Source: SYSTEM_ARCHITECTURE.md — Tool Integration Layer)*

---

## Execution Engine

**Responsibility:**
Transforms approved Specifications into validated project artifacts.

**Primary Capabilities:**
* receive artifact candidates from the AI Agent Runtime;
* validate artifacts against documented acceptance criteria;
* coordinate with CI/CD systems for automated validation;
* produce approved outputs ready for persistence;
* reject non-conforming artifacts and report failures.

**Owned Information:**
* Validation rules (derived from specifications and governance policies);
* Validation outcomes;
* Artifact production records.

**Dependencies:**
* Knowledge Repository — reads specifications and acceptance criteria;
* Governance Module — validation policies and approval gates;
* Tool Integration Gateway — connects to CI/CD platforms for automated checks.

**Interactions:**
* Receives artifact candidates from the AI Agent Runtime.
* Validates against acceptance criteria from the Knowledge Repository.
* Submits approved artifacts to the Knowledge Repository for persistence.
* Reports validation failures back to the Orchestration Engine.

*(Source: SYSTEM_ARCHITECTURE.md — Execution Layer)*

---

## Governance Module

**Responsibility:**
Preserves quality, consistency, and compliance across the entire platform.

**Primary Capabilities:**
* enforce documentation and specification standards;
* apply approval gates before artifacts progress;
* validate architectural consistency;
* maintain audit trails;
* enforce governance policies across all containers.

**Owned Information:**
* Governance policies;
* Approval records;
* Audit logs;
* Compliance state.

**Dependencies:**
* Applied cross-cutting to all containers; no single upstream container dependency.

**Interactions:**
* Monitors and validates outputs produced by every other container.
* Enforces approval gates before artifacts are persisted to the Knowledge Repository.
* Applies documentation standards to outputs from the AI Agent Runtime.
* Records audit events for every significant state change.

*(Source: SYSTEM_ARCHITECTURE.md — Governance Layer)*

---

# 5. Container Relationships

| Source | Target | Purpose | Information Exchanged |
|---|---|---|---|
| Orchestration Engine | Knowledge Repository | Read project knowledge to build workflow context | Documentation, specifications, project state |
| Orchestration Engine | AI Agent Runtime | Delegate engineering tasks | Task assignments, context packages |
| Orchestration Engine | Governance Module | Submit workflows for governance gate | Workflow proposals |
| Knowledge Repository | Governance Module | Validate artifacts before storage | Artifact candidates, validation results |
| AI Agent Runtime | Knowledge Repository | Read authoritative project context | Documentation, specifications, architectural artifacts |
| AI Agent Runtime | Tool Integration Gateway | Invoke AI providers and MCP servers | Prompts, tool requests, results |
| AI Agent Runtime | Execution Engine | Deliver generated artifact candidates | Documentation, diagrams, specifications |
| Tool Integration Gateway | External Systems | Communicate with external capabilities | Requests, results, events |
| Execution Engine | Knowledge Repository | Persist approved artifacts | Validated documentation, specs, diagrams |
| Execution Engine | Governance Module | Apply validation policies | Validation criteria, outcomes |
| Execution Engine | Tool Integration Gateway | Trigger CI/CD validation | Pipeline triggers, results |
| Governance Module | All containers | Enforce policies, audit events | Policy rules, audit records, approvals |

---

# 6. Data Ownership

| Information Category | Owning Container |
|---|---|
| Project documentation (Foundation, Domain Discovery, UL, Domain Model, System Architecture) | Knowledge Repository |
| Specifications (SPECs) | Knowledge Repository |
| Architectural views and diagrams | Knowledge Repository |
| Architecture Decision Records (ADRs) | Knowledge Repository |
| Project State | Knowledge Repository |
| Historical traceability records | Knowledge Repository |
| Workflow definitions and state | Orchestration Engine |
| Task instances and dependencies | Orchestration Engine |
| Agent execution context (transient) | AI Agent Runtime |
| Integration configuration | Tool Integration Gateway |
| Validation rules and outcomes | Execution Engine |
| Governance policies and audit logs | Governance Module |

No information category has more than one owning container. Derived or transient data is explicitly marked as not persisted independently.

---

# 7. Architectural Responsibilities

**Modularity:** Each container owns a single, non-overlapping responsibility. The Orchestration Engine coordinates; the Knowledge Repository persists; the AI Agent Runtime executes; the Tool Integration Gateway abstracts external systems; the Execution Engine validates; the Governance Module enforces compliance.

**Cohesion:** Related capabilities are co-located within a single container. Workflow management (Orchestration Engine) and knowledge persistence (Knowledge Repository) are explicitly separated, preventing the emergence of a coupled monolith.

**Separation of Concerns:** Execution capability (AI Agent Runtime) is separated from validation (Execution Engine), which is separated from persistence (Knowledge Repository). A failed validation does not corrupt the knowledge base.

**Traceability:** Every artifact flows from the AI Agent Runtime through the Execution Engine and Governance Module before reaching the Knowledge Repository. This flow ensures that every stored artifact is validated and its origin is traceable.

*(Source: SYSTEM_ARCHITECTURE.md — Dependency Principles, Cross-Cutting Concerns)*

---

# 8. Container Diagram

See: `docs/architecture/diagrams/container-architecture.mmd`

The diagram shows all six containers within the AI-SDOS system boundary, with directional relationships labeled by purpose. External actors and external systems appear outside the boundary consistent with the System Context.

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
* Architecture Decision Records (ADRs) — none exist yet

---

# Change Log

| Version | Date       | Description                                                           |
| ------- | ---------- | --------------------------------------------------------------------- |
| v0.1    | 2026-07-05 | Initial Container Architecture generated from project documentation. |
