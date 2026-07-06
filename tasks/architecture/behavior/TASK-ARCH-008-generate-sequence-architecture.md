# TASK-ARCH-008 — Generate Sequence Architecture

## Metadata

| Field      | Value                                                                    |
| ---------- | ------------------------------------------------------------------------ |
| ID         | TASK-ARCH-008                                                            |
| Name       | Generate Sequence Architecture                                           |
| Category   | Architecture Documentation                                               |
| Priority   | Medium                                                                   |
| Depends On | TASK-ARCH-001, TASK-ARCH-002, TASK-ARCH-003, TASK-ARCH-004, TASK-ARCH-006 |
| Outputs    | sequence-architecture.md, diagrams in docs/architecture/diagrams/sequences/ |

---

# Objective

Produce the Sequence Architecture documentation for AI-SDOS.

The objective is to document the key operational sequences of the platform — the temporal interactions between containers and components for the most important engineering workflows — making explicit the order of operations, the information exchanged, and the roles involved at each step.

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
* component-architecture.md
* information-flow.md
* Relevant ADRs

If required information is missing or inconsistent, stop execution and report the issue.

---

# Responsibilities

The task must:

* identify the key operational sequences of the platform;
* document the temporal interactions for each sequence;
* show which containers and components participate in each sequence;
* identify human actor touchpoints and governance gates within sequences;
* produce one Mermaid sequence diagram per key sequence.

The task must **not**:

* describe API payloads or message formats;
* define implementation-level function calls;
* introduce undocumented operations;
* describe infrastructure or networking.

---

# Required Sections

## 1. Purpose

Explain why the Sequence Architecture view exists and what it adds beyond the structural and flow views.

---

## 2. Identified Sequences

List the key operational sequences and justify their selection.

---

## 3. Sequence Descriptions

For each sequence:

* Sequence Name
* Trigger
* Participants (containers, components, human actors)
* Steps (ordered)
* Outputs
* Governance Gates

---

## 4. Cross-Sequence Patterns

Identify recurring patterns that appear across multiple sequences.

---

## 5. Sequence Diagrams

One Mermaid sequence diagram per key sequence.

---

# Diagram Requirements

Generate one diagram per sequence in:

```text
docs/architecture/diagrams/sequences/
```

Each diagram:

* Mermaid sequenceDiagram
* Participants are containers or human actors (not source code constructs)
* Messages labeled with information category
* Governance gates explicitly shown
* No API details
* No implementation details

---

# Outputs

Produce:

```text
docs/architecture/sequence-architecture.md
```

and

```text
docs/architecture/diagrams/sequences/seq-*.mmd
```

(one file per sequence, named by sequence identifier)

---

# Acceptance Criteria

The task is complete only if:

* all key sequences are identified and documented;
* every sequence has a corresponding diagram;
* participants match documented containers and components;
* governance gates appear in each sequence;
* diagrams and written descriptions are consistent;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* required documentation is missing;
* undocumented participants are introduced;
* governance gates are absent from sequences;
* implementation details appear;
* diagrams contradict written descriptions.
