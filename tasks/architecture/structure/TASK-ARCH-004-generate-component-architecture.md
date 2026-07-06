# TASK-ARCH-004 — Generate Component Architecture

## Metadata

| Field      | Value                                                 |
| ---------- | ----------------------------------------------------- |
| ID         | TASK-ARCH-004                                         |
| Name       | Generate Component Architecture                       |
| Category   | Architecture Documentation                            |
| Priority   | High                                                  |
| Depends On | TASK-ARCH-001, TASK-ARCH-002, TASK-ARCH-003           |
| Outputs    | component-architecture.md, component-architecture.mmd |

---

# Objective

Produce the Component Architecture documentation for AI-SDOS.

The objective is to decompose each documented container into its major architectural components, describe their responsibilities, define their relationships, and explain how they collaborate within their respective container.

This view corresponds to the **Component level** of the C4 Model.

---

# Inputs

Read and analyze:

* PROJECT_STATE.md
* FOUNDATION.md
* DOMAIN_DISCOVERY.md
* UBIQUITOUS_LANGUAGE.md
* DOMAIN_MODEL.md
* SYSTEM_ARCHITECTURE.md
* architecture-overview.md
* system-context.md
* container-architecture.md
* Relevant ADRs

If required information is missing or inconsistent, stop execution and report the issue.

---

# Responsibilities

The task must:

* identify the architectural components contained within each documented container;
* define the responsibility of every component;
* describe how components collaborate inside their container;
* document component dependencies;
* preserve the boundaries established by the Container Architecture.

The task must **not**:

* introduce undocumented components;
* describe source code structure;
* describe classes or interfaces;
* define APIs or endpoints;
* describe infrastructure or deployment;
* cross container boundaries without documented justification.

---

# Required Sections

## 1. Purpose

Explain the purpose of the Component Architecture view and its relationship to the Container Architecture.

---

## 2. Scope

Define which containers are decomposed and why.

If a documented container has no meaningful internal decomposition, explicitly state that no Component view is required.

---

## 3. Component Catalog

For each documented container requiring decomposition, document:

* Container
* Component Name
* Responsibility
* Primary Capabilities
* Owned Information
* Dependencies
* Collaborating Components

Components must originate from the documented architecture rather than implementation details.

---

## 4. Internal Collaboration

Describe how the components inside each container cooperate to fulfill the container's responsibilities.

Focus on responsibilities and information flow rather than execution details.

---

## 5. Component Responsibilities

Summarize the responsibility assigned to every component and explain how responsibility boundaries prevent overlap and reduce coupling.

---

## 6. Dependency Rules

Document the architectural dependency rules governing interactions between components.

Explicitly identify prohibited dependencies where applicable.

---

## 7. Architectural Consistency

Explain how the Component Architecture preserves:

* modularity;
* cohesion;
* separation of concerns;
* traceability;
* maintainability.

---

## 8. Component Diagram

Generate one or more Component diagrams representing the internal decomposition of the documented containers.

Each diagram should show:

* components;
* responsibilities;
* dependencies;
* information flow.

Avoid implementation details.

---

# Diagram Requirements

Generate:

component-architecture.mmd

Requirements:

* Mermaid
* Left-to-right layout
* One node per architectural component
* Components grouped by their owning container
* Human-readable labels
* Clear directional dependencies
* Maximum readability
* No classes
* No functions
* No source files
* No database tables
* No infrastructure
* No deployment details

If multiple diagrams improve readability, generate one diagram per container instead of a single oversized diagram.

---

# Outputs

Produce:

```text
docs/architecture/component-architecture.md
```

and

```text
docs/architecture/diagrams/component-architecture.mmd
```

or, when appropriate:

```text
docs/architecture/diagrams/components/
```

containing one Mermaid diagram per container.

---

# Acceptance Criteria

The task is complete only if:

* every documented component belongs to exactly one documented container;
* every component has a clearly defined responsibility;
* dependencies respect the Container Architecture;
* no undocumented architectural elements are introduced;
* diagrams and documentation are consistent;
* implementation details are excluded;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* required documentation is missing;
* undocumented components are introduced;
* component boundaries are ambiguous;
* responsibilities overlap without justification;
* components are modeled from implementation rather than architecture;
* diagrams contradict the documented containers;
* implementation details appear.

---

# Notes

This task represents the **Component level** of the C4 Model.

It refines the Container Architecture by revealing the internal organization of each container while preserving the architectural boundaries established by previous documentation.

The resulting Component Architecture becomes the primary input for behavioral views such as Information Flow, Agent Integration, and Sequence Architecture.
