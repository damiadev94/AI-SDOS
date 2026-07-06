# TASK-ARCH-011 — Generate Decision Traceability

## Metadata

| Field      | Value                                                               |
| ---------- | ------------------------------------------------------------------- |
| ID         | TASK-ARCH-011                                                       |
| Name       | Generate Decision Traceability                                      |
| Category   | Architecture Governance                                             |
| Priority   | Medium                                                              |
| Depends On | TASK-ARCH-001 through TASK-ARCH-009                                 |
| Outputs    | decision-traceability.md                                            |

---

# Objective

Produce the Decision Traceability documentation for AI-SDOS.

The objective is to surface every significant architectural decision documented in the project — whether recorded as formal ADRs or captured narratively in foundational documents — and organize them into a traceable record that shows what was decided, why, and what consequences follow.

Note: As of PROJECT_STATE.md, no formal ADRs exist yet. This document must not invent ADRs. Instead, it must:

1. Extract and catalog the architectural decisions documented narratively in SYSTEM_ARCHITECTURE.md (Dependency Principles, Architectural Style, Architectural Constraints) and other foundational documents.
2. Provide the ADR template and creation process so formal ADRs can be added as decisions are made.
3. Record the Known Gap as documented in PROJECT_STATE.md.

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
* All generated architecture views
* All ADRs (if any exist)

If required information is missing, document the gap rather than stopping execution.

---

# Responsibilities

The task must:

* extract all significant architectural decisions documented anywhere in the project;
* organize decisions by topic area;
* for each decision document: what was decided, why, and what consequences follow;
* provide the ADR template for future decisions;
* record which decisions lack formal ADRs as a known gap;
* trace each extracted decision back to its source document.

The task must **not**:

* invent decisions not documented in the project;
* create formal ADRs without documented rationale;
* change or reinterpret documented decisions.

---

# Required Sections

## 1. Purpose

Explain why the Decision Traceability view exists.

---

## 2. Decision Catalog

For each identified architectural decision:

* Decision ID (narrative reference or ADR ID)
* Decision Statement
* Rationale (from source documentation)
* Consequences
* Source Document and Section
* Status (Accepted / Proposed / Superseded)

---

## 3. Decision Areas

Group decisions by architectural area:

* Architectural Style decisions
* Knowledge Management decisions
* Orchestration decisions
* Governance decisions
* External System decisions

---

## 4. ADR Template

Provide the standard ADR template to be used for future formal decisions.

---

## 5. Known Gaps

Explicitly document areas where architectural decisions have been made but not formally recorded as ADRs, as noted in PROJECT_STATE.md.

---

## 6. Decision Dependency Map

Show how decisions relate to each other — which decisions depend on or constrain others.

---

# Outputs

Produce:

```text
docs/architecture/decision-traceability.md
```

---

# Acceptance Criteria

The task is complete only if:

* all documented architectural decisions are cataloged;
* each decision has a source document reference;
* the ADR template is provided;
* known gaps are explicitly documented;
* the decision dependency map is present;
* no undocumented decisions are invented;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* documented decisions are omitted;
* decisions are invented without source documentation;
* the ADR template is absent;
* known gaps are not acknowledged;
* source references are missing.
