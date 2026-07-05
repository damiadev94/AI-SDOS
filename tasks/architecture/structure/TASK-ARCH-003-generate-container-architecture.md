# TASK-ARCH-003 — Generate Container Architecture

## Metadata

| Field      | Value                                                 |
| ---------- | ----------------------------------------------------- |
| ID         | TASK-ARCH-003                                         |
| Name       | Generate Container Architecture                       |
| Category   | Architecture Documentation                            |
| Priority   | High                                                  |
| Depends On | TASK-ARCH-001, TASK-ARCH-002                          |
| Outputs    | container-architecture.md, container-architecture.mmd |

---

# Objective

Produce the Container Architecture documentation for AI-SDOS.

The objective is to identify the major runtime containers that compose the platform, describe their responsibilities, define their relationships, and explain how they collaborate to deliver the system's capabilities.

This view corresponds to the **Container level** of the C4 Model.

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
* Relevant ADRs

If required information is missing or inconsistent, stop execution and report the issue.

---

# Responsibilities

The task must:

* identify the major containers that compose AI-SDOS;
* define the responsibility of each container;
* describe the information exchanged between containers;
* identify container dependencies;
* explain the role of each container within the platform.

The task must **not**:

* describe internal classes or components;
* define APIs or endpoints;
* define deployment topology;
* describe infrastructure or networking;
* introduce undocumented containers.

---

# Required Sections

## 1. Purpose

Explain the purpose of the Container Architecture view.

---

## 2. Architectural Scope

Define the scope covered by this view and its relationship to the System Context.

---

## 3. Container Overview

Provide a concise overview of the platform's major containers.

---

## 4. Container Catalog

For each container, document:

* Name
* Responsibility
* Primary capabilities
* Owned information
* Dependencies
* Interactions

Only include containers supported by the project documentation.

---

## 5. Container Relationships

Describe how containers collaborate.

For each relationship, explain:

* source container;
* target container;
* purpose of the interaction;
* information exchanged.

---

## 6. Data Ownership

Identify which container is responsible for each major category of information.

Avoid duplicated ownership.

---

## 7. Architectural Responsibilities

Summarize how responsibilities are distributed across containers to preserve:

* modularity;
* cohesion;
* separation of concerns;
* traceability.

---

## 8. Container Diagram

Generate a Container Diagram representing:

* every documented container;
* container responsibilities;
* interactions between containers.

The diagram should remain conceptual and implementation-independent.

---

# Diagram Requirements

Generate:

container-architecture.mmd

Requirements:

* Mermaid
* Left-to-right layout
* One node per container
* Human-readable labels
* Clear directional relationships
* Maximum readability
* No components
* No classes
* No database tables
* No infrastructure
* No deployment details
* No protocols unless explicitly documented

---

# Outputs

Produce:

```text
docs/architecture/container-architecture.md
```

and

```text
docs/architecture/diagrams/container-architecture.mmd
```

---

# Acceptance Criteria

The task is complete only if:

* every documented container is represented;
* every container has a clearly defined responsibility;
* ownership boundaries are explicit;
* container interactions are documented;
* the written documentation matches the diagram;
* no implementation details are introduced;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* required documentation is missing;
* undocumented containers are introduced;
* responsibilities overlap without justification;
* ownership is ambiguous;
* implementation details appear;
* the diagram contradicts the written documentation.

---

# Notes

This task represents the **Container level** of the C4 Model.

Subsequent tasks will refine the architecture by decomposing individual containers into components and their internal interactions while preserving the boundaries defined in this document.
