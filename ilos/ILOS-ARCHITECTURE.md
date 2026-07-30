---
title: Invara Labs Engineering Operating System Architecture
version: 1.1.0
status: Approved
owner: Invara Labs
classification: Architecture
review_cycle: Annual
created: 2026-07-30
last_updated: 2026-07-30
authors:
  - Invara Labs Engineering
---

# Invara Labs Engineering Operating System Architecture

> **The architectural blueprint defining the structure, organisation, governance, and evolution of the Invara Labs Engineering Operating System (ILOS).**

## 1. Overview

The Invara Labs Engineering Operating System is an engineering knowledge system designed to organise, govern, and continuously improve engineering documentation.

Rather than treating documentation as isolated files, ILOS treats engineering knowledge as an interconnected system in which every artefact has a defined purpose, lifecycle, owner, and relationship to other artefacts.

This document is the architectural constitution of that system.

## 2. Purpose

This architecture:

- Defines the structural model of ILOS.
- Establishes clear responsibilities for each document type.
- Prevents duplication of engineering knowledge.
- Promotes consistency across the repository.
- Enables documentation to scale with the organisation.
- Supports governance, traceability, and automation.
- Provides a stable foundation for AI-assisted engineering.

## 3. Architectural Goals

ILOS is designed to be:

- Modular
- Scalable
- Discoverable
- Governed
- Maintainable
- Traceable
- Technology-agnostic
- AI-ready

These goals guide every architectural decision within ILOS.

## 4. Design Principles

### Single Responsibility

Every document has one clear purpose and answers one primary question.

### Separation of Concerns

Engineering knowledge is organised into specialised document types, each solving a distinct problem.

### Layered Knowledge

Knowledge flows from enduring philosophy to practical implementation.

### Reuse Before Duplication

Information is maintained in one authoritative location and referenced elsewhere.

### Traceability

Decisions, requirements, standards, and supporting artefacts remain connected throughout their lifecycle.

### Continuous Evolution

The architecture supports incremental growth without routine structural redesign.

### Human Accountability

AI may assist engineering work, but ownership, review, decisions, and approvals remain human responsibilities.

## 5. Canonical Visual Model

```text
                    Engineering Operating System
                               │
            ┌──────────────────┼──────────────────┐
            │                  │                  │
       ILOS Control       Engineering Docs     Templates
            │                  │                  │
    ┌───────┼────────┐    ┌────┴────────────┐     │
    │       │        │    │                 │     │
Architecture Governance Lifecycle       Principles│
    │       │        │                      │     │
    └───────┴────────┴──► Playbooks ──► Standards │
                               │             │    │
                               └──► References ───┤
                                        │         │
                                        └──► Examples
                                                 │
            ◄──────── Continuous Improvement ────┘
```

This is the canonical visual model for ILOS. Reused versions must preserve these relationships even when presentation changes.

## 6. Knowledge Architecture

ILOS organises engineering knowledge into five primary categories.

```text
Principles
    │
    ▼
Playbooks
    │
    ▼
Standards
    │
    ▼
References
    │
    ▼
Examples
```

### Principles

Principles define the philosophy guiding engineering decisions.

> **Why do we work this way?**

### Playbooks

Playbooks describe repeatable engineering processes.

> **How is this activity performed?**

### Standards

Standards define mandatory engineering requirements.

> **What must be followed?**

### References

References provide reusable supporting information.

> **What information should be consulted?**

### Examples

Examples demonstrate practical application.

> **What does good look like?**

## 7. Relationships Between Document Types

| Document Type | Depends On | Responsibility |
|---|---|---|
| Principles | Founder intent and company foundation | Establish engineering philosophy |
| Playbooks | Principles | Turn philosophy into repeatable workflows |
| Standards | Principles and Playbooks | Formalise mandatory expectations |
| References | Standards and Playbooks | Support implementation and decisions |
| Examples | All document types | Demonstrate correct application |

Knowledge flows towards implementation. Operational feedback flows back through review and continuous improvement.

## 8. Repository Architecture

```text
invara-labs-playbook/
├── ilos/
│   ├── README.md
│   ├── ILOS-ARCHITECTURE.md
│   ├── ILOS-ROADMAP.md
│   ├── ILOS-GOVERNANCE.md
│   ├── ILOS-LIFECYCLE.md
│   └── ILOS-CHANGELOG.md
├── docs/
│   └── 03-engineering/
│       ├── 01-principles/
│       ├── 02-playbooks/
│       ├── 03-standards/
│       ├── 04-reference/
│       └── 05-examples/
├── decisions/
│   └── adr/
├── templates/
├── prompts/
└── assets/
```

### ILOS Control Layer — `ilos/`

Defines architecture, governance, roadmap, lifecycle, and ILOS change history.

### Engineering Knowledge — `docs/03-engineering/`

Contains the Principles, Playbooks, Standards, References, and Examples governed by ILOS.

### Decisions — `decisions/adr/`

Preserves significant strategic and architectural decisions, including changes to ILOS.

### Templates — `templates/`

Provides approved structures for repeatable engineering and governance artefacts.

### Prompts and Assets

Prompts support governed AI-assisted workflows. Assets store reusable diagrams, images, and logos.

## 9. Governance Architecture

Governance applies consistently across engineering documentation through:

- Standard document templates.
- Defined ownership and accountability.
- Version management.
- Metadata.
- Review and approval workflows.
- Traceability.
- Periodic reviews.
- Continuous improvement.

Detailed decision rights and change controls are defined in [ILOS Governance](ILOS-GOVERNANCE.md).

## 10. AI Architecture

ILOS supports AI-assisted engineering while preserving human accountability.

AI may assist with:

- Document authoring.
- Review preparation.
- Metadata validation.
- Standards compliance.
- Terminology consistency.
- Traceability analysis.
- Quality assessment.
- Knowledge discovery.

Human reviewers remain accountable for all decisions, approvals, and delivered outcomes.

## 11. Architectural Constraints

To preserve integrity:

1. Every engineering document belongs to one primary document category.
2. Every substantive document has defined ownership and lifecycle status.
3. Approved templates are used where applicable.
4. Substantive documents include required metadata.
5. Cross-references use stable paths and approved identifiers where defined.
6. ILOS governance applies consistently.
7. Domain content does not redefine ILOS controls.
8. Repository-wide structural changes require an ADR.
9. New structure is created only for a demonstrated need.

## 12. Architectural Evolution

Changes must:

- Preserve existing knowledge.
- Minimise disruption.
- Maintain backwards compatibility where practical.
- Improve usability or governance.
- Support organisational growth.
- Enable emerging engineering practices.

Significant architectural changes are recorded in [`decisions/adr/`](../decisions/README.md).

## 13. Maturity Model

- 🟢 **Stable** — approved and dependable
- 🟡 **In Progress** — actively being developed or reviewed
- 🔴 **Planned** — intended but not yet substantive

## 14. Relationships

- Introduced by [ADR-008](../decisions/adr/ADR-008-dedicated-ilos-control-layer.md)
- Governed by [ILOS Governance](ILOS-GOVERNANCE.md)
- Evolved through [ILOS Lifecycle](ILOS-LIFECYCLE.md)
- Sequenced by [ILOS Roadmap](ILOS-ROADMAP.md)
- Summarised by the [ILOS Overview](README.md)

## 15. Summary

The ILOS architecture defines the structural foundation on which engineering documentation is built.

By separating knowledge into Principles, Playbooks, Standards, References, and Examples, ILOS provides a scalable, governed, and maintainable framework supporting engineering excellence, organisational learning, and responsible AI-assisted engineering.

This architecture keeps engineering knowledge consistent, discoverable, and adaptable as the organisation and its technology evolve.
