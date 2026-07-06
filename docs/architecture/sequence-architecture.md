# SEQUENCE_ARCHITECTURE

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

The Sequence Architecture view documents the key operational sequences of AI-SDOS.

While the Information Flow view describes what information moves and where, the Sequence Architecture makes the **temporal order** explicit: who acts first, what is the message exchanged, what response is expected, and where do governance gates and human actors intervene in time.

This view is particularly useful for understanding the lifecycle of specific engineering activities and for identifying the sequence of interactions between containers and human actors during a given operation.

*(Source: TASK-ARCH-008)*

---

# 2. Identified Sequences

The following sequences represent the key operational activities of AI-SDOS. They were selected because they cover the complete engineering lifecycle from knowledge establishment to validated artifact delivery.

| Sequence ID | Name | Trigger |
|---|---|---|
| SEQ-001 | Documentation Artifact Generation | Human actor initiates a documentation task |
| SEQ-002 | Architecture View Generation | Human actor initiates an architecture view task |
| SEQ-003 | Specification Creation and Approval | Human actor requests a specification |
| SEQ-004 | Agent Task Execution | Agent Orchestrator assigns a task to a Specialized Agent |

Each sequence has a corresponding Mermaid diagram in `docs/architecture/diagrams/sequences/`.

---

# 3. Sequence Descriptions

---

## SEQ-001: Documentation Artifact Generation

**Trigger:** Project Architect instructs AI-SDOS to generate a documentation artifact (e.g., FOUNDATION.md, DOMAIN_DISCOVERY.md).

**Participants:**
* Project Architect (Human Actor)
* Orchestration Engine (Workflow Engine, Task Manager, Agent Orchestrator)
* Knowledge Repository
* AI Agent Runtime (Documentation Agent, Review Agent, Validation Agent)
* Tool Integration Gateway (AI Provider Adapter)
* Execution Engine (Artifact Producer, Validation Engine)
* Governance Module (Documentation Standards Validator, Approval Gate Manager, Audit Logger)

**Steps:**
1. Project Architect submits documentation task instruction to the Orchestration Engine.
2. Workflow Engine creates a documentation workflow.
3. Task Manager instantiates tasks: Generate → Review → Validate.
4. Agent Orchestrator assigns the Generate task to the Documentation Agent.
5. Documentation Agent reads relevant context from Knowledge Repository.
6. Documentation Agent invokes AI Provider via Tool Integration Gateway.
7. AI Provider returns generated content.
8. Documentation Agent produces draft document artifact.
9. Agent Orchestrator assigns the Review task to the Review Agent.
10. Review Agent reads the draft and project standards from Knowledge Repository.
11. Review Agent invokes AI Provider for review analysis.
12. Review Agent produces review report (quality, terminology, completeness).
13. Agent Orchestrator assigns the Validate task to the Validation Agent.
14. Validation Agent reads draft, review report, and acceptance criteria.
15. Validation Agent produces validation result.
16. Artifact Producer (Execution Engine) assembles production-ready document.
17. Validation Engine checks against acceptance criteria and DDS standards.
18. Documentation Standards Validator (Governance Module) verifies DDS compliance.
19. Approval Gate Manager routes to Project Architect for approval.
20. Project Architect reviews and approves or rejects.
21. If approved: Audit Logger records approval event; artifact is persisted to Documentation Store (Knowledge Repository).
22. If rejected: Task Manager re-queues or marks task as failed; Project Architect receives rejection report.

**Outputs:**
* Approved documentation artifact stored in the Knowledge Repository.

**Governance Gates:**
* Step 17: Validation Engine acceptance criteria check (automated).
* Step 18: DDS compliance check (automated).
* Steps 19–20: Human approval gate (Project Architect).

---

## SEQ-002: Architecture View Generation

**Trigger:** Project Architect initiates generation of an architecture view (e.g., System Context, Container Architecture).

**Participants:**
* Project Architect (Human Actor)
* Orchestration Engine
* Knowledge Repository (including existing architecture views as context)
* AI Agent Runtime (Architecture Agent, Review Agent, Validation Agent)
* Tool Integration Gateway (AI Provider Adapter)
* Execution Engine
* Governance Module

**Steps:**
1. Project Architect submits architecture task (specifying the target view: e.g., System Context).
2. Workflow Engine creates an architecture view workflow.
3. Task Manager instantiates tasks: Generate → Review → Validate.
4. Agent Orchestrator assigns the Generate task to the Architecture Agent.
5. Architecture Agent reads foundational docs + all prior architecture views from Knowledge Repository (prerequisite views must exist).
6. Architecture Agent invokes AI Provider for view and diagram generation.
7. Architecture Agent produces draft architecture document (.md) and Mermaid diagram (.mmd).
8. Review Agent reads draft, project UL, and existing views for consistency review.
9. Review Agent produces consistency and quality review report.
10. Validation Agent verifies acceptance criteria for the specific architecture task.
11. Artifact Producer assembles both the .md and .mmd files.
12. Validation Engine checks completeness, absence of implementation details, and UL consistency.
13. Governance Module applies architectural consistency check.
14. Approval Gate Manager routes to Project Architect.
15. Project Architect approves.
16. Audit Logger records; artifacts persisted to Architecture Repository (Knowledge Repository).

**Outputs:**
* Approved architecture view document and diagram stored in Architecture Repository.

**Governance Gates:**
* Step 12: Automated validation (completeness, UL consistency, no implementation details).
* Step 13: Architectural consistency check.
* Steps 14–15: Human approval gate.

---

## SEQ-003: Specification Creation and Approval

**Trigger:** Technical Lead or Project Architect requests a specification for a defined scope.

**Participants:**
* Technical Lead / Project Architect (Human Actor)
* Orchestration Engine
* Knowledge Repository
* AI Agent Runtime (Documentation Agent, Review Agent, Validation Agent)
* Tool Integration Gateway
* Execution Engine
* Governance Module

**Steps:**
1. Technical Lead defines specification scope and submits to Orchestration Engine.
2. Workflow Engine creates a specification workflow.
3. Task Manager instantiates tasks: Generate Spec → Review → Validate → Approve.
4. Agent Orchestrator assigns Generate task to Documentation Agent (or Architecture Agent for architectural specs).
5. Agent reads architectural context, domain model, and UL from Knowledge Repository.
6. Agent invokes AI Provider and produces draft specification.
7. Review Agent checks draft for completeness, unambiguous acceptance criteria, and alignment with architecture.
8. Validation Agent verifies the specification satisfies specification standards.
9. Execution Engine validates against specification acceptance criteria template.
10. Governance Module: Documentation Standards Validator checks specification structure.
11. Approval Gate Manager routes to Project Architect for formal approval.
12. Project Architect reviews and approves.
13. Audit Logger records approval; specification persisted to Documentation Store (Knowledge Repository).
14. Specification is now available as input to Orchestration workflows.

**Outputs:**
* Approved specification stored in Knowledge Repository, available to trigger implementation workflows.

**Governance Gates:**
* Step 9: Automated validation (spec structure, acceptance criteria completeness).
* Step 10: DDS/specification standard compliance.
* Steps 11–12: Human approval gate (mandatory — specifications drive implementation).

---

## SEQ-004: Agent Task Execution

**Trigger:** Agent Orchestrator has a ready task to assign to a Specialized Agent.

This sequence zooms into the micro-level of a single agent task execution, showing the internal mechanics that underlie all higher-level sequences.

**Participants:**
* Agent Orchestrator (Orchestration Engine)
* Task Manager (Orchestration Engine)
* Specialized Agent (any: Documentation, Architecture, Implementation, Testing, Analysis, Review, or Validation)
* Knowledge Repository
* Tool Integration Gateway (AI Provider Adapter, optionally MCP Server Adapter)
* Execution Engine
* Governance Module (cross-cutting)

**Steps:**
1. Task Manager marks task as ready (dependencies resolved).
2. Agent Orchestrator selects the appropriate Specialized Agent for the task type.
3. Agent Orchestrator packages task assignment (task definition + context references).
4. Specialized Agent receives assignment.
5. Agent reads required artifacts from Knowledge Repository (read-only access).
6. Agent sends inference request to AI Provider via Tool Integration Gateway.
7. (Optional) Agent invokes MCP Server for additional tool capabilities.
8. Agent receives model response and tool results.
9. Agent produces artifact candidate.
10. Agent delivers artifact candidate to Execution Engine (Artifact Producer).
11. Artifact Producer assembles production-ready artifact.
12. Validation Engine verifies artifact against task acceptance criteria.
13. If validation fails: Agent Orchestrator notified; Task Manager updates task state to Failed; rejection report generated.
14. If validation passes: Governance Module receives artifact for policy and approval check.
15. Governance Module applies standards and (if required) routes to human for approval.
16. Approved artifact persisted to Knowledge Repository.
17. Task Manager marks task as Completed; dependent tasks may be unblocked.

**Outputs:**
* Approved artifact in Knowledge Repository (or rejection report).
* Task state updated in Task Manager.

**Governance Gates:**
* Step 12: Automated acceptance criteria validation.
* Step 14–15: Governance policy and (conditional) human approval.

---

# 4. Cross-Sequence Patterns

The following patterns appear across all identified sequences:

**Read-Before-Generate:** Every agent reads from the Knowledge Repository before producing any artifact. This ensures that generated outputs are grounded in existing documented knowledge.

**Generator → Reviewer → Validator Chain:** Every significant artifact passes through at least three agents: the generating agent, the Review Agent, and the Validation Agent. This three-stage pattern prevents low-quality artifacts from reaching the Execution Engine.

**Automated Gate → Human Gate:** Every sequence has at least one automated validation step (Validation Engine) followed by a human approval gate for strategic artifacts. Automated gates verify structural completeness; human gates validate strategic alignment and judgment.

**Rejection Loops:** Rejected artifacts return to the Orchestration Engine with a rejection report. The Task Manager decides whether to re-queue (for retry) or mark the task as permanently failed. Rejected artifacts never reach the Knowledge Repository.

**Audit at Every State Change:** The Audit Logger records every significant state transition. This pattern is invisible in sequence diagrams but applies universally.

---

# 5. Sequence Diagrams

See:

* `docs/architecture/diagrams/sequences/seq-001-documentation-generation.mmd`
* `docs/architecture/diagrams/sequences/seq-002-architecture-view-generation.mmd`
* `docs/architecture/diagrams/sequences/seq-003-specification-creation.mmd`
* `docs/architecture/diagrams/sequences/seq-004-agent-task-execution.mmd`

---

# Related Documents

* PROJECT_STATE.md
* SYSTEM_ARCHITECTURE.md
* container-architecture.md
* component-architecture.md
* information-flow.md
* agent-integration.md
* Architecture Decision Records (ADRs) — none exist yet

---

# Change Log

| Version | Date       | Description                                                            |
| ------- | ---------- | ---------------------------------------------------------------------- |
| v0.1    | 2026-07-05 | Initial Sequence Architecture generated from project documentation. |
