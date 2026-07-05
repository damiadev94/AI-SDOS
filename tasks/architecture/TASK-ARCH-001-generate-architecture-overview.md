# TASK-ARCH-001 — Generate Architecture Overview

## Metadata

| Field      | Value                                                      |
| ---------- | ---------------------------------------------------------- |
| ID         | TASK-ARCH-001                                              |
| Name       | Generate Architecture Overview                             |
| Category   | Architecture Documentation                                 |
| Priority   | High                                                       |
| Depends On | SPEC-001, SPEC-002, SPEC-003, SPEC-004, SPEC-005, SPEC-006 |
| Outputs    | architecture-overview.md, architecture-overview.mmd        |

---

# Objective

Produce a high-level architectural overview of AI-SDOS that explains the system as a whole without implementation details.

The objective is to create the first architectural artifact that provides readers with an overall understanding of the platform before exploring lower-level documentation.

This document must communicate:

* the purpose of the system
* its architectural vision
* its major subsystems
* the relationships between them
* the overall information flow

without describing internal implementations.

---

# Inputs

Read and analyze:

* PROJECT_STATE.md
* FOUNDATION.md
* DOMAIN_DISCOVERY.md
* UBIQUITOUS_LANGUAGE.md
* DOMAIN_MODEL.md
* SYSTEM_ARCHITECTURE.md
* All Architecture Decision Records (ADRs)

If inconsistencies are found, stop and report them instead of making assumptions.

---

# Responsibilities

The task must:

* identify the major architectural domains
* identify the primary responsibilities of each domain
* identify the interactions between domains
* identify external actors
* describe the architectural philosophy
* describe the overall system boundaries
* explain how information flows across the platform

The task must **not**:

* define APIs
* define database schemas
* define deployment infrastructure
* define implementation details
* create sequence diagrams
* invent missing architecture

---

# Required Sections

The generated document must contain at least the following sections.

## 1. Purpose

Why AI-SDOS exists.

---

## 2. Architectural Vision

The overall architectural philosophy.

---

## 3. Design Principles

Summarize the core principles guiding the architecture.

---

## 4. High-Level Building Blocks

Describe each major subsystem.

For example:

* User Layer
* Orchestration Layer
* AI Agent Layer
* Knowledge Layer
* Specification Layer
* Execution Layer
* Persistence Layer
* External Integrations

(The actual blocks must come from the project documentation.)

---

## 5. System Boundaries

Explain what belongs to AI-SDOS and what is external.

---

## 6. Information Flow

Describe, at a conceptual level, how work moves through the platform.

---

## 7. Architectural Characteristics

Summarize qualities such as:

* modularity
* extensibility
* scalability
* traceability
* maintainability
* human-in-the-loop

---

## 8. Key Architectural Decisions

Reference relevant ADRs that influence the overall architecture.

---

## 9. Overview Diagram

Generate one high-level architecture diagram illustrating:

* major subsystems
* external actors
* primary relationships

The diagram must avoid implementation details.

---

# Diagram Requirements

Generate:

architecture-overview.mmd

Requirements:

* Mermaid
* Left-to-right layout
* High-level only
* Maximum readability
* No implementation classes
* No database tables
* No protocols
* No low-level dependencies

---

# Outputs

Produce:

```
docs/architecture/architecture-overview.md
```

and

```
docs/architecture/diagrams/architecture-overview.mmd
```

---

# Acceptance Criteria

The task is complete only if:

* the entire platform can be understood in under five minutes by a new contributor
* every major subsystem is documented
* responsibilities are clearly separated
* architectural philosophy is explained
* no implementation details are introduced
* the diagram matches the written documentation
* terminology is consistent with the Ubiquitous Language
* no unsupported assumptions are made

---

# Failure Conditions

Fail the task if:

* required documentation is missing
* architecture is inconsistent
* undocumented components are invented
* implementation details appear
* terminology differs from the project glossary
* the generated diagram contradicts the written documentation
