# TASK-ARCH-005 — Generate Domain Architecture

## Metadata

| Field      | Value                                                   |
| ---------- | ------------------------------------------------------- |
| ID         | TASK-ARCH-005                                           |
| Name       | Generate Domain Architecture                            |
| Category   | Architecture Documentation                              |
| Priority   | High                                                    |
| Depends On | TASK-ARCH-001, TASK-ARCH-002, TASK-ARCH-003             |
| Outputs    | domain-architecture.md, domain-architecture.mmd         |

---

# Objective

Produce the Domain Architecture documentation for AI-SDOS.

The objective is to describe the domain structure of the platform by identifying its bounded contexts, their responsibilities, the conceptual entities and aggregates within each context, and the relationships between contexts.

This view corresponds to the **Domain level** of the architecture — a DDD-aligned complement to the C4 structural views.

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
* container-architecture.md
* Relevant ADRs

If required information is missing or inconsistent, stop execution and report the issue.

---

# Responsibilities

The task must:

* identify every bounded context defined in the domain model;
* describe the primary responsibility of each bounded context;
* identify the principal aggregates, entities, value objects, and domain services within each context;
* describe context relationships and integration points;
* map bounded contexts to the architectural containers identified in the Container Architecture.

The task must **not**:

* introduce undocumented bounded contexts;
* describe database schemas or implementation details;
* define APIs or protocols;
* cross bounded context boundaries without documented justification.

---

# Required Sections

## 1. Purpose

Explain why the Domain Architecture view exists and how it relates to the structural views.

---

## 2. Domain Overview

Summarize the domain and the rationale for its subdivision into bounded contexts.

---

## 3. Bounded Context Catalog

For each bounded context, document:

* Name
* Responsibility
* Primary Aggregates
* Primary Entities
* Primary Value Objects
* Domain Services
* Context Relationships

---

## 4. Context Map

Describe the relationships between bounded contexts.

For each relationship:

* source context;
* target context;
* integration type;
* information exchanged.

---

## 5. Context-to-Container Mapping

Map each bounded context to the architectural container(s) that implement its responsibilities.

---

## 6. Domain Invariants

List the domain invariants that must hold across all bounded contexts.

---

## 7. Domain Diagram

Generate a domain diagram representing:

* bounded contexts as named regions;
* primary aggregates within each context;
* context relationships.

---

# Diagram Requirements

Generate:

domain-architecture.mmd

Requirements:

* Mermaid
* Left-to-right layout
* Bounded contexts as subgraph regions
* Primary aggregates as nodes within contexts
* Labeled context relationships
* No implementation details
* No database tables
* No source code constructs

---

# Outputs

Produce:

```text
docs/architecture/domain-architecture.md
```

and

```text
docs/architecture/diagrams/domain-architecture.mmd
```

---

# Acceptance Criteria

The task is complete only if:

* every bounded context from DOMAIN_MODEL.md is represented;
* every context has a clearly defined responsibility;
* context relationships are documented;
* bounded contexts map to containers from container-architecture.md;
* the diagram matches the written documentation;
* no undocumented concepts are introduced;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* required documentation is missing;
* undocumented bounded contexts are introduced;
* context boundaries are ambiguous;
* responsibilities overlap without justification;
* the diagram contradicts the documentation;
* implementation details appear.
