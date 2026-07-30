---
title: Engineering Terminology Reference
id: REF-TERMINOLOGY
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
  - terminology
  - glossary
  - engineering
  - reference
related:
  - TERM-STANDARD
  - REF-IDENTIFIERS
  - REF-ACRONYMS
supersedes: null
superseded_by: null
---

# Engineering Terminology Reference

> **Provides the authoritative glossary of engineering terminology used throughout the Invara Labs Engineering Operating System (ILOS).**

## 1. Overview

Consistent terminology supports clear communication, collaboration, governance, documentation, and automation.

This reference is the single source of truth for the engineering terms defined below. Other engineering artefacts should link to these definitions instead of creating competing definitions.

`TERM-STANDARD` governs how terminology is introduced and maintained; this reference holds the vocabulary itself.

## 2. Purpose

This reference:

- Establishes a shared engineering vocabulary.
- Reduces ambiguity and conflicting definitions.
- Improves consistency and discoverability.
- Supports governance, onboarding, and traceability.
- Gives AI-assisted workflows a controlled vocabulary.

## 3. Scope

This reference applies to Principles, Playbooks, Standards, References, Examples, Templates, and ILOS governance documentation.

It does not replace specialised domain glossaries. When a specialised definition is necessary, the domain document should state its scope and link back here.

## 4. Terminology Categories

- Documentation
- Governance
- Architecture
- Requirements and development
- Quality
- Testing
- Operations
- AI-assisted engineering

## 5. Documentation Terms

### Artefact

Any governed engineering deliverable managed within ILOS, including a Principle, Playbook, Standard, Reference, Example, Template, ADR, or RFC.

### Document

An artefact whose primary purpose is to communicate structured knowledge, guidance, evidence, or a decision.

### Metadata

Structured information that describes an artefact, including its identity, version, lifecycle status, ownership, and relationships.

### Identifier

A stable, unique value used to distinguish an artefact within its governed namespace.

Example: `STD-TRACEABILITY`.

### Cross-reference

An explicit link or identifier-based relationship from one artefact to another.

### Traceability

The ability to establish, follow, and maintain relationships between engineering artefacts and delivery evidence throughout their lifecycles.

## 6. Governance Terms

### Standard

A mandatory engineering requirement that defines practices, controls, or quality expectations that must be followed within its stated scope.

### Principle

A foundational statement that explains why engineering decisions and practices should be guided in a particular direction.

### Playbook

A repeatable, practical process describing how an engineering activity is performed.

### Reference

Authoritative supporting information intended to be consulted rather than enforced as a procedure.

### Example

A practical illustration of how a governed practice or expected outcome may be applied.

### Review

A structured evaluation of an artefact against defined quality, technical, and governance criteria.

### Approval

Formal acceptance by an authorised approver that advances an artefact to the Approved lifecycle state.

### Governance

The policies, processes, roles, decisions, and controls used to manage engineering artefacts and practices.

## 7. Architecture Terms

### Architecture Decision Record (ADR)

A durable record of a significant architectural decision, including its context, decision, rationale, and consequences.

### Request for Comments (RFC)

A proposal circulated for structured review before a significant technical or organisational change is adopted.

### Dependency

A relationship in which an artefact, component, or outcome relies on another artefact, component, or outcome.

### Single Source of Truth

The designated authoritative location for a specific category of information.

## 8. Requirements and Development Terms

### Requirement

A documented capability, behaviour, quality attribute, or constraint that a solution must satisfy.

### User Story

A concise statement of a desired outcome from the perspective of a user or stakeholder.

### Epic

A large body of related work that is decomposed into smaller requirements, features, or user stories.

### Feature

A coherent product capability that delivers value to a user or stakeholder.

### Technical Debt

The future cost or constraint created when an expedient technical choice requires later remediation, limits change, or increases operational risk.

## 9. Quality Terms

### Validation

Confirmation that an artefact or solution satisfies its intended use and stakeholder need.

### Verification

Confirmation that an artefact or solution satisfies specified requirements, rules, or standards.

### Compliance

Demonstrated adherence to applicable mandatory standards, policies, and governance requirements.

### Audit

A systematic and evidence-based assessment of artefacts, processes, or controls against defined criteria.

## 10. Testing Terms

### Test Case

A documented set of preconditions, inputs, actions, and expected results used to verify behaviour.

### Test Report

A record of testing scope, execution, evidence, results, and unresolved issues.

### Regression Testing

Testing performed after a change to confirm that previously working behaviour remains correct.

## 11. Operations Terms

### Release

A versioned set of software changes made available to a defined environment or audience.

For documentation, use **document version** and the ILOS lifecycle states rather than treating approval as a software release.

### Incident

An unplanned event that disrupts, degrades, or creates material risk to a service.

### Postmortem

A structured, blameless analysis of an incident that records impact, causes, contributing factors, lessons, and improvement actions.

## 12. AI-Assisted Engineering Terms

### AI-Assisted Engineering

The use of artificial intelligence to support engineering work while qualified people retain oversight, judgement, and accountability.

### AI Review

The use of AI to prepare observations or recommendations for a human-led review.

### AI Validation

Automated analysis performed by AI to identify potential inconsistencies, omissions, risks, or quality issues; it does not constitute formal approval.

### Human-in-the-Loop

An operating model in which a qualified person reviews consequential AI outputs and remains accountable for the resulting decision or action.

## 13. Terminology Governance

New or changed terms should:

- Have one clear definition and an appropriate category.
- Avoid duplicating an existing concept.
- Use recognised industry language where it is precise.
- Be reviewed under `TERM-STANDARD`.
- Be updated consistently across affected artefacts.
- Preserve deprecated meanings when historical traceability requires them.

Draft definitions are not approved terminology until this reference reaches the Approved lifecycle state.

## 14. Related Artefacts

### Standards

- [`TERM-STANDARD`](../03-standards/TERM-STANDARD.md) — Governs terminology.
- [`STD-METADATA`](../03-standards/STD-METADATA.md) — Defines metadata.
- [`STD-TRACEABILITY`](../03-standards/STD-TRACEABILITY.md) — Defines traceability requirements.

### References

- [`REF-IDENTIFIERS`](REF-IDENTIFIERS.md) — Defines identifier families.
- `REF-ACRONYMS` — Planned acronym catalogue.

## 15. External References

- ISO/IEC/IEEE 24765 — Systems and software engineering vocabulary
- ISO/IEC/IEEE 29148 — Requirements engineering
- ISO/IEC/IEEE 42010 — Architecture description

These references inform this glossary; approved ILOS terminology remains authoritative within the repository.

## 16. Revision History

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Initial terminology reference draft |

## 17. Summary

The Engineering Terminology Reference gives ILOS one controlled vocabulary for its core documentation, governance, architecture, delivery, quality, operations, and AI-assisted engineering concepts.

Consistent use of these definitions improves shared understanding, traceability, search, onboarding, and responsible automation.
