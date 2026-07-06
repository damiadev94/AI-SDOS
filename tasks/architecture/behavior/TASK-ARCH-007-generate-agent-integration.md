# TASK-ARCH-007 — Generate Agent Integration

## Metadata

| Field      | Value                                                               |
| ---------- | ------------------------------------------------------------------- |
| ID         | TASK-ARCH-007                                                       |
| Name       | Generate Agent Integration                                          |
| Category   | Architecture Documentation                                          |
| Priority   | High                                                                |
| Depends On | TASK-ARCH-001, TASK-ARCH-002, TASK-ARCH-003, TASK-ARCH-004         |
| Outputs    | agent-integration.md, agent-integration.mmd                         |

---

# Objective

Produce the Agent Integration documentation for AI-SDOS.

The objective is to describe how Specialized AI Agents are integrated into the platform — how they receive assignments, what context they consume, what capabilities they invoke, and how their outputs are validated and persisted.

This view describes the collaboration model between the Orchestration Engine, the AI Agent Runtime, the Tool Integration Gateway, and the Execution Engine from the perspective of agent-driven engineering activity.

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
* Relevant ADRs

If required information is missing or inconsistent, stop execution and report the issue.

---

# Responsibilities

The task must:

* identify every Specialized Agent documented in the architecture;
* describe the responsibility and capabilities of each agent;
* describe how agents receive task assignments from the Orchestration Engine;
* describe how agents consume knowledge from the Knowledge Repository;
* describe how agents invoke external capabilities via the Tool Integration Gateway;
* describe how agent outputs flow through the Execution Engine and Governance Module.

The task must **not**:

* define prompt templates or AI model configurations;
* describe agent implementation internals;
* introduce undocumented agent types;
* define API contracts.

---

# Required Sections

## 1. Purpose

Explain why the Agent Integration view exists.

---

## 2. Agent Catalog

For each Specialized Agent:

* Name
* Responsibility
* Primary Capabilities
* Inputs (information consumed)
* Outputs (artifacts produced)
* External Tool Dependencies

---

## 3. Assignment and Delegation Model

Describe how the Agent Orchestrator assigns tasks to agents.

---

## 4. Context Consumption

Describe how agents read project knowledge from the Knowledge Repository to build their execution context.

---

## 5. Tool Invocation

Describe how agents invoke external capabilities through the Tool Integration Gateway.

---

## 6. Output Lifecycle

Describe how agent outputs travel from production to validated persistence in the Knowledge Repository.

---

## 7. Agent Collaboration Patterns

Describe how agents collaborate — for example, how the Review Agent validates outputs from other agents before they reach the Validation Agent.

---

## 8. Agent Integration Diagram

Generate a diagram showing the integration model for agents.

---

# Diagram Requirements

Generate:

agent-integration.mmd

Requirements:

* Mermaid
* Shows agent assignment, context consumption, tool invocation, and output lifecycle
* Labels flows by information category
* No prompt templates
* No model configuration details
* No implementation details

---

# Outputs

Produce:

```text
docs/architecture/agent-integration.md
```

and

```text
docs/architecture/diagrams/agent-integration.mmd
```

---

# Acceptance Criteria

The task is complete only if:

* every documented Specialized Agent is described;
* the assignment model is explicitly described;
* context consumption from the Knowledge Repository is documented;
* tool invocation via the Tool Integration Gateway is documented;
* the output lifecycle through Execution Engine and Governance is documented;
* the diagram matches the written documentation;
* terminology is consistent with the Ubiquitous Language.

---

# Failure Conditions

Fail the task if:

* required documentation is missing;
* undocumented agent types are introduced;
* agent responsibilities overlap without justification;
* the output lifecycle is incomplete;
* implementation details appear.
