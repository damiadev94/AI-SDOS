# TASK-ARCH-006 — Generate Information Flow

## Metadata

| Field      | Value                                                   |
| ---------- | ------------------------------------------------------- |
| ID         | TASK-ARCH-006                                           |
| Name       | Generate Information Flow                               |
| Category   | Architecture Documentation                              |
| Priority   | High                                                    |
| Depends On | TASK-ARCH-001, TASK-ARCH-002, TASK-ARCH-003, TASK-ARCH-004 |
| Outputs    | information-flow.md, information-flow.mmd               |

---

# Objective

Produce the Information Flow documentation for AI-SDOS.

The objective is to describe how information moves through the platform — from human actors defining objectives, through the knowledge and orchestration layers, through agent execution, to validated artifact persistence — and to make explicit what information is produced, transformed, and consumed at each stage.

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
* component-architecture.md
* Relevant ADRs

If required information is missing or inconsistent, stop execution and report the issue.

---

# Responsibilities

The task must:

* identify the primary information flows across the platform lifecycle;
* describe each flow stage: what information enters, what is produced, what is consumed;
* show how information moves between containers and components;
* identify the role of the Knowledge Repository as the central information hub;
* describe how governance intersects information flows.

The task must **not**:

* describe API contracts or data schemas;
* define message formats or protocols;
* describe infrastructure;
* introduce undocumented flows.

---

# Required Sections

## 1. Purpose

Explain why the Information Flow view exists and what it adds to the structural views.

---

## 2. Flow Overview

Provide a concise narrative of how information moves through the platform from input to output.

---

## 3. Primary Flows

Document each primary information flow.

For each flow:

* Flow Name
* Trigger
* Stages (ordered)
* Information Produced at Each Stage
* Consumers of the Output
* Governance Checkpoints

---

## 4. Knowledge Repository Centrality

Explain how the Knowledge Repository acts as the central information hub and how every major flow intersects it.

---

## 5. Governance Intersections

Describe where the Governance Module intersects each information flow and what it validates or enforces at each point.

---

## 6. Information Flow Diagram

Generate a diagram showing the primary information flows across containers.

---

# Diagram Requirements

Generate:

information-flow.mmd

Requirements:

* Mermaid flowchart or sequence diagram (choose the most readable for the content)
* Shows information flows across containers
* Labels flows with the information category
* Highlights governance checkpoints
* No implementation details
* No API contracts

---

# Outputs

Produce:

```text
docs/architecture/information-flow.md
```

and

```text
docs/architecture/diagrams/information-flow.mmd
```

---

# Acceptance Criteria

The task is complete only if:

* every primary information flow is documented;
* every stage in each flow identifies what information is produced and consumed;
* the Knowledge Repository's central role is explicitly described;
* governance checkpoints are identified in every flow;
* the diagram matches the written documentation;
* no undocumented flows or containers are introduced;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* required documentation is missing;
* flows reference undocumented containers or components;
* governance intersections are absent;
* implementation details appear;
* the diagram contradicts the written documentation.
