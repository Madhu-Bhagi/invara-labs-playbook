---
title: Technical Design Playbook
id: PB-TECH-DESIGN
version: 1.0.3
status: Draft
owner: Invara Labs Engineering
classification: Engineering Playbook
review_cycle: Annual
created: 2026-07-30
last_updated: 2026-07-30
approved_by: TBD
authors:
  - Invara Labs Engineering
tags:
  - technical-design
  - engineering
  - implementation
  - design
  - interfaces
  - data
  - playbook
related:
  - EP-001
  - EP-002
  - EP-004
  - EP-005
  - AR-004
  - AR-005
  - AR-007
  - PB-REQ
  - PB-ARCH
  - PB-AI-ENGINEERING
  - PB-CODING
  - PB-AUTHORING
  - STD-REVIEW
  - STD-TRACEABILITY
  - STD-METADATA
  - STD-VERSIONING
  - TERM-STANDARD
  - REF-IDENTIFIERS
  - REF-TERMINOLOGY
  - REF-ACRONYMS
supersedes: null
superseded_by: null
---

# Technical Design Playbook

> **The standard operating procedure for transforming an approved architecture into implementation-ready technical designs that enable consistent, maintainable, secure, scalable, and high-quality software development.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. Technical Design Workflow
10. Technical Design Lifecycle
11. Detailed Phase Activities
12. Technical Design Concepts
13. Technical Decision Framework
14. Deliverables
15. Quality Gates
16. Technical Design Checklist
17. AI-Assisted Technical Design
18. Common Mistakes
19. Best Practices
20. Templates
21. Examples
22. Related Principles
23. Related Standards
24. Related References
25. Related Playbooks
26. Metrics
27. Reference Implementation and Enterprise Appendices
28. Revision History
29. Summary

## 1. Overview

Technical design converts an approved architecture into a precise, reviewable plan for implementation. It defines the internal components, interfaces, data structures, behaviours, controls, failure handling, operational signals, configuration, and delivery sequence needed to build a change.

Architecture answers:

> What system should we build, and why is this direction appropriate?

Technical design answers:

> Exactly how will we build this change within the approved architecture?

The playbook begins with an approved architecture baseline and ends when:

- The implementation boundary and responsibilities are explicit.
- Interfaces and data contracts are defined.
- Important behaviours, state transitions, failures, and edge cases are designed.
- Security, privacy, testability, observability, and deployment concerns are addressed.
- Material design decisions trace to requirements and architecture decisions.
- Review findings are resolved or accepted by authorised owners.
- Engineers can estimate, sequence, implement, and test the work without inventing material design during coding.

Technical design is not a second architecture process. A design may refine an approved direction, but it must not silently change system boundaries, architectural drivers, material technology choices, or accepted risks.

## 2. Purpose

This playbook establishes a repeatable way to:

- Translate approved architecture into implementation-ready designs.
- Define component responsibilities and collaboration boundaries.
- Make interface, API, event, and data contracts explicit.
- Design normal, exceptional, degraded, and recovery behaviour.
- Integrate security, validation, observability, configuration, and deployment concerns before coding.
- Expose uncertainty and reduce high-cost implementation risk.
- Create traceability from requirements and architecture to code, tests, releases, and operational evidence.
- Give engineers a shared baseline for estimation, implementation, review, and change control.

## 3. Objectives

Following this playbook should produce:

- A Technical Design Document (TDD).
- Component or module specifications.
- API, event, and interface contracts.
- Database and persistence design.
- Data-flow, sequence, and state views where needed.
- Error-handling and recovery design.
- Security, privacy, and validation design.
- Logging, metrics, tracing, and alerting design.
- Configuration and deployment considerations.
- An implementation and rollout plan.
- A coding-readiness decision with recorded approval.

The depth of each output must be proportionate to risk. The goal is enough design to build safely, not maximum documentation.

## 4. Scope

### In Scope

Apply this playbook to:

- New components, modules, services, integrations, or material features.
- New software systems, shared libraries, platform capabilities, and infrastructure automation.
- Changes to public or cross-team contracts.
- New or materially changed data models and migrations.
- Security-sensitive, regulated, or high-risk behaviour.
- Work with complex state, concurrency, failure, or recovery behaviour.
- Changes affecting deployment, operability, or several engineering disciplines.
- Implementation that consumes an approved architecture package.

### Proportionate Application

| Change Profile | Expected Design Depth |
|---|---|
| Small, local, reversible | Focused design note, affected contract, tests, and reviewer approval |
| Material feature or integration | TDD, component and interface design, data and failure design, review record |
| High-risk, regulated, or multi-team | Full design package, prototypes where needed, multidisciplinary review, formal approval |

### Out of Scope

This playbook does not:

- Revalidate the business need or replace `PB-REQ`.
- Select or approve the system architecture; use `PB-ARCH`.
- Author production code.
- Replace coding, testing, security, deployment, or operational playbooks.
- Require class diagrams or low-level detail when they do not reduce risk.
- Permit unapproved architectural deviation.
- Treat generated code or diagrams as evidence of design correctness.

## 5. When to Use This Playbook

Start technical design when:

- The architecture is approved or approved with workable conditions.
- The implementation scope and owners are known.
- Relevant requirements and acceptance criteria are available.
- Material architecture decisions and quality thresholds are accessible.
- The team needs shared detail before coding.

Re-enter this playbook when:

- Implementation reveals a material design gap.
- A contract, data model, security control, or operational assumption changes.
- Test, deployment, or production evidence invalidates a design assumption.
- A review finding requires redesign.
- An architectural change is approved and the design baseline must be updated.

A short design may be sufficient for a low-risk change. Skipping design is acceptable only when the accountable engineering lead records why the change is local, reversible, understood, and adequately covered by existing patterns.

## 6. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| Technical Design Owner | Coordinates the design, resolves cross-cutting concerns, maintains coherence, and owns the final package |
| Architecture Owner | Confirms alignment with the approved architecture and evaluates material deviations |
| Engineering Lead | Confirms buildability, sequencing, ownership, maintainability, and coding readiness |
| Implementing Engineers | Supply implementation knowledge, challenge assumptions, estimate work, and confirm the design is executable |
| API or Integration Owner | Owns interface compatibility, consumer impact, error semantics, and contract evolution |
| Data Owner | Owns data meaning, integrity, lifecycle, migration, retention, residency, and access expectations |
| Security or Privacy Reviewer | Reviews trust boundaries, threats, permissions, secrets, validation, and privacy controls |
| Quality Engineer | Defines test strategy, verification evidence, edge cases, and acceptance coverage |
| Operations or Platform Engineer | Reviews configuration, deployment, observability, capacity, resilience, recovery, and supportability |
| Product Owner | Clarifies intended behaviour, acceptance criteria, priorities, and user-visible trade-offs |
| Approver | Records approval, conditions, rejection, or escalation within delegated authority |

One person may perform several roles. Each required concern must still have a named accountable owner.

### Responsibility Rules

- The design owner integrates decisions; they do not decide every specialist concern alone.
- Implementers participate before approval, not only after handover.
- Contract and data owners approve changes within their domains.
- The architecture owner decides whether a proposed deviation returns to `PB-ARCH`.
- AI tools may draft or analyse; named people remain accountable for correctness and approval.

## 7. Inputs

| Input | Required Information |
|---|---|
| Approved architecture package | System boundaries, major responsibilities, interaction model, deployment assumptions, and approval conditions |
| Architecture Decision Records | Consequential choices, alternatives, consequences, and review triggers |
| Requirements baseline | Functional requirements, non-functional requirements, acceptance criteria, priorities, and traceable identifiers |
| Architecture views | Context, component, data-flow, security, deployment, and sequence views relevant to the change |
| Quality thresholds | Measurable security, reliability, performance, scalability, maintainability, and operability expectations |
| Constraints and assumptions | Fixed limits, open assumptions, evidence, owners, and review conditions |
| Current implementation | Existing modules, contracts, schemas, dependencies, conventions, and known debt |
| Standards and references | Applicable engineering rules, terminology, identifiers, and approved patterns |
| Delivery context | Team ownership, environments, release approach, schedule, budget, and dependency constraints |
| Risk register | Material technical, security, data, delivery, and operational risks |

Every authoritative input must have a stable source. Do not copy information into the TDD when a maintained source can be referenced.

## 8. Entry Criteria

Before beginning, confirm:

- The architecture outcome is Approved or Approved with Conditions.
- Blocking architecture conditions are resolved or explicitly carried into the design.
- The design scope, owner, reviewers, and approver are named.
- Requirements and acceptance criteria are sufficient for the selected scope.
- Applicable ADRs, constraints, quality thresholds, and risks are available.
- Current contracts, data structures, and implementation constraints have been inspected.
- Open questions have owners and resolution dates.

If a missing input changes the system direction, return to `PB-ARCH`. If it changes the business outcome or acceptance criteria, return to `PB-REQ`.

## 9. Technical Design Workflow

| Phase | Goal | Exit Decision |
|---|---|---|
| 1. Understand Approved Architecture | Establish the design baseline, scope, constraints, and unresolved conditions | Is the approved direction understood well enough to design? |
| 2. Decompose into Components | Define responsibilities, boundaries, dependencies, and ownership | Are component boundaries coherent and buildable? |
| 3. Design Interfaces and Contracts | Specify synchronous, asynchronous, internal, and external interactions | Can producers and consumers implement independently and safely? |
| 4. Design Data and Persistence | Define models, ownership, integrity, lifecycle, access, and migration | Is data behaviour complete, safe, and recoverable? |
| 5. Design Security and Validation | Define trust, identity, authorisation, validation, privacy, and abuse controls | Are threats and invalid inputs handled by design? |
| 6. Design Operational Concerns | Define failure handling, observability, configuration, capacity, deployment, and recovery | Can the change be operated and supported? |
| 7. Validate Technical Design | Test high-risk assumptions and internal consistency | Is there sufficient evidence for review? |
| 8. Technical Review | Conduct multidisciplinary review and resolve findings | Is the design ready for an approval decision? |
| 9. Approval and Handover | Baseline the design and transfer it to implementation | May coding start under this design? |

```text
Approved Architecture
        │
        ▼
Understand Architecture
        │
        ▼
Decompose Components
        │
        ▼
Design Interfaces
        │
        ▼
Design Data
        │
        ▼
Design Security
        │
        ▼
Design Operations
        │
        ▼
Validate
        │
        ▼
Technical Review
        │
        ▼
Approval and Handover
        │
        ▼
Coding
```

Teams may iterate between phases. New evidence must update affected decisions, diagrams, risks, and traceability before approval.

## 10. Technical Design Lifecycle

The TDD is a controlled baseline, not a document abandoned after coding starts.

```text
Draft Design
      │
      ▼
Reviewed Design
      │
      ▼
Approved Baseline
      │
      ▼
Implementation Verification
      │
      ▼
Deployment Evidence
      │
      ▼
Maintenance or Supersession
```

During implementation:

- Minor clarifications update the TDD through normal versioning.
- Material technical changes require renewed review.
- Architectural deviations return to `PB-ARCH` and may require a new or superseding ADR.
- Code, tests, migrations, and operational artefacts must remain traceable to the approved design.
- Obsolete designs are superseded or retired according to the ILOS lifecycle.

## 11. Detailed Phase Activities

### Phase 1: Understand Approved Architecture

**Objective:** Establish the authoritative baseline and the exact implementation scope.

**Activities:**

1. Read the architecture package, ADRs, requirements, approval conditions, risks, and validation evidence.
2. Identify the system boundary, affected capabilities, quality thresholds, constraints, and assumptions.
3. Inspect the current implementation and existing patterns.
4. Separate fixed architecture decisions from technical-design choices.
5. Build a traceability map for the change.
6. Record unresolved questions and owners.

**Outputs:**

- Design scope and context.
- Architecture-alignment matrix.
- Open-question and assumption register.
- Initial traceability map.

**Exit criteria:**

- Scope and authority are clear.
- Architecture constraints are understood.
- Missing or conflicting inputs have resolution paths.

### Phase 2: Decompose into Components

**Objective:** Allocate behaviour to cohesive, owned components with explicit boundaries.

**Activities:**

1. Identify responsibilities from use cases and architecture boundaries.
2. Group related behaviour and data by cohesion and ownership.
3. Define module, component, service, job, adapter, and external dependency responsibilities.
4. Map allowed dependencies and prohibited coupling.
5. Identify lifecycle, concurrency, state, and scaling implications.
6. Confirm build, test, deploy, and ownership boundaries.

**Outputs:**

- Component model.
- Responsibility catalogue.
- Dependency map.
- Ownership and change-impact map.

**Exit criteria:**

- Each responsibility has one clear home.
- Dependencies follow the approved architecture.
- Components can be implemented and tested without hidden ownership.

### Phase 3: Design Interfaces and Contracts

**Objective:** Define observable interactions so producers and consumers share one contract.

**Activities:**

1. Identify internal, external, synchronous, asynchronous, batch, and human interfaces.
2. Define request, response, event, command, and callback schemas.
3. Specify validation, identity, authorisation, idempotency, ordering, pagination, timeouts, and retry semantics.
4. Define error codes, failure responses, compatibility rules, and deprecation.
5. Model critical sequences, including failure and recovery paths.
6. Confirm contract ownership and consumer impact.

**Outputs:**

- API or interface specifications.
- Event and message contracts.
- Sequence diagrams.
- Compatibility and evolution plan.

**Exit criteria:**

- Normal and failure contracts are explicit.
- Consumers can test against stable specifications.
- Compatibility and ownership are agreed.

### Phase 4: Design Data and Persistence

**Objective:** Define how data is represented, owned, protected, changed, and recovered.

**Activities:**

1. Define conceptual and logical data models.
2. Assign authoritative ownership and consistency boundaries.
3. Specify identifiers, relationships, constraints, indexes, and integrity rules.
4. Define transaction, concurrency, locking, ordering, and idempotency behaviour.
5. Design query and access patterns against expected volume and latency.
6. Define migration, backfill, rollback, reconciliation, archival, retention, and deletion.
7. Classify sensitive data and record lineage where required.

**Outputs:**

- Data model and schema design.
- Persistence and access design.
- Migration and rollback plan.
- Data lifecycle and integrity rules.

**Exit criteria:**

- Data ownership and integrity are explicit.
- Migration and failure recovery are feasible.
- Access patterns support required qualities.

### Phase 5: Design Security and Validation

**Objective:** Protect trust boundaries, data, operations, and users before implementation.

**Activities:**

1. Identify actors, identities, trust boundaries, assets, and threats.
2. Define authentication, authorisation, least privilege, and service identity.
3. Define validation and normalisation at every trust boundary.
4. Design secret, key, token, and certificate handling.
5. Define encryption, audit, privacy, consent, retention, and deletion controls.
6. Address abuse, replay, injection, enumeration, resource exhaustion, and unsafe defaults.
7. Map controls to requirements and verification evidence.

**Outputs:**

- Security and privacy design.
- Validation rules.
- Threat and control mapping.
- Audit and sensitive-data handling plan.

**Exit criteria:**

- Material threats have preventive, detective, or recovery controls.
- Permission and validation rules are testable.
- Residual risks have named owners.

### Phase 6: Design Operational Concerns

**Objective:** Make the implementation deployable, observable, resilient, and supportable.

**Activities:**

1. Define error classification, propagation, retries, timeouts, circuit breaking, and fallback.
2. Define logs, metrics, traces, health signals, dashboards, alerts, and correlation identifiers.
3. Define configuration sources, defaults, validation, ownership, and safe change.
4. Estimate capacity, concurrency, resource limits, hot paths, and degradation behaviour.
5. Define deployment topology, dependencies, rollout, rollback, compatibility, and migration ordering.
6. Define startup, shutdown, recovery, backup, restore, and disaster-recovery behaviour where applicable.
7. Define runbook and support information required before release.

**Outputs:**

- Error-handling and resilience design.
- Observability specification.
- Configuration design.
- Deployment and rollback considerations.
- Capacity and recovery assumptions.

**Exit criteria:**

- Failures are bounded and observable.
- Configuration and rollout can be changed safely.
- Operators can detect, diagnose, and recover the change.

### Phase 7: Validate Technical Design

**Objective:** Replace the most consequential uncertainty with evidence.

**Activities:**

1. Rank assumptions by impact, uncertainty, and reversibility.
2. Select the cheapest credible validation method.
3. Prototype complex integrations, concurrency, migrations, or performance-sensitive paths.
4. Review interface and schema compatibility.
5. Walk through normal, failure, recovery, security, and operational scenarios.
6. Check traceability and internal consistency across the design package.
7. Update the design, risks, or architecture based on evidence.

**Outputs:**

- Validation records.
- Prototype or benchmark evidence where needed.
- Updated risk and assumption register.
- Review-ready design package.

**Exit criteria:**

- Critical assumptions have evidence or explicit risk treatment.
- The design satisfies requirements and architecture constraints.
- Known limitations are visible.

### Phase 8: Technical Review

**Objective:** Find material implementation weaknesses before coding makes them expensive.

**Activities:**

1. Apply `STD-REVIEW` with the required disciplines.
2. Review architecture alignment, completeness, simplicity, contracts, data, security, failure handling, observability, deployment, testability, and traceability.
3. Classify findings by severity and impact.
4. Assign owners and due dates.
5. Resolve blocking findings and record conditional actions.
6. Re-review changed areas when resolution is material.

**Outputs:**

- Review record.
- Findings register.
- Updated design package.
- Approval recommendation.

**Exit criteria:**

- Required reviewers participated.
- Blocking findings are resolved.
- Remaining conditions and risks have owners and authority.

### Phase 9: Approval and Handover to Development

**Objective:** Establish the controlled implementation baseline and transfer it without losing intent.

**Activities:**

1. Record Approved, Approved with Conditions, Revisions Required, Rejected, or Escalated.
2. Baseline the TDD, specifications, diagrams, validation evidence, risks, and conditions.
3. Break the design into implementation slices with dependencies and owners.
4. Define code-review, test, migration, release, and operational evidence expected from each slice.
5. Walk implementers through decisions, constraints, failure behaviour, and open conditions.
6. Define change-control and escalation triggers.

**Outputs:**

- Approval record.
- Baseline technical design package.
- Implementation plan.
- Coding-readiness checklist.
- Traceability and change-control handover.

**Exit criteria:**

- Engineers can implement without unresolved material decisions.
- Work items map to design elements and acceptance evidence.
- Conditions, deviations, and review checkpoints are owned.

## 12. Technical Design Concepts

### Architecture Alignment

Every design choice must be one of:

- A direct application of an approved architecture decision.
- A reversible implementation detail within the design owner's authority.
- A material decision requiring an ADR or architecture review.

When uncertain, compare the choice against system boundaries, quality attributes, cross-team impact, cost of reversal, and accepted risk.

### Component Design

A component specification should define:

- Purpose and responsibilities.
- Owned data and state.
- Provided and consumed interfaces.
- Dependencies and prohibited dependencies.
- Normal, exceptional, and lifecycle behaviour.
- Concurrency and consistency expectations.
- Security and operational obligations.
- Owner and test boundary.

### Interface Contracts

A contract is complete when producers and consumers agree on:

- Semantics, not only syntax.
- Valid and invalid inputs.
- Success, partial-success, and failure responses.
- Identity, permissions, idempotency, ordering, timeouts, and retries.
- Compatibility, versioning, deprecation, and ownership.
- Operational limits and observable signals.

### Data Design

Data design must make ownership, meaning, integrity, lifecycle, and access explicit. Storage technology does not replace a data model. Schema diagrams do not replace migration, consistency, recovery, retention, and deletion decisions.

### Behaviour and State

Use sequence or state diagrams when order, concurrency, time, retries, or transitions matter. Model at least:

- Normal flow.
- Invalid input.
- Dependency failure.
- Duplicate or delayed work.
- Partial completion.
- Recovery or compensation.

### Error Handling

Define:

- Error categories and stable error semantics.
- Where errors are detected, translated, logged, retried, or surfaced.
- Retry safety and limits.
- Partial failure and compensation.
- User-visible behaviour.
- Correlation and diagnostic context.

### Observability by Design

Each critical behaviour should identify:

- The signal proving success.
- The signal revealing failure or degradation.
- The context needed to diagnose it.
- The owner and action expected from an alert.

### Implementation Planning

Break work into vertical, testable slices where possible. Each slice should have:

- Scope and owner.
- Design references.
- Dependencies.
- Acceptance and test evidence.
- Migration or rollout considerations.
- Completion and rollback conditions.

## 13. Technical Decision Framework

Use this sequence for consequential technical choices:

1. State the decision and decision owner.
2. Trace the choice to a requirement, architecture constraint, quality threshold, or risk.
3. Define evaluation criteria before selecting an option.
4. Include the simplest viable option and existing pattern.
5. Compare correctness, security, operability, testability, maintainability, cost, and reversibility.
6. Gather evidence where uncertainty is material.
7. Record the outcome at the correct level: TDD, ADR, or architecture review.

### Decision Classification

| Decision Type | Record and Authority |
|---|---|
| Local and easily reversible | TDD decision note; design owner |
| Shared contract or data change | TDD plus affected owner approval |
| Cross-team, long-lived, or costly to reverse | ADR and architecture owner |
| Changes approved architecture or accepted risk | Return to `PB-ARCH` |

### Escalate When

- The design changes an approved system boundary or architectural driver.
- A required quality threshold cannot be met.
- Security, privacy, legal, or data risk exceeds delegated authority.
- A public contract requires an incompatible change.
- Migration or rollback cannot be made acceptably safe.
- Evidence contradicts an ADR or architecture assumption.
- Ownership or approval authority is unresolved.

## 14. Deliverables

| Deliverable | Minimum Content | Required When |
|---|---|---|
| Technical Design Document | Scope, context, decisions, component, interface, data, security, operations, validation, plan | Every material design |
| Component Specifications | Responsibilities, dependencies, state, interfaces, ownership | New or materially changed components |
| API or Interface Specifications | Semantics, schemas, errors, security, compatibility, limits | A contract changes |
| Integration Design | Participants, protocols, ownership, sequencing, failure, reconciliation, and support | A system or external dependency is integrated |
| Database and Data Design | Model, integrity, access, migration, retention, recovery | Persisted data changes |
| Sequence or State Diagrams | Order, transitions, failures, retries, recovery | Behaviour is time- or state-sensitive |
| Security and Validation Design | Trust, permissions, validation, controls, residual risk | Security or privacy exposure exists |
| Observability Design | Logs, metrics, traces, alerts, correlation, ownership | Production behaviour changes |
| Error-Handling Strategy | Classification, propagation, retry, compensation, user impact | Failure behaviour is non-trivial |
| Configuration Design | Sources, defaults, validation, ownership, change safety | Runtime behaviour is configurable |
| Deployment Considerations | Topology, rollout, compatibility, migrations, rollback | Release or runtime behaviour changes |
| Implementation Plan | Slices, dependencies, owners, evidence, checkpoints | Every approved design |
| Coding-Readiness Checklist | Gate evidence and unresolved conditions | Before coding starts |

The TDD may link to maintained specifications rather than duplicate them.

## 15. Quality Gates

### Gate A: Baseline Ready

- Architecture and requirements are approved for the design scope.
- Conditions, constraints, risks, and owners are visible.
- The current implementation has been inspected.

### Gate B: Structure and Contracts Ready

- Responsibilities and dependencies are coherent.
- Interfaces include success, failure, compatibility, and ownership.
- Data ownership, integrity, lifecycle, and migration are defined.

### Gate C: Security and Operations Ready

- Trust, permissions, validation, privacy, and residual risk are addressed.
- Error, observability, configuration, capacity, deployment, and recovery behaviour are designed.
- Testability is built into contracts and components.

### Gate D: Evidence and Review Ready

- Critical assumptions have evidence or explicit treatment.
- Required diagrams and specifications agree.
- Traceability is complete.
- Reviewers have a stable package and defined questions.

### Gate E: Coding Ready

- Blocking findings are resolved.
- Approval and conditions are recorded.
- Implementation slices, owners, dependencies, and evidence are defined.
- Change-control triggers are understood.

Failure of a gate returns the design to the relevant phase. Schedule pressure does not convert missing evidence into approval.

## 16. Technical Design Checklist

### Context and Alignment

- [ ] Scope, owner, reviewers, and approver are named.
- [ ] Requirements, architecture decisions, constraints, and risks are linked.
- [ ] Approved architecture is preserved or deviations are escalated.
- [ ] Assumptions and open questions have owners.

### Components and Contracts

- [ ] Responsibilities and dependency directions are explicit.
- [ ] Interfaces define semantics, validation, failures, security, and compatibility.
- [ ] Critical sequences and state transitions include failure and recovery.
- [ ] Component and contract owners are named.

### Data

- [ ] Data meaning, ownership, integrity, and access patterns are defined.
- [ ] Transactions, concurrency, idempotency, and consistency are addressed.
- [ ] Migration, rollback, reconciliation, retention, and deletion are safe.
- [ ] Sensitive data is classified and protected.

### Security and Operations

- [ ] Trust boundaries, permissions, validation, secrets, and audit needs are covered.
- [ ] Errors, retries, timeouts, degradation, and recovery are designed.
- [ ] Logs, metrics, traces, dashboards, and alerts support diagnosis.
- [ ] Configuration, capacity, deployment, compatibility, and rollback are addressed.

### Validation and Handover

- [ ] Critical assumptions have credible evidence.
- [ ] Review findings are resolved or authorised.
- [ ] Work items trace to the design and required evidence.
- [ ] Coding-readiness approval is recorded.

## 17. AI-Assisted Technical Design

AI may accelerate analysis and drafting. It cannot own context, accept risk, or approve a design.

| Activity | AI Can Help | Engineer Must |
|---|---|---|
| Analyse inputs | Summarise requirements, ADRs, constraints, and open questions | Verify sources, omissions, priorities, and authority |
| Component design | Suggest decomposition and known patterns | Select boundaries and test fit with the real codebase |
| Interface design | Draft schemas, examples, and compatibility checks | Confirm semantics, consumers, security, and evolution |
| Data design | Suggest models, constraints, indexes, and migration cases | Validate integrity, access patterns, volume, privacy, and recovery |
| Behaviour modelling | Draft sequence and state diagrams | Verify ordering, concurrency, failures, and side effects |
| Security analysis | Suggest threats, abuse cases, and missing controls | Perform threat review and accept residual risk |
| Operational design | Suggest signals, alerts, failure modes, and runbook topics | Confirm actionable telemetry and operating ownership |
| Validation | Generate edge cases and consistency checks | Select evidence and judge whether it is sufficient |
| Documentation | Draft TDD sections and trace links | Confirm accuracy, provenance, clarity, and completeness |
| Review | Identify contradictions and checklist gaps | Make findings, decisions, and approval accountable |

### AI Guardrails

- Provide only information permitted by security and data policy.
- Treat generated facts, code, diagrams, and citations as untrusted until verified.
- Inspect the actual implementation and authoritative contracts.
- Record meaningful AI use when policy or risk requires it.
- Never let AI approve a design, accept risk, or decide an architectural deviation.
- Preserve a human-readable rationale for every consequential decision.

## 18. Common Mistakes

### Reopening Architecture Silently

Changing system boundaries or material technology choices in a TDD bypasses approved decisions. Escalate the deviation.

### Designing from a Blank Page

Ignoring the current implementation creates unnecessary variation. Inspect and reuse established patterns when they remain fit.

### Treating Diagrams as the Design

A diagram without contracts, failures, ownership, and decisions cannot guide implementation.

### Specifying Only the Happy Path

Production behaviour is defined by invalid input, retries, partial failure, recovery, and change.

### Mixing Semantics with Transport

An endpoint or message format does not explain the business meaning, invariants, ownership, or compatibility promise.

### Deferring Security and Operations

Security, observability, migration, and rollback added after coding usually expose avoidable redesign.

### Overdesigning Internal Detail

Premature class and method detail makes the design expensive to maintain without reducing meaningful risk.

### Hiding Uncertainty

Unrecorded assumptions become accidental commitments. Name uncertainty and validate the costly parts.

### Approving Without Implementers

A design that reviewers accept but implementers cannot build is not coding ready.

## 19. Best Practices

- Start with approved constraints and current code, not preferred patterns.
- Keep one authoritative source for each contract.
- Design from observable behaviours and invariants.
- Make failure, migration, recovery, and compatibility first-class.
- Prefer simple, reversible decisions until evidence justifies complexity.
- Design test seams and operational signals with the component.
- Use diagrams only when relationships, sequence, state, or deployment become clearer.
- Review high-risk areas early rather than presenting a finished document late.
- Keep the TDD current during implementation.
- Record why a decision was made, not only what was selected.

## 20. Templates

### Technical Design Document

```markdown
# <Change> Technical Design

## Metadata
ID, version, status, owner, reviewers, approver, dates

## Context and Scope
Problem, outcomes, in scope, out of scope, affected users and systems

## Source Artefacts
Requirements, architecture package, ADRs, standards, risks

## Design Summary
Selected approach, key decisions, constraints, assumptions

## Component Design
Responsibilities, ownership, dependencies, lifecycle

## Interfaces and Behaviour
Contracts, sequences, state, validation, errors, compatibility

## Data Design
Models, ownership, integrity, access, migration, retention, recovery

## Security and Privacy
Trust, identity, permissions, threats, controls, residual risk

## Operational Design
Failure handling, observability, configuration, capacity, deployment, rollback

## Validation
Questions, methods, evidence, limitations, resulting changes

## Implementation Plan
Slices, owners, dependencies, tests, rollout, checkpoints

## Risks and Open Questions
Impact, owner, treatment, due date

## Review and Approval
Findings, conditions, decision, authority, date
```

### Component Specification

| Field | Content |
|---|---|
| Component | Stable name and identifier |
| Purpose | One responsibility-focused statement |
| Owner | Accountable team or person |
| Responsibilities | Behaviours owned |
| Exclusions | Behaviours intentionally not owned |
| Interfaces | Provided and consumed contracts |
| State and data | Owned state and consistency rules |
| Dependencies | Allowed dependencies and failure assumptions |
| Security | Trust, identity, permissions, sensitive data |
| Operations | Signals, limits, failure, recovery |
| Verification | Unit, integration, contract, and operational evidence |

### Interface Contract

| Field | Content |
|---|---|
| Name and owner | Stable contract identity and accountable owner |
| Purpose | Business and technical semantics |
| Consumers | Known callers and impact |
| Input and output | Schemas, constraints, examples |
| Behaviour | Success, partial success, failure, side effects |
| Control | Identity, permissions, idempotency, ordering, limits |
| Resilience | Timeout, retry, duplicate, degradation behaviour |
| Evolution | Versioning, compatibility, deprecation |
| Operations | Metrics, logs, traces, alerts |

### Data Change Plan

| Stage | Action | Compatibility | Verification | Rollback |
|---|---|---|---|---|
| Prepare | Add compatible structures | Old and new code work | Schema check | Remove unused addition |
| Migrate | Backfill or transform | Reads remain safe | Reconciliation | Restore or reverse batch |
| Switch | Move reads or writes | Controlled cutover | Behaviour and data checks | Return to prior path |
| Clean up | Remove obsolete structures | Consumers confirmed | Dependency scan | New migration if needed |

### Validation Record

```text
Question:
Decision affected:
Risk if wrong:
Method:
Success threshold:
Evidence:
Limitations:
Outcome:
Design change:
Owner:
Date:
```

## 21. Examples

### Example: Order Creation Design

**Architecture baseline:** A modular monolith owns order creation. A payment provider is external. PostgreSQL is the authoritative store. The public interaction is REST.

**Technical design:**

1. `Orders` owns order state and invariants.
2. `Payments` owns provider interaction and payment status.
3. `POST /orders` requires an idempotency key and returns a stable order identifier.
4. The request validates customer, lines, currency, and totals before persistence.
5. Order creation and the outbound payment request use a transactional outbox so committed work is not lost.
6. Duplicate requests return the original result when the idempotency key and payload match.
7. Provider timeout leaves the order in `PAYMENT_PENDING`; a bounded retry worker continues processing.
8. Metrics cover creation success, validation failures, duplicate requests, payment latency, retry depth, and terminal failures.
9. The implementation is split into schema, order behaviour, contract, provider adapter, worker, observability, and rollout slices.

```text
Client
  │ POST /orders
  ▼
Order API
  │ validate + idempotency check
  ▼
Orders Module ── transaction ──► Order + Outbox
                                  │
                                  ▼
                              Payment Worker
                                  │
                                  ▼
                           Payment Provider
```

The architecture remains unchanged. The TDD adds the contracts, state, failure behaviour, persistence mechanics, and operational evidence needed to implement it.

### Example: Architectural Deviation

During design, the team proposes splitting `Payments` into an independently deployed service to meet an assumed scaling need.

This is not a local technical-design detail. It changes deployment, ownership, failure, data, and interaction boundaries. The design owner records the proposal and evidence, then returns it to `PB-ARCH`. The TDD remains aligned with the current baseline until the architecture decision changes.

## 22. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Architecture Principles](../01-principles/03-architecture-principles.md)
- [Coding Principles](../01-principles/04-coding-principles.md)
- [Testing Principles](../01-principles/05-testing-principles.md)
- [Security Principles](../01-principles/06-security-principles.md)
- [Observability Principles](../01-principles/07-observability-principles.md)
- [Performance Principles](../01-principles/08-performance-principles.md)

## 23. Related Standards

- [Playbook Authoring Standard](../03-standards/PB-AUTHORING.md)
- [Engineering Review Standard](../03-standards/STD-REVIEW.md)
- [Engineering Traceability Standard](../03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](../03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](../03-standards/STD-VERSIONING.md)
- [Engineering Terminology Standard](../03-standards/TERM-STANDARD.md)
- [Documentation Style Guide](../03-standards/DOC-STYLE.md)

## 24. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)

## 25. Related Playbooks

- [Requirements Playbook](PB-REQ.md) provides the requirements baseline.
- [Architecture Playbook](PB-ARCH.md) provides the approved architecture package and governs material deviations.
- [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md) governs responsible AI assistance across the engineering lifecycle.
- [`PB-CODING`](PB-CODING.md) consumes the approved design and implementation plan.
- [Code Review Playbook](06-code-review-playbook.md) will verify implementation against the design.
- [Testing Playbook](07-testing-playbook.md) will produce verification evidence.
- [Deployment Playbook](12-deployment-playbook.md) will execute rollout and rollback controls.
- [Observability Playbook](10-observability-playbook.md) will operationalise the design signals.
- [Technical Decision Playbook](15-technical-decision-playbook.md) will govern detailed decision practice.

## 26. Metrics

Use metrics to improve the design process, not to reward document volume.

| Metric | Meaning | Warning |
|---|---|---|
| Design lead time | Time from ready inputs to coding-ready approval | Segment waiting time from active design work |
| First-review acceptance | Designs without blocking findings at first review | A high rate may also indicate weak review |
| Finding escape rate | Material design issues found during coding, testing, or production | Classify by root cause, not blame |
| Architectural deviation rate | Designs requiring architecture re-entry | Distinguish healthy discovery from bypass |
| Contract change failure rate | Failures caused by incompatible or ambiguous contracts | Include internal, external, and event contracts |
| Migration defect rate | Data defects caused by migrations or backfills | Track detection and recovery time |
| Traceability completeness | Required design elements linked to source and evidence | Sample meaning, not only link presence |
| Rework caused by design gaps | Delivery effort spent resolving missing or incorrect design | Use trends to improve templates and gates |
| Review condition closure | Conditions closed by agreed dates | Do not hide overdue conditions by reclassification |

Review trends by risk class. A low-risk design and a regulated multi-team design should not have identical cycle-time targets.

## 27. Reference Implementation and Enterprise Appendices

`PB-TECH-DESIGN` is the second flagship ILOS playbook and the reference implementation for playbooks that convert an approved upstream baseline into execution-ready engineering work. It inherits the governance, traceability, review, and navigation model established by `PB-ARCH` while adding the implementation detail required before coding.

Future delivery playbooks should reuse this pattern where they need:

- Explicit entry and exit criteria.
- Phase ownership, outputs, and quality gates.
- Traceability from an approved baseline into implementation evidence.
- Human-accountable AI assistance.
- Review, approval, handover, and change control.

### 27.1 Phase Governance Matrix

| Phase | Accountable Role | Required Reviewers | Primary Outputs | Gate |
|---|---|---|---|---|
| 1. Understand Architecture | Technical Design Owner | Architecture Owner, Engineering Lead | Scope, alignment, trace map | A |
| 2. Decompose Components | Engineering Lead | Implementers, Architecture Owner | Component and dependency model | B |
| 3. Design Interfaces | Contract Owner | Consumers, Security, Quality | Interface specs and sequences | B |
| 4. Design Data | Data Owner | Implementers, Security, Operations | Data and migration design | B |
| 5. Design Security | Security or Privacy Reviewer | Design Owner, Operations | Controls and residual risks | C |
| 6. Design Operations | Operations or Platform Engineer | Engineering, Quality, Security | Failure, telemetry, deployment design | C |
| 7. Validate | Technical Design Owner | Relevant specialists | Evidence and updated risks | D |
| 8. Review | Engineering Reviewer | Required disciplines | Findings and recommendation | D |
| 9. Approve and Handover | Approver | Design Owner, Engineering Lead | Baseline and implementation plan | E |

### 27.2 Traceability Model

```text
Business Objective
        │
        ▼
Requirement / NFR
        │
        ▼
Architecture Decision
        │
        ▼
Technical Design Element
        │
        ├───────────────┐
        ▼               ▼
Implementation     Test Evidence
        │               │
        └───────┬───────┘
                ▼
        Release and Operational Evidence
```

Each material design element should identify:

- Source requirement or quality threshold.
- Governing architecture decision.
- Owning implementation work.
- Verification evidence.
- Release or operational evidence where applicable.

### 27.3 Interface Review Checklist

- [ ] Semantics and ownership are explicit.
- [ ] Inputs, outputs, constraints, and examples agree.
- [ ] Identity, permissions, validation, and sensitive data are addressed.
- [ ] Idempotency, ordering, timeouts, retries, and limits are defined.
- [ ] Error and partial-success behaviour is stable.
- [ ] Compatibility, versioning, and deprecation protect consumers.
- [ ] Contract and integration tests are planned.
- [ ] Operational signals identify consumer and provider failures.

### 27.4 Data Design Checklist

- [ ] Data meaning and authoritative owner are named.
- [ ] Identifiers, relationships, constraints, and invariants are explicit.
- [ ] Read and write patterns match volume and latency needs.
- [ ] Transaction, consistency, concurrency, and duplicate handling are designed.
- [ ] Migration, backfill, validation, cutover, and rollback are tested.
- [ ] Retention, deletion, archival, privacy, residency, and audit needs are met.
- [ ] Reconciliation and recovery can detect and repair partial failure.

### 27.5 Security and Privacy Checklist

- [ ] Actors, assets, trust boundaries, and threats are identified.
- [ ] Authentication, authorisation, and least privilege are defined.
- [ ] Every trust boundary validates and normalises input.
- [ ] Secrets and sensitive data have controlled storage, transport, access, and rotation.
- [ ] Abuse, replay, injection, enumeration, and resource exhaustion are considered.
- [ ] Audit events support accountability without exposing secrets.
- [ ] Residual risks have authorised owners.

### 27.6 Operational Readiness Checklist

- [ ] Error categories and user-visible behaviour are defined.
- [ ] Retry, timeout, fallback, compensation, and degradation are bounded.
- [ ] Logs, metrics, traces, health checks, dashboards, and alerts are actionable.
- [ ] Configuration has safe defaults, validation, ownership, and rollback.
- [ ] Capacity and resource limits have evidence or monitored assumptions.
- [ ] Deployment, schema change, compatibility, rollout, and rollback order are safe.
- [ ] Backup, restore, recovery, and support information match risk.

### 27.7 Technical Review Agenda

1. Confirm scope, decision authority, and required reviewers.
2. Restate requirements, architecture constraints, and approval conditions.
3. Walk through component responsibilities and dependencies.
4. Review critical contracts, sequences, and state.
5. Review data integrity, migration, and recovery.
6. Review security, privacy, failure, observability, and deployment.
7. Present validation evidence and known limitations.
8. Classify findings and assign owners.
9. Agree the recommendation and next gate.

### 27.8 Approval Workflow

```text
Review-Ready Design
        │
        ▼
Technical Review
        │
        ├── Blocking findings ──► Revise and re-review
        │
        ▼
Approval Decision
        │
        ├── Approved
        ├── Approved with Conditions
        ├── Revisions Required
        ├── Rejected
        └── Escalated to Architecture or Governance
        │
        ▼
Baseline and Handover
```

An approval record must include:

- Design ID and version.
- Outcome, date, approver, and authority.
- Review participants.
- Conditions, owners, and due dates.
- Accepted residual risks.
- Required implementation checkpoints.
- Triggers for renewed technical or architecture review.

### 27.9 Deliverables Checklist

- [ ] Technical Design Document.
- [ ] Component and ownership specifications.
- [ ] Interface, API, or event contracts.
- [ ] Data model, integrity rules, and migration plan.
- [ ] Sequence and state diagrams where behaviour requires them.
- [ ] Security, privacy, and validation design.
- [ ] Error-handling and recovery strategy.
- [ ] Observability and configuration design.
- [ ] Deployment, compatibility, rollout, and rollback considerations.
- [ ] Validation evidence and risk register.
- [ ] Review and approval record.
- [ ] Implementation plan and coding-readiness checklist.

### 27.10 Technical Design Maturity Model

| Level | Characteristics |
|---|---|
| 1. Ad Hoc | Material decisions occur during coding; contracts and failures are implicit |
| 2. Repeatable | Teams use a TDD and review important changes, but coverage varies |
| 3. Defined | Nine phases, gates, roles, templates, and traceability are standard |
| 4. Measured | Escaped gaps, rework, contract failures, and review outcomes improve the process |
| 5. Adaptive | Design depth and validation respond to evidence, risk, and operational learning |

Maturity measures repeatability and learning, not document length.

### 27.11 Coding-Readiness Gate

Before marking this playbook Approved as a reference-quality document, reviewers must confirm that a team can use it to:

- Consume a real approved architecture package.
- Produce every required implementation-focused deliverable.
- Distinguish technical choices from architectural deviations.
- Design normal, failure, migration, recovery, security, and operational behaviour.
- Apply phase roles, outputs, exit criteria, gates, and approval.
- Trace requirements through design into implementation and evidence.
- Use AI assistance without transferring human accountability.
- Hand over a design that implementers can estimate, build, and test.

Failure of any item keeps the playbook in Draft.

## 28. Revision History

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0.3 | 2026-07-30 | Invara Labs Engineering | Linked the downstream `PB-CODING` execution playbook |
| 1.0.2 | 2026-07-30 | Invara Labs Engineering | Updated the AI control-layer identity to `PB-AI-ENGINEERING` |
| 1.0.1 | 2026-07-30 | Invara Labs Engineering | Linked the cross-lifecycle `PB-AI-DEVELOPMENT` control layer |
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Initial Draft flagship playbook with nine-phase workflow, implementation deliverables, quality gates, templates, AI controls, and enterprise appendices |

## 29. Summary

The Technical Design Playbook turns approved architecture into a controlled, implementation-ready baseline.

It defines how teams:

- Understand architecture and requirements.
- Decompose responsibilities.
- Design contracts, data, security, failures, observability, and deployment.
- Validate uncertainty.
- Review and approve the design.
- Hand work to development with traceability and change control.

`PB-ARCH` establishes what system should be built and why. `PB-TECH-DESIGN` establishes exactly how the approved direction will be implemented. Together they provide the design foundation for coding, review, testing, deployment, and operation.
