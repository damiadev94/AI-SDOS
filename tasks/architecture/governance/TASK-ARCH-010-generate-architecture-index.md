# TASK-ARCH-010 — Generate Architecture Index

## Metadata

| Field      | Value                                                                              |
| ---------- | ---------------------------------------------------------------------------------- |
| ID         | TASK-ARCH-010                                                                      |
| Name       | Generate Architecture Index                                                        |
| Category   | Architecture Governance                                                            |
| Priority   | Medium                                                                             |
| Depends On | TASK-ARCH-001 through TASK-ARCH-009                                                |
| Outputs    | architecture-index.md                                                              |

---

# Objective

Produce the Architecture Index for AI-SDOS.

The objective is to create a single navigable index of all architecture documentation — views, diagrams, decision records, and governance artifacts — so that any reader can understand what architectural documentation exists, where to find it, and how the views relate to each other.

---

# Inputs

Read and analyze:

* All previously generated architecture views (TASK-ARCH-001 through TASK-ARCH-009 outputs)
* PROJECT_STATE.md
* Relevant ADRs

If required information is missing or inconsistent, document the gap in the index rather than stopping execution.

---

# Responsibilities

The task must:

* enumerate every generated architecture view;
* enumerate every generated diagram;
* enumerate all existing ADRs (or document their absence);
* describe the purpose and C4/domain level of each view;
* show the dependency relationships between views;
* provide navigation guidance for different reader types.

The task must **not**:

* duplicate content from other architecture documents;
* summarize architectural decisions not yet documented;
* introduce new architectural content.

---

# Required Sections

## 1. Purpose

Explain why the Architecture Index exists.

---

## 2. Architecture Views Inventory

A complete catalog of all architecture view documents.

For each view:

* Document name
* Location
* Purpose (one sentence)
* C4 level or view type
* Depends on

---

## 3. Diagram Inventory

A complete catalog of all architecture diagrams.

For each diagram:

* File name
* Location
* Associated view
* Diagram type

---

## 4. ADR Inventory

A complete catalog of all Architecture Decision Records, or an explicit statement that none exist yet.

---

## 5. View Dependency Map

Show how the architecture views depend on each other (reading order and prerequisite relationships).

---

## 6. Reading Guide

Provide guidance for different reader types on which views to read and in what order:

* For a first-time reader
* For a Project Architect
* For a Software Engineer
* For a new contributor

---

## 7. Documentation Maturity

Report the current maturity status of all architecture documentation.

---

# Outputs

Produce:

```text
docs/architecture/architecture-index.md
```

---

# Acceptance Criteria

The task is complete only if:

* every generated architecture view is listed;
* every generated diagram is listed;
* ADR status is explicitly documented;
* the view dependency map is accurate;
* the reading guide covers at least three reader types;
* documentation maturity is reported;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* architecture views are missing from the inventory;
* diagrams are missing from the inventory;
* the ADR section is absent;
* new architectural content is introduced;
* the dependency map is inaccurate.
