# DEPLOYMENT_ARCHITECTURE

**Project:** AI-SDOS (AI Software Development Operating System)

---

# 1. Purpose

The Deployment Architecture view describes how the AI-SDOS containers are deployed — the environments they run in, how they relate to the underlying platform, and how they connect to external systems at the deployment level.

This is the C4 Model Deployment view for AI-SDOS.

**Important scope note:** As recorded in PROJECT_STATE.md, AI-SDOS is currently in the Documentation Bootstrap phase. No formal Architecture Decision Records (ADRs) exist yet, and no deployment technology choices have been formally documented. This view documents the **conceptual deployment topology** — the logical environments and constraints — without prescribing specific infrastructure, cloud providers, or networking configurations that have not been decided.

Wherever deployment decisions are pending, this document explicitly records the gap rather than inventing undocumented information.

*(Source: TASK-ARCH-009; PROJECT_STATE.md — Known Gaps)*

---

# 2. Deployment Scope

**In scope:**
* Logical deployment environments for AI-SDOS containers.
* Container-to-environment mapping based on container responsibilities.
* External system connectivity from a deployment perspective.
* Documented deployment constraints derived from architectural principles.

**Explicitly out of scope (undecided):**
* Specific cloud provider or hosting platform.
* Networking topology, ports, or protocols.
* Infrastructure-as-code configuration.
* Container orchestration platform (Kubernetes, Docker Swarm, etc.).
* Database technology for the Knowledge Repository.
* Specific AI provider selection.

These decisions are expected to be captured in ADRs when they are made.

*(Source: PROJECT_STATE.md — Known Gaps; SYSTEM_ARCHITECTURE.md — Out of Scope)*

---

# 3. Deployment Environments

Based on the architectural responsibilities defined in container-architecture.md and the deployment constraints derived from SYSTEM_ARCHITECTURE.md, AI-SDOS requires the following logical deployment environments:

---

## Platform Environment

**Purpose:** Hosts the core AI-SDOS platform containers that manage orchestration, knowledge, execution, and governance.

**Characteristics required (from architectural constraints):**
* Must support persistent storage for the Knowledge Repository.
* Must be isolated from external systems except through the Tool Integration Gateway.
* Must support concurrent execution of multiple workflows.
* Must be auditable — every operation must be logged.

**Containers deployed here:**
* Orchestration Engine
* Knowledge Repository
* Execution Engine
* Governance Module

---

## Agent Execution Environment

**Purpose:** Hosts the AI Agent Runtime, which may have different resource and isolation requirements from the core platform due to the nature of AI inference workloads.

**Characteristics required:**
* Must have access to AI Provider endpoints via the Tool Integration Gateway.
* May require higher computational resources during peak agent execution.
* Must be isolated from direct write access to the Knowledge Repository — all writes flow through the Execution Engine.
* Must be able to communicate with the Tool Integration Gateway.

**Containers deployed here:**
* AI Agent Runtime

---

## Integration Environment

**Purpose:** Hosts the Tool Integration Gateway, which manages all outbound connections to external systems.

**Characteristics required:**
* Must have network access to all configured external systems (AI Providers, VCS, IDEs, MCP Servers, CI/CD, Issue Trackers, Documentation Platforms).
* Must act as the single point of outbound connectivity — no other environment connects directly to external systems.
* Must be configurable per deployment (different projects may use different external systems).

**Containers deployed here:**
* Tool Integration Gateway

---

# 4. Container Deployment Mapping

| Container | Deployment Environment | Persistence Required | External Connectivity |
|---|---|---|---|
| Orchestration Engine | Platform Environment | Workflow state, task state | None (internal only) |
| Knowledge Repository | Platform Environment | Yes — all project artifacts | None (internal only) |
| AI Agent Runtime | Agent Execution Environment | No (stateless execution) | Via Tool Integration Gateway |
| Tool Integration Gateway | Integration Environment | Configuration only | Yes — all external systems |
| Execution Engine | Platform Environment | Validation records | Via Tool Integration Gateway (CI/CD) |
| Governance Module | Platform Environment | Policies, audit logs, approval records | None (internal only) |

---

# 5. External System Connectivity

All external system connectivity is mediated exclusively through the **Tool Integration Gateway**.

| External System | Connected Via | Direction | Purpose |
|---|---|---|---|
| AI Providers | AI Provider Adapter | Outbound | LLM inference for agent execution |
| Version Control Platform | Version Control Adapter | Bidirectional | Artifact storage and history retrieval |
| Development Environments (IDEs) | IDE Adapter | Outbound | Context and specification delivery |
| MCP Servers | MCP Server Adapter | Outbound | Extended tool capabilities |
| Issue Tracking Systems | Issue Tracker Adapter | Outbound | Task and decision surfacing |
| Documentation Platforms | (via Version Control or direct adapter) | Outbound | Documentation publication |
| CI/CD Platforms | CI/CD Adapter | Bidirectional | Automated validation pipeline |

No environment other than the Integration Environment (Tool Integration Gateway) has outbound connections to external systems. This enforces the architectural principle that external integrations remain loosely coupled to the platform core.

*(Source: SYSTEM_ARCHITECTURE.md — Tool Integration Layer, Dependency Principles)*

---

# 6. Deployment Constraints

The following constraints must be respected by any deployment implementation. These constraints are derived from SYSTEM_ARCHITECTURE.md and FOUNDATION.md rather than from specific technology decisions.

1. **Knowledge Repository persistence is mandatory.** The Knowledge Repository must survive system restarts. All approved artifacts are permanent project assets.

2. **Agent Execution Environment must not have direct write access to the Knowledge Repository.** All artifact writes flow through the Execution Engine and Governance Module.

3. **Tool Integration Gateway is the single external boundary.** No other container or environment may initiate outbound connections to external systems.

4. **Governance Module must be co-deployed with the Execution Engine.** The Governance Module applies cross-cutting policies at artifact transition time; it cannot be an optional or externally-hosted component.

5. **Audit logs must be persisted.** The Audit Logger's records are permanent — no audit event may be discarded without an explicit governance policy permitting it.

6. **External system adapters must be configurable.** The Tool Integration Gateway must support per-deployment configuration of external system endpoints and credentials without requiring changes to platform internals.

7. **Strategic decisions require human actor availability.** Any deployment must ensure human actors are reachable for governance approval gates — the platform must not become blocked on human gates without a timeout or escalation path.

*(Source: SYSTEM_ARCHITECTURE.md — Architectural Constraints, Dependency Principles; FOUNDATION.md — Design Principles)*

---

# 7. Known Gaps

The following deployment decisions have not been made as of this documentation version. These gaps are recorded honestly and must be resolved through future ADRs.

| Gap | Description | Impact |
|---|---|---|
| Deployment platform | No cloud provider, hosting platform, or on-premises strategy has been selected | Cannot determine specific infrastructure configuration |
| Container orchestration | No container orchestration platform has been selected | Cannot determine scaling, restart, or health check mechanisms |
| Knowledge Repository technology | No specific storage technology (database, file system, object store) has been selected | Cannot determine persistence implementation |
| AI Provider selection | No specific AI provider(s) have been formally selected | Cannot configure AI Provider Adapter |
| Inter-environment networking | No networking approach (VPN, service mesh, API gateway) has been selected | Cannot determine inter-container communication mechanisms |
| Authentication and authorization | No authn/authz strategy has been selected | Cannot determine how human actors and agents are authenticated |

*(Source: PROJECT_STATE.md — Known Gaps; SYSTEM_ARCHITECTURE.md — Out of Scope)*

---

# 8. Deployment Diagram

See: `docs/architecture/diagrams/deployment-architecture.mmd`

The diagram shows the three logical deployment environments, the containers deployed in each, and the external system connections through the Tool Integration Gateway.

---

# Related Documents

* PROJECT_STATE.md
* FOUNDATION.md
* SYSTEM_ARCHITECTURE.md
* system-context.md
* container-architecture.md
* Architecture Decision Records (ADRs) — none exist yet

---

# Change Log

| Version | Date       | Description                                                               |
| ------- | ---------- | ------------------------------------------------------------------------- |
| v0.1    | 2026-07-05 | Initial Deployment Architecture. Conceptual topology only — specific infrastructure decisions are pending ADRs. |
