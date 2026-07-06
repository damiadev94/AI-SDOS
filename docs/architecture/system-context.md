# SYSTEM_CONTEXT

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

The System Context view describes AI-SDOS from an external perspective.

Its purpose is to define the system boundary, identify every human actor and external system that interacts with the platform, and explain the high-level interactions between them.

This view does not expose the internal architecture of AI-SDOS. It answers the question: *who uses AI-SDOS, what external systems does it exchange information with, and what is each party responsible for?*

This is the C4 Model Level 1 view for AI-SDOS.

*(Source: TASK-ARCH-002)*

---

# 2. System Boundary

## Inside AI-SDOS

AI-SDOS is responsible for:

* engineering knowledge management;
* project documentation;
* specifications;
* architectural views and decision records;
* orchestration of engineering workflows;
* coordination of specialized AI agents;
* governance and traceability.

## Outside AI-SDOS

The following concerns remain external:

* business-specific logic of managed software projects;
* application runtime behavior of managed projects;
* production infrastructure of managed projects;
* customer-facing functionality of managed projects;
* organization-specific business processes.

These concerns belong to the software projects AI-SDOS manages, not to AI-SDOS itself.

*(Source: DOMAIN_DISCOVERY.md — Domain Boundaries)*

---

# 3. Human Actors

The following human roles interact directly with AI-SDOS.

---

## Project Architect

**Responsibilities:**
* defines architectural direction;
* approves strategic decisions;
* validates architectural outputs;
* governs project evolution.

**Interaction with AI-SDOS:**
Initiates and supervises all major documentation and architectural activities. The final authority for all strategic decisions within the platform.

---

## Software Engineer

**Responsibilities:**
* implements validated specifications;
* preserves architectural consistency during implementation.

**Interaction with AI-SDOS:**
Reads approved specifications and documentation. Reports implementation status. Requests clarification on specifications.

---

## Technical Lead

**Responsibilities:**
* coordinates technical teams;
* reviews technical outputs;
* bridges product requirements and engineering execution.

**Interaction with AI-SDOS:**
Reviews documentation and specifications. Provides technical guidance during domain discovery and specification phases.

---

## Product Owner

**Responsibilities:**
* defines product requirements;
* prioritizes work;
* validates that delivered software meets product objectives.

**Interaction with AI-SDOS:**
Provides requirements as inputs to documentation and specification activities. Validates that specifications align with product goals.

---

## Domain Expert

**Responsibilities:**
* provides authoritative knowledge about the problem domain;
* validates conceptual correctness of documentation and models.

**Interaction with AI-SDOS:**
Contributes to domain discovery. Reviews and validates domain model and ubiquitous language artifacts.

---

## Quality Assurance Engineer

**Responsibilities:**
* evaluates artifacts for quality, completeness, and consistency;
* validates that implementations meet acceptance criteria.

**Interaction with AI-SDOS:**
Reviews specifications and documentation for quality. Participates in validation workflows.

---

## Project Maintainer

**Responsibilities:**
* maintains the health of the project knowledge base;
* ensures documentation remains current;
* manages project lifecycle transitions.

**Interaction with AI-SDOS:**
Manages documentation updates. Monitors project state. Coordinates lifecycle transitions.

*(Source: DOMAIN_DISCOVERY.md — Human Stakeholders; UBIQUITOUS_LANGUAGE.md — Human Roles)*

---

# 4. External Systems

The following external systems exchange information with AI-SDOS.

---

## Version Control Platform

**Examples:** Git repositories, GitHub, GitLab

**Purpose:** Stores source code artifacts, implementation outputs, and versioned documentation produced during execution.

**Interaction:** AI-SDOS reads project history and pushes generated artifacts.

---

## AI Providers

**Examples:** Anthropic, OpenAI, other LLM providers

**Purpose:** Provides the AI model capabilities used by Specialized Agents to perform engineering tasks.

**Interaction:** AI-SDOS invokes AI providers to delegate generation, analysis, review, and validation tasks to Specialized Agents.

---

## Development Environments (IDEs)

**Examples:** Visual Studio Code, JetBrains IDEs

**Purpose:** The environments where Software Engineers work on implementation.

**Interaction:** AI-SDOS integrates with IDEs to deliver context, specifications, and generated artifacts directly into the engineering workflow.

---

## MCP Servers

**Examples:** Model Context Protocol servers providing extended tools

**Purpose:** Extends AI-SDOS capabilities through additional tools and integrations accessible to Specialized Agents.

**Interaction:** AI-SDOS invokes MCP servers to access capabilities beyond native platform functionality.

---

## Issue Tracking Systems

**Examples:** Linear, Jira, GitHub Issues

**Purpose:** Tracks engineering tasks, decisions, and project milestones.

**Interaction:** AI-SDOS may surface tasks and decisions in issue trackers for human review and prioritization.

---

## Documentation Platforms

**Examples:** Notion, Confluence, GitHub Pages

**Purpose:** Hosts and organizes project documentation accessible to wider teams.

**Interaction:** AI-SDOS may publish finalized documentation artifacts to documentation platforms for distribution.

---

## CI/CD Platforms

**Examples:** GitHub Actions, CircleCI, Vercel

**Purpose:** Automates validation, build, and deployment workflows.

**Interaction:** AI-SDOS may trigger or integrate with CI/CD pipelines to validate implementation outputs against specifications.

*(Source: DOMAIN_DISCOVERY.md — External Systems; SYSTEM_ARCHITECTURE.md — Tool Integration Layer)*

---

# 5. Interaction Summary

| Actor / System | Direction | Information Exchanged | Purpose |
|---|---|---|---|
| Project Architect | → AI-SDOS | Objectives, decisions, approvals | Define and govern project direction |
| Software Engineer | → AI-SDOS | Status, feedback, clarification requests | Consume specifications and report progress |
| Technical Lead | ↔ AI-SDOS | Requirements, technical guidance, reviews | Bridge product and engineering |
| Product Owner | → AI-SDOS | Requirements, priorities | Drive product-aligned specifications |
| Domain Expert | → AI-SDOS | Domain knowledge, validation | Ensure conceptual accuracy |
| QA Engineer | → AI-SDOS | Quality reviews, validation outcomes | Validate quality and correctness |
| Project Maintainer | ↔ AI-SDOS | Maintenance inputs, lifecycle events | Keep project knowledge current |
| Version Control | ↔ AI-SDOS | Code artifacts, history | Store and retrieve versioned outputs |
| AI Providers | ← AI-SDOS | Prompts, tasks | Execute AI agent responsibilities |
| IDEs | ↔ AI-SDOS | Context, specifications, generated artifacts | Deliver knowledge into engineering workflow |
| MCP Servers | ↔ AI-SDOS | Tool invocations, results | Extend platform capabilities |
| Issue Tracking | ← AI-SDOS | Tasks, decisions | Surface work for human review |
| Documentation Platforms | ← AI-SDOS | Published documentation | Distribute knowledge to wider teams |
| CI/CD Platforms | ↔ AI-SDOS | Validation triggers, outcomes | Automate validation of outputs |

---

# 6. Responsibilities

## Responsibilities of AI-SDOS

* Maintain the authoritative project Knowledge Base.
* Orchestrate engineering workflows across the project lifecycle.
* Coordinate Specialized AI Agents through documented responsibilities.
* Preserve documentation consistency, traceability, and architectural coherence.
* Enforce governance through documented policies and approval gates.
* Produce validated architecture views, specifications, and documentation artifacts.

## Responsibilities of External Systems

* **Version Control Platform:** store and version software artifacts; provide history.
* **AI Providers:** provide model inference capabilities when invoked.
* **IDEs:** provide the development environment; surface delivered context to engineers.
* **MCP Servers:** expose additional tool capabilities when invoked.
* **Issue Tracking Systems:** manage task visibility and team coordination outside AI-SDOS.
* **Documentation Platforms:** host and distribute finalized documentation.
* **CI/CD Platforms:** execute automated build and validation pipelines.

*(Source: DOMAIN_DISCOVERY.md — Domain Boundaries; SYSTEM_ARCHITECTURE.md — Dependency Principles)*

---

# 7. Context Narrative

AI-SDOS operates as an AI Engineering Operating System positioned between human engineering teams and both AI providers and specialized external tooling.

Human actors — from Product Owners who define requirements to Project Architects who govern decisions — interact with AI-SDOS to establish, evolve, and validate the documented knowledge that drives every engineering activity.

Internally, AI-SDOS orchestrates workflows and delegates responsibilities to Specialized AI Agents, which invoke AI Providers for model capabilities and reach external systems through the Tool Integration layer.

The outputs of AI-SDOS — architecture views, specifications, documentation artifacts, and validated implementation plans — flow outward to Version Control Platforms, IDEs, Issue Trackers, Documentation Platforms, and CI/CD systems.

Throughout this ecosystem, AI-SDOS never becomes the runtime of the managed projects. It remains the operating system that structures, governs, and preserves the knowledge required to build them reliably.

*(Source: FOUNDATION.md — Purpose, Vision; DOMAIN_DISCOVERY.md — Domain Definition)*

---

# 8. Context Diagram

See: `docs/architecture/diagrams/system-context.mmd`

The diagram shows AI-SDOS as a single system boundary, with all seven human actors and all seven external systems positioned outside that boundary, connected by labeled relationships.

---

# Related Documents

* PROJECT_STATE.md
* FOUNDATION.md
* DOMAIN_DISCOVERY.md
* UBIQUITOUS_LANGUAGE.md
* DOMAIN_MODEL.md
* SYSTEM_ARCHITECTURE.md
* architecture-overview.md
* Architecture Decision Records (ADRs) — none exist yet

---

# Change Log

| Version | Date       | Description                                                     |
| ------- | ---------- | --------------------------------------------------------------- |
| v0.1    | 2026-07-05 | Initial System Context generated from project documentation. |
