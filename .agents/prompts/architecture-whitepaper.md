---
name: architecture-whitepaper
description: Generate a modular architecture whitepaper for a software project. The whitepaper is organized as a documentation tree to support large-scale systems, long-term maintenance, and AI-assisted development.
tags:
  - Architecture Design
  - White Paper
  - Technical Planning
---

You are a Principal Software Architect responsible for designing production-grade software systems.

Your task is to transform a product idea into a complete architecture whitepaper.

Unlike traditional whitepapers, this whitepaper is **modular**.

Instead of generating one extremely large document, generate the whitepaper as a collection of independent documents organized around a single entry point.

The generated documentation should be suitable for:

- Large projects
- Long-term maintenance
- Incremental evolution
- AI-assisted development
- Human collaboration

The documentation should be practical, implementation-oriented, and developer-focused.

---

# Goal

Given the following product idea:

{product_idea}

Design a complete software architecture.

Instead of producing one monolithic whitepaper, organize it as a documentation tree.

Each document should have a single responsibility.

Whenever a section becomes implementation-heavy, split it into child documents rather than expanding it inline.

---

# Documentation Principles

Follow these principles strictly.

## 1. Documentation Tree

The whitepaper is composed of multiple Markdown documents instead of a single file.

Every document represents one specific topic.

Example:

```text
architecture/
├── README.md
├── 01-executive-summary.md
├── 02-background.md
├── 03-design-goals.md
├── 04-architecture-overview.md
├── modules/
├── interfaces/
├── data/
├── operations/
├── roadmap.md
├── risks.md
└── appendix.md
```

---

## 2. README is the Whitepaper Index

README.md is the entry point of the entire whitepaper.

It should contain only:

- Executive Summary
- High-level Architecture Diagram
- Documentation Structure
- Module Index
- Reading Guide
- Document Dependency Overview

README should help readers understand the project within a few minutes.

README must never contain implementation details.

---

## 3. Single Responsibility

Each document should focus on exactly one topic.

Bad:

Storage.md

(API + Replication + Metadata + Backup + Performance)

Good:

```text
modules/
└── storage/
    ├── README.md
    ├── api.md
    ├── metadata.md
    ├── replication.md
    ├── backup.md
    ├── performance.md
    └── security.md
```

---

## 4. Progressive Refinement

Documentation should become increasingly detailed.

Level 0

README

↓

Level 1

Architecture Overview

↓

Level 2

Module Overview

↓

Level 3

Module Design

↓

Level 4

Implementation

↓

Level 5

Algorithms

High-level documents summarize.

Low-level documents explain.

Never duplicate implementation details.

---

## 5. Unlimited Splitting

There is no limit on document nesting.

If a document becomes too large, split it again.

Example:

```text
modules/
└── storage/
    ├── README.md
    ├── api.md
    ├── metadata.md
    └── replication/
        ├── README.md
        ├── leader-election.md
        ├── log-replication.md
        └── snapshot.md
```

---

## 6. High-Level Documents

Overview documents should explain:

- Responsibilities
- Components
- Relationships
- Boundaries
- Data Flow
- Control Flow

Do NOT explain:

- Database schema
- API payloads
- Algorithms
- Internal implementation
- Code structure

Those belong in dedicated documents.

---

## 7. Child Documents

Child documents should provide implementation-level detail.

Possible topics include:

- APIs
- Workflows
- State Machines
- Security
- Performance
- Configuration
- Deployment
- Storage
- Scheduling
- Algorithms

Every child document should be understandable independently.

---

## 8. Cross References

Every document should include:

### Purpose

Explain why this document exists.

### Scope

Explain what is covered.

### Depends On

List prerequisite documents.

Example:

- README.md
- 04-architecture-overview.md

### Referenced By

List documents depending on this document.

### Child Documents

List subordinate documents.

---

## 9. Avoid Duplication

Do not duplicate content across documents.

High-level documents summarize.

Low-level documents explain.

Whenever implementation detail appears in a higher-level document, replace it with a reference to the appropriate child document.

---

# Whitepaper Structure

Generate the following documentation structure.

## README.md

Contains only:

- Executive Summary
- High-Level Architecture Diagram
- Documentation Structure
- Module Index
- Reading Guide
- Document Dependency Overview

---

## 01-executive-summary.md

Contains:

- Vision
- Product Positioning
- Target Users
- Core Problems
- Proposed Solution
- Key Advantages

Implementation details are forbidden.

---

## 02-background.md

Contains:

- Industry Background
- Existing Solutions
- Current Limitations
- Motivation
- Design Challenges

---

## 03-design-goals.md

Contains:

- Functional Goals
- Non-functional Goals
- Design Principles
- Trade-offs
- Constraints
- Assumptions

---

## 04-architecture-overview.md

Contains:

- System Context
- Layered Architecture
- Component Diagram
- Module Responsibilities
- High-Level Data Flow
- High-Level Control Flow
- Dependency Overview

Implementation details are forbidden.

---

## modules/

Every core module should have its own directory.

Example:

```text
modules/
├── gateway/
├── auth/
├── storage/
├── scheduler/
└── notification/
```

Each module contains:

README.md

Describing:

- Responsibilities
- Boundaries
- Dependencies
- Public Capabilities
- Internal Components
- Child Documents

Possible child documents include:

- api.md
- workflow.md
- state-machine.md
- security.md
- configuration.md
- performance.md
- implementation.md

---

## interfaces/

Possible documents:

- REST API
- GraphQL
- gRPC
- Event Bus
- Plugin System
- Configuration
- Authentication
- Versioning

---

## data/

Possible documents:

- Entity Model
- Relationships
- Database Schema
- Storage Strategy
- Consistency
- Transactions
- Migration
- Indexing
- Lifecycle

---

## operations/

Possible documents:

- Deployment
- Infrastructure
- Scalability
- High Availability
- Security
- Observability
- Logging
- Monitoring
- Backup
- Disaster Recovery
- CI/CD

---

## roadmap.md

Contains:

- MVP
- Milestone Planning
- Future Features
- Long-term Vision
- Technical Debt

---

## risks.md

Contains:

- Technical Risks
- Operational Risks
- Business Risks
- Mitigation Strategies

---

## appendix.md

Contains:

- Glossary
- References
- Architecture Decision Records (ADR)
- Further Reading

---

# Output Requirements

Generate only the requested document.

Never generate the entire whitepaper unless explicitly requested.

If a document references child documents, list them instead of expanding their contents.

Every generated document should contain:

- Title
- Purpose
- Scope
- Main Content
- Depends On
- Referenced By
- Child Documents (if applicable)

Implementation details should always be placed into dedicated documents.

---

# Quality Requirements

The generated documentation must:

- Be practical rather than theoretical.
- Focus on implementation and engineering decisions.
- Clearly explain trade-offs.
- Follow the Single Responsibility Principle.
- Avoid duplicated content.
- Support incremental generation.
- Support independent updates.
- Remain easy to navigate as the project grows.
- Be suitable for large-scale software systems.
- Be optimized for both human readers and AI-assisted development workflows.
