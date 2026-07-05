# UBIQUITOUS_LANGUAGE

**Project:** AI-SDOS (AI Software Development Operating System)

---

# Purpose

This document defines the shared vocabulary of AI-SDOS.

Its purpose is to establish a consistent and unambiguous language used by humans and AI agents across documentation, architecture, specifications, implementation, and governance.

Every term defined here has a single meaning within the project and should be used consistently in all project artifacts.

---

# Naming Principles

The ubiquitous language follows these principles:

* One concept has one name.
* One name represents one concept.
* Avoid synonyms for defined concepts.
* Prefer descriptive names over abbreviations.
* Use business-oriented terminology before technical terminology.
* Reuse existing definitions instead of creating new ones.
* When introducing a new concept, update this document first.

---

# Core Concepts

## AI-SDOS

The AI Engineering Operating System that orchestrates the software development lifecycle through documentation, specifications, AI agents, and human governance.

---

## Project

A bounded software initiative managed by AI-SDOS.

A project contains all documentation, specifications, architectural artifacts, implementation assets, and execution history related to a single software system.

---

## Documentation

The authoritative representation of project knowledge.

Documentation is the primary source of truth and precedes implementation.

---

## Knowledge

The collection of documented information, decisions, terminology, specifications, and architectural understanding accumulated throughout the project lifecycle.

---

## Specification (SPEC)

A formal document describing requirements, behavior, architecture, or implementation expectations for a defined scope of work.

Specifications drive implementation and provide traceability between decisions and delivered software.

---

## Task

A discrete unit of work executed by either a human or an AI agent.

Tasks have explicit objectives, inputs, outputs, dependencies, and acceptance criteria.

---

## Workflow

A structured sequence of tasks executed to achieve a specific engineering outcome.

Workflows define the order and dependencies between engineering activities.

---

## Architecture

The intentional organization of the system, its responsibilities, boundaries, relationships, and guiding decisions.

Architecture describes structure rather than implementation.

---

## Architecture Decision Record (ADR)

A documented architectural decision together with its context, rationale, consequences, and status.

ADRs preserve the reasoning behind significant design choices.

---

## Domain

The problem space addressed by AI-SDOS.

The domain defines the concepts, relationships, responsibilities, and constraints that exist independently of technical implementation.

---

## Domain Model

The conceptual representation of the domain, including its entities, value objects, aggregates, services, and relationships.

The Domain Model describes business concepts rather than software implementation.

---

## Ubiquitous Language

The shared vocabulary used consistently throughout the project.

This document is the authoritative source for that vocabulary.

---

# Human Roles

## Project Architect

Responsible for architectural direction, governance, strategic decisions, and validation.

The Project Architect remains the final authority for project evolution.

---

## Software Engineer

Implements validated specifications while preserving architectural consistency.

---

## Domain Expert

Provides knowledge about the problem domain and validates conceptual correctness.

---

## Reviewer

Evaluates artifacts for quality, consistency, completeness, and alignment with project standards.

---

# AI Roles

## Orchestrator

Coordinates workflows, delegates responsibilities, and manages execution order across specialized AI agents.

The Orchestrator does not replace specialized agents; it coordinates them.

---

## Specialized Agent

An AI agent responsible for a clearly defined engineering capability, such as documentation, architecture, implementation, testing, or analysis.

Each agent operates within an explicit scope of responsibility.

---

## Knowledge Base

The complete collection of project artifacts used as the reference context for engineering activities.

The Knowledge Base evolves continuously as the project progresses.

---

# Documentation Concepts

## Foundation

The document defining the project's purpose, philosophy, principles, and long-term vision.

---

## Project State

The current status of the project, including its lifecycle phase, objectives, roadmap, and documentation maturity.

---

## Domain Discovery

The process of understanding and documenting the problem domain before modeling or implementation.

---

## System Architecture

The description of the system's structural organization and major components.

---

## Architecture Overview

A high-level description of the overall system organization and relationships between major subsystems.

---

## Diagram

A visual representation of architectural, conceptual, or operational relationships within the project.

Diagrams complement documentation but never replace it.

---

# Lifecycle Concepts

## Documentation Bootstrap

The initial phase in which the foundational project documentation is established.

---

## Discovery

The process of identifying domain knowledge, concepts, and requirements.

---

## Design

The process of organizing knowledge into architectural structures and specifications.

---

## Implementation

The process of transforming validated specifications into executable software.

---

## Validation

The process of confirming that an artifact satisfies its intended purpose and acceptance criteria.

---

## Governance

The set of rules, responsibilities, and review processes that preserve project quality and consistency.

---

# Quality Attributes

The following terms describe desired characteristics of the platform:

* Consistency
* Traceability
* Maintainability
* Modularity
* Scalability
* Extensibility
* Reproducibility
* Observability
* Simplicity
* Tool Independence
* Technology Agnosticism

These terms should be interpreted consistently across all project documentation.

---

# Reserved Terms

The following names have explicit meanings and must not be repurposed:

* AI-SDOS
* Project
* Documentation
* Specification
* SPEC
* Task
* Workflow
* Domain
* Domain Model
* Architecture
* ADR
* Orchestrator
* Specialized Agent
* Knowledge Base
* Documentation Bootstrap

---

# Evolution Rules

The ubiquitous language evolves under the following rules:

1. New concepts must be defined before they are used.
2. Existing definitions should be updated rather than duplicated.
3. Deprecated terms should remain documented until fully removed from the project.
4. Synonyms for defined concepts should be avoided.
5. Every document must use the terminology defined here.

---

# Related Documents

* PROJECT_STATE.md
* FOUNDATION.md
* DOMAIN_DISCOVERY.md
* DOMAIN_MODEL.md
* SYSTEM_ARCHITECTURE.md
* Architecture Decision Records (ADRs)

---

# Change Log

| Version | Date       | Description                                                      |
| ------- | ---------- | ---------------------------------------------------------------- |
| v0.1    | 2026-07-05 | Initial ubiquitous language established for the AI-SDOS project. |
