# AGENT_INTEGRATION

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

The Agent Integration view describes how Specialized AI Agents are integrated into AI-SDOS.

Where the Container Architecture describes the AI Agent Runtime as a container and the Component Architecture decomposes it into individual agents, this view describes the **operational model** of agent integration: how agents receive work, what information they consume, how they invoke external capabilities, how they collaborate with each other, and how their outputs travel to validated persistence.

This view answers the question: *how does the platform coordinate AI agents to produce trusted, traceable engineering artifacts?*

*(Source: TASK-ARCH-007)*

---

# 2. Agent Catalog

---

## Documentation Agent

| Field | Value |
|---|---|
| Responsibility | Generates, updates, and reviews project documentation artifacts |
| Primary Capabilities | Document generation; documentation review; gap analysis; consistency checking |
| Inputs | Project documentation context from Knowledge Repository; task assignment from Agent Orchestrator |
| Outputs | Draft documentation artifacts (Foundation, Domain Discovery, UL, Domain Model, System Architecture, and derivatives) |
| External Tool Dependencies | AI Provider (LLM inference) |

---

## Architecture Agent

| Field | Value |
|---|---|
| Responsibility | Produces and validates architectural views and diagrams |
| Primary Capabilities | Architecture view generation; Mermaid diagram generation; architectural review; C4 view production |
| Inputs | All foundational project documentation; existing architecture views; task assignment |
| Outputs | Architecture view documents (.md); Mermaid diagram files (.mmd) |
| External Tool Dependencies | AI Provider (LLM inference) |

---

## Implementation Agent

| Field | Value |
|---|---|
| Responsibility | Transforms validated specifications into implementation artifacts |
| Primary Capabilities | Code generation; implementation guidance; specification-to-code translation |
| Inputs | Approved specifications; architectural context; ubiquitous language; task assignment |
| Outputs | Implementation artifact candidates (code, configuration, scripts) |
| External Tool Dependencies | AI Provider (LLM inference); IDE (via Tool Integration Gateway) |

---

## Testing Agent

| Field | Value |
|---|---|
| Responsibility | Generates and coordinates test artifacts for validated specifications |
| Primary Capabilities | Test generation; acceptance criteria verification; test plan production |
| Inputs | Approved specifications; acceptance criteria; implementation artifacts; task assignment |
| Outputs | Test artifact candidates (test files, test plans) |
| External Tool Dependencies | AI Provider (LLM inference); CI/CD Platform (via Tool Integration Gateway) |

---

## Analysis Agent

| Field | Value |
|---|---|
| Responsibility | Performs analysis tasks: impact assessment, gap detection, consistency checking |
| Primary Capabilities | Impact analysis; documentation gap detection; inconsistency detection; dependency analysis |
| Inputs | All project artifacts from Knowledge Repository; analysis scope from task assignment |
| Outputs | Analysis reports; gap reports; inconsistency reports |
| External Tool Dependencies | AI Provider (LLM inference) |

---

## Review Agent

| Field | Value |
|---|---|
| Responsibility | Reviews generated artifacts for quality, correctness, and standards alignment |
| Primary Capabilities | Artifact review; quality assessment; consistency validation; terminology verification against Ubiquitous Language |
| Inputs | Artifact candidate from another agent; project standards and UL from Knowledge Repository |
| Outputs | Review report; quality assessment; pass/fail recommendation |
| External Tool Dependencies | AI Provider (LLM inference) |

---

## Validation Agent

| Field | Value |
|---|---|
| Responsibility | Verifies that artifacts satisfy their documented acceptance criteria |
| Primary Capabilities | Acceptance criteria matching; artifact completeness checking; specification compliance validation |
| Inputs | Artifact candidate; acceptance criteria from specifications; review report from Review Agent |
| Outputs | Validation result (pass/fail with specific findings) |
| External Tool Dependencies | AI Provider (LLM inference) |

*(Source: SYSTEM_ARCHITECTURE.md — AI Agent Layer; DOMAIN_DISCOVERY.md — AI Stakeholders; component-architecture.md — AI Agent Runtime)*

---

# 3. Assignment and Delegation Model

The agent assignment model follows a strict delegation chain:

1. The **Workflow Engine** (Orchestration Engine) creates a workflow for an engineering objective.
2. The **Task Manager** (Orchestration Engine) instantiates tasks from the workflow, resolves dependencies, and queues tasks that are ready for execution.
3. The **Agent Orchestrator** (Orchestration Engine) receives a ready task and selects the appropriate Specialized Agent based on the task's declared capability requirement.
4. The Agent Orchestrator packages the task with a context reference (pointer to the relevant Knowledge Repository artifacts) and delivers the assignment to the targeted Specialized Agent.
5. The Specialized Agent acknowledges the assignment and begins execution.
6. Upon completion, the agent returns its output to the Execution Engine (not directly to the Agent Orchestrator).
7. The Execution Engine reports the task outcome (pass/fail) back to the Task Manager, which updates the task state and may unblock dependent tasks.

**Key constraints:**
* The Agent Orchestrator does not decide *how* a task is executed — only *which agent* executes it.
* Agents may not self-assign tasks; all assignments flow through the Agent Orchestrator.
* Agents may not communicate directly with each other — agent collaboration occurs through a defined sequencing in the Task Manager (one agent's output becomes a subsequent agent's input as a new task).

*(Source: SYSTEM_ARCHITECTURE.md — Orchestration Layer; component-architecture.md — Orchestration Engine)*

---

# 4. Context Consumption

Before executing a task, each Specialized Agent constructs an execution context by reading from the Knowledge Repository.

The context package typically includes:

| Context Component | Source in Knowledge Repository | Purpose |
|---|---|---|
| Project Foundation | Documentation Store (FOUNDATION.md) | Platform purpose and principles |
| Domain knowledge | Documentation Store (DOMAIN_DISCOVERY.md, DOMAIN_MODEL.md) | Domain understanding |
| Ubiquitous Language | Documentation Store (UBIQUITOUS_LANGUAGE.md) | Consistent terminology |
| System Architecture | Documentation Store (SYSTEM_ARCHITECTURE.md) | Architectural principles |
| Existing architecture views | Architecture Repository | Consistency with prior views |
| Relevant specifications | Documentation Store (SPEC artifacts) | Acceptance criteria for the task |
| Project state | Project Manager (Knowledge Repository) | Lifecycle phase and known gaps |

Context is always **read-only** — agents never write directly to the Knowledge Repository. All writes occur through the Execution Engine after validation and governance approval.

This read-only constraint preserves the integrity of the Knowledge Repository and ensures that no agent can corrupt authoritative project knowledge.

*(Source: SYSTEM_ARCHITECTURE.md — Dependency Principles; component-architecture.md — Knowledge Repository)*

---

# 5. Tool Invocation

Specialized Agents invoke external capabilities exclusively through the **Tool Integration Gateway**.

The invocation model:

1. The agent determines that external capability is needed (e.g., AI model inference, IDE context access, MCP tool call).
2. The agent sends an invocation request to the Tool Integration Gateway.
3. The appropriate adapter (AI Provider Adapter, MCP Server Adapter, IDE Adapter, etc.) handles the external system communication.
4. The adapter returns the result to the agent.
5. The agent incorporates the result into its artifact production.

**Agents never access external systems directly.** All external communication is mediated by the Tool Integration Gateway. This ensures:
* External system dependencies are encapsulated in adapters.
* External systems can be replaced or updated without modifying agent logic.
* All external interactions are observable and auditable.

The most frequent invocations:
* **AI Provider Adapter** — every agent invokes an AI model provider for language model capabilities.
* **MCP Server Adapter** — agents with tool-augmented capabilities invoke MCP servers for extended functionality.
* **IDE Adapter** — the Implementation Agent may receive IDE context through this adapter.
* **CI/CD Adapter** — the Testing Agent and Execution Engine invoke CI/CD platforms for automated test execution.

*(Source: SYSTEM_ARCHITECTURE.md — Tool Integration Layer; component-architecture.md — Tool Integration Gateway)*

---

# 6. Output Lifecycle

An agent-produced artifact follows this lifecycle before becoming part of the authoritative knowledge base:

```
Agent produces artifact candidate
        ↓
Execution Engine: Artifact Producer assembles production-ready format
        ↓
Execution Engine: Validation Engine checks against acceptance criteria
        ↓
    [Pass?]
        ↓ No → Rejection report → Orchestration Engine (task re-queued or failed)
        ↓ Yes
Governance Module: Documentation Standards Validator checks DDS compliance
        ↓
Governance Module: Approval Gate Manager routes to human actor (if required)
        ↓
    [Approved?]
        ↓ No → Rejection → Orchestration Engine
        ↓ Yes
Governance Module: Audit Logger records approval event
        ↓
Knowledge Repository: artifact stored in Documentation Store or Architecture Repository
        ↓
Artifact is now authoritative project knowledge
```

Strategic artifacts (architecture views, foundational documentation, specifications) require human approval at the Governance Module gate. Derivative or lower-stakes artifacts may pass through automated gates only.

No artifact bypasses the Execution Engine or Governance Module before reaching the Knowledge Repository.

*(Source: SYSTEM_ARCHITECTURE.md — Execution Layer, Governance Layer)*

---

# 7. Agent Collaboration Patterns

Agents collaborate indirectly through the Task Manager's dependency model. The primary collaboration patterns are:

### Generator → Reviewer → Validator

The most common pattern for any significant artifact:
1. A Generator Agent (Documentation, Architecture, Implementation, or Testing Agent) produces the draft artifact.
2. The Task Manager creates a dependent review task and assigns it to the Review Agent.
3. The Review Agent reads the draft artifact from the Execution Engine's input queue (or a temporary staging area) and produces a review report.
4. The Task Manager creates a dependent validation task and assigns it to the Validation Agent.
5. The Validation Agent reads both the draft and the review report and produces a validation result.
6. Only a passing validation result advances the artifact to the Execution Engine.

### Analysis → Generation

For complex or uncertain tasks:
1. The Analysis Agent performs gap analysis or impact assessment.
2. Its report becomes context for a subsequent generation task.
3. The relevant Generator Agent uses the analysis report as additional context alongside the standard Knowledge Repository context.

### Sequential Architecture Views

Architecture views are produced in dependency order. The Architecture Agent produces System Context first; the output becomes context for Container Architecture generation; Container Architecture becomes context for Component Architecture, and so on. This is managed by the Task Manager's dependency graph, not by direct agent-to-agent communication.

*(Source: component-architecture.md — AI Agent Runtime, Internal Collaboration)*

---

# 8. Agent Integration Diagram

See: `docs/architecture/diagrams/agent-integration.mmd`

The diagram shows the integration model: task assignment from the Agent Orchestrator, context consumption from the Knowledge Repository, tool invocation through the Tool Integration Gateway, and the output lifecycle through the Execution Engine and Governance Module.

---

# Related Documents

* PROJECT_STATE.md
* SYSTEM_ARCHITECTURE.md
* container-architecture.md
* component-architecture.md
* information-flow.md
* Architecture Decision Records (ADRs) — none exist yet

---

# Change Log

| Version | Date       | Description                                                        |
| ------- | ---------- | ------------------------------------------------------------------ |
| v0.1    | 2026-07-05 | Initial Agent Integration generated from project documentation. |
