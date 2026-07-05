# TASK-ARCH-002 — Generate System Context

## Metadata

| Field      | Value                                 |
| ---------- | ------------------------------------- |
| ID         | TASK-ARCH-002                         |
| Name       | Generate System Context               |
| Category   | Architecture Documentation            |
| Priority   | High                                  |
| Depends On | TASK-ARCH-001                         |
| Outputs    | system-context.md, system-context.mmd |

---

# Objective

Produce the System Context documentation for AI-SDOS.

The objective is to describe the platform from an external perspective by identifying:

* the system boundary;
* external actors;
* external systems;
* high-level interactions.

The generated artifacts must explain how AI-SDOS fits into its surrounding ecosystem without exposing its internal architecture.

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
* Relevant ADRs

If required information is missing or inconsistent, stop execution and report the issue.

---

# Responsibilities

The task must:

* define the system boundary;
* identify all human actors;
* identify all external systems;
* describe each interaction at a conceptual level;
* explain the responsibilities that belong to AI-SDOS;
* explain the responsibilities delegated to external systems.

The task must **not**:

* describe internal components;
* describe containers or services;
* define APIs or protocols;
* describe infrastructure;
* define implementation details.

---

# Required Sections

## 1. Purpose

Explain why the System Context view exists.

---

## 2. System Boundary

Define what belongs to AI-SDOS and what remains external.

---

## 3. Human Actors

Identify every human role interacting with the platform.

For each actor describe:

* role;
* responsibilities;
* interaction with AI-SDOS.

---

## 4. External Systems

Identify every external system that exchanges information with AI-SDOS.

Examples may include:

* Git repositories
* AI providers
* IDEs
* MCP servers
* Issue tracking platforms
* Documentation platforms
* CI/CD systems

Only include systems documented in the project.

---

## 5. Interaction Summary

Describe, at a conceptual level:

* who communicates with AI-SDOS;
* what information is exchanged;
* why the interaction exists.

---

## 6. Responsibilities

Separate clearly:

### Responsibilities of AI-SDOS

### Responsibilities of External Systems

---

## 7. Context Narrative

Provide a concise description of how AI-SDOS operates within its ecosystem.

---

## 8. Context Diagram

Generate a System Context diagram showing:

* AI-SDOS
* Human actors
* External systems
* High-level relationships

No internal architecture should appear.

---

# Diagram Requirements

Generate:

system-context.mmd

Requirements:

* Mermaid
* Left-to-right layout
* AI-SDOS represented as a single system
* External actors outside the system boundary
* External systems outside the system boundary
* Human-readable labels
* High readability
* No containers
* No components
* No implementation details

---

# Outputs

Produce:

```text
docs/architecture/system-context.md
```

and

```text
docs/architecture/diagrams/system-context.mmd
```

---

# Acceptance Criteria

The task is complete only if:

* the system boundary is explicitly defined;
* every documented external actor is represented;
* every documented external system is represented;
* responsibilities are clearly separated;
* the context diagram matches the written documentation;
* no internal architectural elements appear;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* required documentation is missing;
* undocumented actors are introduced;
* undocumented external systems are invented;
* implementation details appear;
* the system boundary is ambiguous;
* the generated diagram contradicts the project documentation.
