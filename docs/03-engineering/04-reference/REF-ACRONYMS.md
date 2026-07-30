---
title: Engineering Acronym Reference
id: REF-ACRONYMS
version: 1.0.0
status: Draft
owner: Invara Labs
classification: Engineering Reference
review_cycle: Quarterly
created: 2026-07-30
last_updated: 2026-07-30
approved_by: TBD
authors:
  - Invara Labs Engineering
tags:
  - acronyms
  - abbreviations
  - terminology
  - reference
related:
  - TERM-STANDARD
  - REF-TERMINOLOGY
  - REF-IDENTIFIERS
supersedes: null
superseded_by: null
---

# Engineering Acronym Reference

> **Provides the authoritative catalogue of engineering acronyms used throughout the Invara Labs Engineering Operating System (ILOS).**

## 1. Overview

Acronyms reduce repetition but create ambiguity when their meanings are undocumented or inconsistent.

This reference records one ILOS expansion and meaning for each listed acronym. `TERM-STANDARD` governs how acronyms are introduced and maintained; this reference holds the catalogue.

Because this document is Draft, its entries are proposed for approval and should not be described as formally approved until the document reaches the Approved lifecycle state.

## 2. Purpose

This reference:

- Establishes one source of truth for engineering acronyms.
- Prevents conflicting expansions.
- Improves readability, search, onboarding, and cross-document consistency.
- Supports terminology validation and AI-assisted engineering.
- Preserves deprecated acronyms when historical traceability requires them.

## 3. Scope

This catalogue covers reusable acronyms used across ILOS engineering documentation. It does not attempt to catalogue every vendor, product, protocol, or project-specific abbreviation.

Project-specific abbreviations should be defined locally and added here only when they become part of the shared engineering vocabulary.

## 4. Acronym Usage Principles

- Use one approved expansion and meaning per acronym.
- Write the expanded form followed by the acronym on first use in a document.
- Use the acronym alone only after it has been introduced.
- Prefer the expanded term when an acronym is uncommon or used only once.
- Preserve established capitalisation.
- Do not invent an acronym when clear language is shorter or equally readable.
- Do not use a listed acronym as an artefact identifier unless `REF-IDENTIFIERS` also permits it.

Example:

```text
Architecture Decision Record (ADR)
```

## 5. Engineering Acronyms

| Acronym | Expanded Form | Description |
|---|---|---|
| API | Application Programming Interface | A contract through which software components expose functionality or data. |
| CLI | Command-Line Interface | A text-based interface used to operate software through commands. |
| CRUD | Create, Read, Update, Delete | The fundamental operations performed on persistent data. |
| SDK | Software Development Kit | Tools, libraries, and guidance used to build against a platform. |
| UI | User Interface | The means through which a user interacts with a system. |
| UX | User Experience | A user's overall experience of interacting with a product or service. |

## 6. Architecture Acronyms

| Acronym | Expanded Form | Description |
|---|---|---|
| ADR | Architecture Decision Record | A durable record of a significant architectural decision and its rationale. |
| MFE | Micro Frontend | An architectural approach using independently developed frontend modules. |
| REST | Representational State Transfer | An architectural style for networked applications and web APIs. |
| RFC | Request for Comments | A proposal circulated for structured review before adoption. |
| SSR | Server-Side Rendering | Rendering a user interface on a server before sending it to a client. |

## 7. Development Acronyms

| Acronym | Expanded Form | Description |
|---|---|---|
| IDE | Integrated Development Environment | A tool combining source editing, execution, debugging, and related development capabilities. |
| JSON | JavaScript Object Notation | A text format for structured data interchange. |
| NFR | Non-Functional Requirement | A requirement describing a quality attribute or constraint rather than functional behaviour. |
| SQL | Structured Query Language | A language used to define, query, and manipulate relational data. |
| YAML | YAML Ain't Markup Language | A human-readable data-serialisation language used by repository metadata. |

## 8. Quality and Testing Acronyms

| Acronym | Expanded Form | Description |
|---|---|---|
| E2E | End-to-End | Testing across a complete user or system workflow. |
| QA | Quality Assurance | Systematic activities used to build confidence in process and product quality. |
| SUT | System Under Test | The system or component being evaluated by a test. |
| UAT | User Acceptance Testing | Validation by users or authorised stakeholders that a solution meets intended needs. |

## 9. Operations and DevOps Acronyms

| Acronym | Expanded Form | Description |
|---|---|---|
| CD | Continuous Delivery | Keeping software in a releasable state through automated delivery practices. |
| CI | Continuous Integration | Frequently integrating changes and validating them through automation. |
| IaC | Infrastructure as Code | Defining and managing infrastructure through version-controlled code. |
| KPI | Key Performance Indicator | A metric used to evaluate progress toward an objective. |
| MTTR | Mean Time to Restore | The average time required to restore service after disruption. |
| RCA | Root Cause Analysis | A structured investigation of underlying and contributing causes. |
| RPO | Recovery Point Objective | The maximum tolerable period of data loss following disruption. |
| RTO | Recovery Time Objective | The target time for restoring a service after disruption. |
| SLA | Service Level Agreement | A formal commitment describing agreed service levels and responsibilities. |
| SLI | Service Level Indicator | A measured value representing an aspect of service performance. |
| SLO | Service Level Objective | A target value or range for a service level indicator. |

Within ILOS, `CD` means **Continuous Delivery**. Write **Continuous Deployment** in full when that distinct practice is intended.

Within ILOS, `MTTR` means **Mean Time to Restore**. Write alternative measures such as mean time to repair or recover in full unless a future approved acronym is assigned.

## 10. Documentation and Governance Acronyms

| Acronym | Expanded Form | Description |
|---|---|---|
| ADR | Architecture Decision Record | A governed architecture decision artefact. |
| ILOS | Invara Labs Engineering Operating System | The system governing Invara Labs engineering knowledge and documentation. |
| RFC | Request for Comments | A governed proposal submitted for structured review. |
| SSOT | Single Source of Truth | The designated authoritative location for a category of information. |

`ADR` and `RFC` appear here because they are both architectural concepts and governed document types; their expansion and meaning remain identical.

## 11. AI and Automation Acronyms

| Acronym | Expanded Form | Description |
|---|---|---|
| AI | Artificial Intelligence | Machine-based capabilities that support tasks commonly requiring human intelligence. |
| HITL | Human-in-the-Loop | A model in which qualified people review consequential AI outputs and retain accountability. |
| LLM | Large Language Model | A language model trained on large datasets to process and generate language. |
| ML | Machine Learning | Methods through which systems learn patterns from data. |
| NLP | Natural Language Processing | Computational methods for processing and generating human language. |
| RAG | Retrieval-Augmented Generation | Generating model output using information retrieved from an external knowledge source. |

## 12. Usage Guidelines

Correct:

```text
The Architecture Decision Record (ADR) explains the decision.
The ADR links to the affected requirements.
```

Avoid:

```text
The ADR explains the decision.  # Acronym not introduced
```

Headings, tables, diagrams, and metadata may use an acronym without local expansion when the expanded form is adjacent or the document is the acronym's dedicated reference.

## 13. Adding New Acronyms

Before adding an acronym:

1. Confirm that the expanded term is part of the shared engineering vocabulary.
2. Confirm that the acronym is necessary and not already assigned.
3. Check `REF-TERMINOLOGY` and `REF-IDENTIFIERS` for conflicts.
4. Define one expansion, meaning, category, and capitalisation.
5. Review the change under `TERM-STANDARD`.
6. Update affected artefacts after approval.

New entries require a version update and revision-history entry.

## 14. Deprecated Acronyms

No acronyms are currently deprecated.

When an acronym is deprecated, retain:

- Its former expansion and meaning.
- Its deprecation date.
- Its replacement, when applicable.
- Any migration guidance needed to preserve traceability.

Deprecated acronyms should not be removed from historical documents solely to modernise language.

## 15. Related Artefacts

### Standards

- [`TERM-STANDARD`](../03-standards/TERM-STANDARD.md) — Governs acronym creation and usage.
- [`STD-METADATA`](../03-standards/STD-METADATA.md) — Defines governed document metadata.

### References

- [`REF-TERMINOLOGY`](REF-TERMINOLOGY.md) — Defines engineering terms.
- [`REF-IDENTIFIERS`](REF-IDENTIFIERS.md) — Defines artefact identifiers and prefixes.

## 16. References

- ISO/IEC/IEEE 24765 — Systems and software engineering vocabulary
- ISO 704 — Terminology work, principles and methods

These references inform the catalogue; approved ILOS governance remains authoritative within the repository.

## 17. Revision History

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Initial acronym reference draft |

## 18. Summary

The Engineering Acronym Reference gives ILOS one governed expansion and meaning for each shared abbreviation.

Used with `REF-IDENTIFIERS` and `REF-TERMINOLOGY`, it completes the Draft vocabulary foundation for Principles, Playbooks, Standards, References, and Examples.
