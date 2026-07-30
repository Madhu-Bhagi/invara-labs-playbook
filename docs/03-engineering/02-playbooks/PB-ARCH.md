---
title: Architecture Playbook
id: PB-ARCH
version: 1.1.0
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
  - architecture
  - design
  - decision-making
  - playbook
related:
  - EP-001
  - EP-002
  - EP-004
  - EP-005
  - AR-001
  - AR-002
  - AR-003
  - AR-004
  - AR-005
  - AR-006
  - AR-007
  - AP-001
  - PB-REQ
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

# Architecture Playbook

> **The standard operating procedure for turning a validated business need into an approved architecture package that teams can design, build, operate, and evolve with confidence.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. Architecture Workflow
10. Architecture Lifecycle
11. Detailed Phase Activities
12. Architecture Concepts and Activities
13. Decision Framework
14. Deliverables
15. Quality Gates
16. Architecture Checklist
17. AI-Assisted Architecture
18. Common Mistakes
19. Best Practices
20. Templates
21. Examples
22. Related Principles
23. Related Standards
24. Related References
25. Related Playbooks
26. Metrics
27. Revision History
28. Summary

## 1. Overview

Software architecture is the process of making and communicating the decisions that shape a system's structure, qualities, boundaries, dependencies, delivery model, and operation.

This playbook begins after a business need and its requirements are sufficiently understood. It ends when the architecture is:

- Proportionate to the system's risk and expected lifetime.
- Traceable to business goals, requirements, constraints, and quality attributes.
- Supported by explicit decisions and evidence.
- Reviewed by the people who must build, secure, test, operate, and fund it.
- Detailed enough to guide technical design without prescribing every implementation detail.

The playbook does not select a preferred architecture style. A monolith, modular monolith, service-oriented system, event-driven system, or another style may be appropriate. The workflow determines suitability from context rather than fashion.

## 2. Purpose

This playbook helps teams:

- Translate business intent into a buildable system direction.
- Identify architectural drivers before choosing technologies.
- Compare viable alternatives using explicit criteria.
- Make trade-offs visible and reviewable.
- Control technical, security, delivery, and operational risk.
- Produce the minimum architecture evidence needed for confident execution.
- Preserve decisions so future teams understand why the system is shaped as it is.

## 3. Objectives

Following this playbook should produce:

- A shared architecture vision.
- Agreed scope and system boundaries.
- Prioritised quality attributes with measurable scenarios.
- A record of material constraints and assumptions.
- A selected architecture approach with rejected alternatives.
- Explicit Architecture Decision Records (ADRs) for consequential choices.
- Early evidence that critical risks are acceptable.
- Clear handoff into technical design and delivery.
- A plan for validating and evolving the architecture.

## 4. Scope

### In Scope

Apply this playbook to:

- New products, platforms, services, and integrations.
- Material changes to system boundaries or interaction models.
- Major migrations and modernisation programmes.
- New data, security, reliability, or deployment models.
- Technology choices with long-lived operational or commercial consequences.
- Changes that affect multiple teams or business capabilities.
- Architecture remediation following material incidents or risk findings.

### Proportionate Application

The depth of architecture work depends on:

- Business criticality.
- Security, privacy, legal, and regulatory exposure.
- Cost of failure or reversal.
- Expected lifetime.
- Number of teams and dependencies.
- Novelty and uncertainty.
- Operational scale and reliability needs.

A low-risk internal tool may need a one-page architecture brief and one ADR. A regulated platform may need several views, threat modelling, prototypes, formal review evidence, and staged approval.

### Out of Scope

This playbook does not:

- Replace requirements engineering.
- Define detailed class, function, database-column, or endpoint designs.
- Prescribe a vendor, framework, cloud, or architecture style.
- Replace security, data, deployment, or operational review.
- Require an ADR for every reversible implementation detail.
- Justify speculative design for unvalidated future needs.

## 5. When to Use This Playbook

Start architecture work when:

- The problem, desired outcomes, and primary stakeholders are known.
- Requirements are stable enough to expose the main drivers.
- The proposed change crosses a material technical or organisational boundary.
- Teams need a shared direction before detailed design or implementation.

Re-enter this playbook when:

- A requirement or constraint materially changes.
- Evidence invalidates an architectural assumption.
- A decision creates unacceptable cost, risk, or operational burden.
- An incident reveals a systemic design weakness.
- Scale, ownership, regulation, or business strategy changes.

Do not wait for perfect requirements. Record uncertainty and make only the decisions needed for the current stage.

## 6. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| Business Sponsor | Owns business outcomes, investment constraints, and material business trade-offs |
| Product Owner | Clarifies scope, priorities, users, and product acceptance |
| Architecture Owner | Leads the workflow, integrates concerns, records decisions, and maintains coherence |
| Engineering Lead | Tests buildability, delivery sequencing, team impact, and maintainability |
| Engineers | Contribute implementation knowledge, identify constraints, prototype risks, and challenge assumptions |
| Security or Privacy Reviewer | Evaluates threats, trust boundaries, data protection, and control obligations |
| Data Owner | Defines data meaning, ownership, quality, retention, residency, and access expectations |
| Operations or Platform Engineer | Evaluates deployability, observability, resilience, recovery, support, and cost |
| Quality Engineer | Defines testability and evidence for quality-attribute validation |
| Reviewer or Governance Approver | Confirms decision quality, traceability, risk treatment, and readiness |

One person may perform several roles on small projects. Accountability must still be explicit.

### Responsibility Rules

- The architecture owner coordinates; they do not decide every concern alone.
- The decision owner accepts the consequences of a material choice.
- Reviewers challenge the reasoning, not the seniority of the author.
- AI tools may assist; named people remain accountable.

## 7. Inputs

| Input | What It Must Explain |
|---|---|
| Problem statement | The problem, affected users, and reason to act |
| Business objectives | The outcomes and measures the architecture must enable |
| Functional requirements | The capabilities and behaviours the system must support |
| Quality attributes | The required security, reliability, performance, scalability, operability, maintainability, and usability |
| Constraints | Fixed legal, organisational, financial, technical, schedule, or contractual limits |
| Current-state architecture | Existing systems, boundaries, dependencies, data, and operational conditions |
| Stakeholder concerns | What each affected group needs protected or improved |
| Risk and assumption logs | What may invalidate the design or require evidence |
| Delivery context | Team structure, skills, sequencing, budget, and timeline |

Every important input should have an owner and authoritative source.

## 8. Entry Criteria

Before beginning, confirm that the team has:

- A named business sponsor or accountable product owner.
- A clear problem statement and desired outcomes.
- Relevant functional and non-functional requirements.
- Known stakeholders and decision-makers.
- Initial scope, constraints, assumptions, and risks.
- Access to current system and integration information.
- A named architecture owner.

If critical inputs are missing, return them to `PB-REQ` rather than concealing uncertainty inside the design.

## 9. Architecture Workflow

| Phase | Objective | Exit Decision |
|---|---|---|
| 1. Understand the Problem | Establish context, scope, stakeholders, and constraints | Is the problem understood well enough to design? |
| 2. Define Architectural Drivers | Prioritise requirements, quality attributes, constraints, and risks | Are the forces shaping the design explicit and measurable? |
| 3. Explore Solution Options | Generate and compare viable approaches | Have credible alternatives been evaluated? |
| 4. Select the Architecture | Choose the simplest option that satisfies the drivers | Are trade-offs understood and owned? |
| 5. Validate the Design | Test critical assumptions and quality attributes | Is there enough evidence to proceed? |
| 6. Record Decisions | Capture consequential choices in ADRs | Can future teams understand why the choices were made? |
| 7. Architecture Review | Conduct multidisciplinary review and resolve findings | Is the architecture ready for an approval decision? |
| 8. Approval | Record approval, conditions, rejection, or escalation | May the architecture become the delivery baseline? |
| 9. Handover to Development | Transfer decisions, constraints, risks, and open work | Can technical design and delivery proceed without losing intent? |

```text
Business Need
      │
      ▼
Understand Problem
      │
      ▼
Define Architectural Drivers
      │
      ▼
Explore Solution Options
      │
      ▼
Select Architecture
      │
      ▼
Validate Design
      │
      ▼
Record ADRs
      │
      ▼
Architecture Review
      │
      ▼
Approval
      │
      ▼
Technical Design and Development
```

Each phase has an explicit output and exit decision. Teams may iterate between phases when new evidence changes the problem, drivers, or selected design.

## 10. Architecture Lifecycle

Architecture continues after handover. Delivery and production evidence may require decisions to be revised through a new or superseding ADR.

```text
Approved Architecture
      │
      ▼
Technical Design
      │
      ▼
Implementation Verification
      │
      ▼
Production Evidence
      │
      ▼
Architecture Evolution
```

## 11. Detailed Phase Activities

### Phase 1: Understand the Problem

This phase combines initiation and contextual analysis.

**Objective:** Establish ownership, scope, system boundaries, stakeholders, current state, and the outcomes architecture must enable.

**Activities:**

1. Name the architecture owner and approver.
2. Review the problem statement, business objectives, and requirements.
3. Map users, systems, organisations, external actors, and dependencies.
4. Document current-state strengths, constraints, and failure modes.
5. Separate facts, assumptions, preferences, and unknowns.

**Exit criteria:**

- Scope, owners, system boundary, and desired outcomes are clear.
- Stakeholder concerns and existing dependencies are represented.
- Missing requirements have owners and resolution paths.

### Phase 2: Define Architectural Drivers

**Objective:** Identify and prioritise the requirements, quality attributes, constraints, risks, and expected changes that materially shape the design.

**Activities:**

1. Identify critical functional requirements.
2. Express quality attributes as measurable scenarios.
3. Record fixed constraints and validate claimed constraints.
4. Rank drivers and expose conflicts.
5. Identify assumptions requiring evidence.

**Exit criteria:**

- Drivers are prioritised.
- Conflicts are explicit.
- Critical quality attributes have measurable thresholds.

### Phase 3: Explore Solution Options

**Objective:** Generate credible alternatives before committing to a design.

**Activities:**

1. Define evaluation criteria from the drivers.
2. Include the simplest viable option and the current state where relevant.
3. Compare benefits, costs, risks, reversibility, and operational impact.
4. Identify evidence needed to distinguish between options.
5. Retain rejected alternatives and reasons.

**Exit criteria:**

- At least two viable options were considered for consequential choices.
- Evaluation criteria trace to architectural drivers.
- Differences in risk and reversibility are clear.

### Phase 4: Select the Architecture

**Objective:** Choose and communicate the simplest coherent architecture that satisfies the prioritised drivers.

**Activities:**

1. Select the option using the agreed criteria and available evidence.
2. Define system boundaries, major responsibilities, interactions, data flow, trust boundaries, and deployment assumptions.
3. Evaluate technology choices for fitness, support, skills, cost, lock-in, and exit options.
4. State trade-offs and residual risks.
5. Identify review conditions that would invalidate the choice.

**Exit criteria:**

- The selected approach has a clear rationale.
- Consequences are accepted by the appropriate owners.
- The architecture vision is understandable to technical and non-technical stakeholders.

### Phase 5: Validate the Design

**Objective:** Convert the most consequential uncertainty into evidence.

Use the cheapest credible method:

- Prototype for feasibility.
- Benchmark for performance or capacity.
- Threat model for security.
- Failure-mode exercise for resilience and recovery.
- Cost model for commercial risk.
- Migration rehearsal for data or platform change.

Each validation defines the question, threshold, method, evidence, limitations, and decision affected.

**Exit criteria:**

- Critical assumptions have evidence, treatment, or explicit risk acceptance.
- Failed assumptions changed the design or triggered escalation.
- Residual risk owners are named.

### Phase 6: Record Decisions

**Objective:** Preserve the rationale and consequences of material choices.

Create an ADR when a decision is long-lived, costly to reverse, cross-team, risk-bearing, disputed, or necessary for future understanding.

**Exit criteria:**

- Material decisions have ADRs.
- Each ADR records context, alternatives, decision, consequences, owner, status, and review conditions.
- Architecture views and ADRs reference authoritative requirements and evidence.

### Phase 7: Architecture Review

**Objective:** Find material weaknesses before implementation makes them expensive.

Review business alignment, driver coverage, simplicity, security, privacy, data, reliability, performance, operability, delivery feasibility, decision quality, traceability, and residual risk.

Apply `STD-REVIEW`. Classify findings by impact and assign owners and due dates.

**Exit criteria:**

- Required disciplines participated.
- Blocking findings are resolved or awaiting explicit risk acceptance.
- Conditional actions are traceable.

### Phase 8: Approval

**Objective:** Record whether the proposed architecture may govern technical design and delivery.

Possible outcomes:

- Approved.
- Approved with conditions.
- Revisions required.
- Rejected.
- Escalated.

Approval must name the approver, date, conditions, residual risks, and next review trigger. AI cannot approve architecture or accept risk.

**Exit criteria:**

- The outcome and authority are recorded.
- Conditions have owners and dates.
- Rejected or escalated decisions have a clear next action.

### Phase 9: Handover to Development

**Objective:** Transfer architectural intent into technical design and delivery without losing constraints or rationale.

Provide the architecture baseline, ADRs, views, risks, validation evidence, required technical designs, quality thresholds, and architecture review checkpoints.

**Exit criteria:**

- Delivery teams understand boundaries, constraints, open questions, and quality obligations.
- Design ownership and risk-reduction work are assigned.
- Material deviations require review rather than becoming accidental architecture.

## 12. Architecture Concepts and Activities

### Architecture Deliverables

Produce only the outputs needed for the decision and risk level.

### Required Outputs

- Architecture brief.
- Context and system-boundary view.
- Prioritised architectural drivers.
- Quality-attribute scenarios.
- Constraints and assumptions register.
- Architecture options and trade-off analysis.
- Selected architecture vision.
- Material ADRs.
- Risk register with treatment and owners.
- Review record and approval outcome.

### Conditional Outputs

- Component, container, deployment, data-flow, integration, or sequence views.
- Threat model and security-boundary view.
- Data classification and ownership model.
- Proof of concept, benchmark, or operational simulation.
- Migration and coexistence architecture.
- Cost model.
- Architecture runway or staged evolution plan.

An output is complete when its reader can use it to make or execute a decision. Diagram volume is not a quality measure.

### Deliverables by Scale

| Change Profile | Expected Deliverables |
|---|---|
| Low-risk, reversible change | Architecture brief, context view, decision note, and focused review |
| Material product or integration | Required outputs, relevant architecture views, ADRs, risk register, and validation evidence |
| High-risk, regulated, or multi-team system | Full required and conditional output set with formal multidisciplinary review |

### Architectural Drivers

A driver is a requirement, quality attribute, constraint, risk, or business objective that materially changes the design. If removing an item would not affect the architecture, it is probably not a driver.

### Quality-Attribute Scenarios

Express critical qualities as observable scenarios:

| Element | Question |
|---|---|
| Source | Who or what creates the event? |
| Stimulus | What happens? |
| Environment | Under what operating condition? |
| Artefact | What part of the system is affected? |
| Response | What must the system do? |
| Measure | What threshold proves success? |

Example:

> During normal operation, when a regional dependency becomes unavailable, customer read requests continue with no more than 1% errors and service is restored to normal within 15 minutes.

Words such as "fast", "scalable", "secure", and "highly available" are not testable without measures.

### Constraints and Assumptions

- A **constraint** limits available choices.
- An **assumption** is believed true but may require validation.

Each should record source, owner, impact, and review condition. Do not present preference as constraint.

### Architecture Views

Create a view only for a named concern and audience.

| View | Typical Concern |
|---|---|
| Context | System boundary and external actors |
| Component or container | Responsibilities and dependencies |
| Data flow | Movement, ownership, classification, and trust |
| Deployment | Runtime placement, scaling, isolation, and recovery |
| Sequence | Important interactions, timing, and failure behaviour |
| Security | Trust boundaries, threats, identities, and controls |
| Evolution | Migration stages, coexistence, and rollback |

Every diagram should have a title, scope, legend where needed, and a short explanation of the decision it supports.

### Architecture Decision Records

Create an ADR when a decision:

- Has material or long-lived consequences.
- Is expensive or risky to reverse.
- Affects several teams or systems.
- Selects a major technology, boundary, data, security, or deployment model.
- Resolves a disputed trade-off.
- Needs future readers to understand why.

An ADR records context, decision, alternatives, consequences, owner, status, and review conditions. Do not use an ADR as a meeting transcript.

### Risk Assessment

For each material risk, record:

- Cause and event.
- Business or technical impact.
- Likelihood and severity.
- Affected driver or decision.
- Prevention, detection, response, and recovery controls.
- Owner and review date.
- Residual risk and acceptance.

### Architecture Validation

Validation is decision-oriented. A prototype that does not change confidence or a decision is exploration, not evidence.

Prefer small, disposable experiments. Production code should not inherit prototype shortcuts without review.

## 13. Decision Framework

For each consequential decision, answer:

1. What decision is required now?
2. Which drivers and constraints govern it?
3. What happens if the decision is deferred?
4. What are the viable options, including the simplest option?
5. What evidence supports each option?
6. Which trade-offs and risks does each option create?
7. How reversible is the choice?
8. Who owns the consequences?
9. What condition should trigger review?

### Decision Criteria

Use weighted scoring only when it clarifies judgement. Never hide weak evidence behind precise numbers.

| Criterion | Example Evidence |
|---|---|
| Business fit | Supported capability and outcome |
| Quality fit | Scenario or benchmark result |
| Simplicity | Components, dependencies, and operational burden |
| Delivery fit | Skills, sequence, and implementation risk |
| Operability | Deployment, observation, support, and recovery |
| Security and compliance | Threats, controls, and obligations |
| Cost | Build, run, support, migration, and exit costs |
| Evolvability | Expected changes and blast radius |

### Escalate When

Escalate a decision when:

- Business outcomes or constraints conflict.
- Required evidence cannot be obtained.
- Residual risk exceeds the owner's authority.
- Teams cannot agree on ownership or operational responsibility.
- A choice creates structural repository or organisation-wide policy.

## 14. Deliverables

| Phase | Required Deliverable |
|---|---|
| Requirements | Approved or review-ready requirement specification |
| Problem Understanding | Architecture brief and context view |
| Drivers | Prioritised driver register and quality-attribute scenarios |
| Options | Option and trade-off analysis |
| Selection | Architecture vision and required views |
| Validation | Validation evidence and updated risk register |
| Decisions | Architecture Decision Records |
| Review | Review report and tracked findings |
| Approval | Approval record with conditions and residual risks |
| Handover | Versioned architecture package |

The architecture package links to authoritative artefacts rather than copying them.

## 15. Quality Gates

### Gate A: Context Ready

- [ ] Problem and outcomes are clear.
- [ ] Scope and system boundary are defined.
- [ ] Stakeholders, owners, and approver are named.
- [ ] Requirements, constraints, assumptions, and current state are available.
- [ ] Architecture effort is proportionate to risk.

### Gate B: Drivers Ready

- [ ] Critical functional requirements are identified.
- [ ] Quality attributes are prioritised and measurable.
- [ ] Conflicting drivers are explicit.
- [ ] Security, privacy, data, operations, and delivery concerns are included.
- [ ] Unknowns have owners.

### Gate C: Decision Ready

- [ ] Viable alternatives were compared.
- [ ] The simplest viable option was considered.
- [ ] Evaluation criteria trace to drivers.
- [ ] Material assumptions have evidence.
- [ ] Trade-offs, consequences, reversibility, and cost are visible.
- [ ] Material decisions have ADRs.

### Gate D: Review Ready

- [ ] Required architecture views are understandable.
- [ ] Critical risks have treatment and owners.
- [ ] Validation evidence meets defined thresholds.
- [ ] Traceability links resolve.
- [ ] Metadata and terminology follow governing standards.
- [ ] Delivery, operations, security, and quality reviewers participated.

### Gate E: Delivery Ready

- [ ] Approval outcome is recorded.
- [ ] Blocking findings are resolved.
- [ ] Conditional actions have owners and dates.
- [ ] Technical-design work is identified.
- [ ] Architecture risks and milestones are in the delivery plan.
- [ ] Evolution and review conditions are defined.

No checklist can replace engineering judgement. A checked box without credible evidence does not pass a gate.

## 16. Architecture Checklist

- [ ] Problem, outcomes, scope, and stakeholders are clear.
- [ ] Functional requirements and quality attributes are traceable.
- [ ] Constraints and assumptions are distinguished.
- [ ] Viable alternatives and the simplest option were evaluated.
- [ ] Trade-offs, reversibility, cost, and operational impact are explicit.
- [ ] Critical risks and assumptions have evidence or owners.
- [ ] Material decisions have ADRs.
- [ ] Required architecture views are understandable.
- [ ] Security, data, operations, quality, and delivery concerns were reviewed.
- [ ] Approval status, conditions, and residual risks are recorded.
- [ ] The handover package enables technical design and development.

## 17. AI-Assisted Architecture

| Phase Activity | AI Can Assist | Human Responsibility |
|---|---|---|
| Understand the problem | Summarise requirements and stakeholder concerns | Verify accuracy, context, and omissions |
| Define drivers | Suggest quality attributes, conflicts, and questions | Prioritise drivers and define thresholds |
| Explore options | Generate candidate approaches and failure modes | Confirm viability and contextual fit |
| Select architecture | Compare documented criteria and trade-offs | Make the decision and own consequences |
| Validate design | Draft experiment plans and analyse supplied results | Approve methods and judge evidence |
| Record decisions | Draft ADR structure and concise rationale | Confirm the decision and its consequences |
| Review architecture | Check consistency, traceability, and missing concerns | Resolve findings and assess risk |
| Approval | Prepare an approval summary | Approve, reject, condition, or escalate |
| Handover | Summarise constraints, decisions, and open work | Confirm shared understanding and ownership |

AI may assist with:

- Preparing workshop questions and review checklists.
- Drafting diagrams, risk statements, ADRs, and traceability links.
- Checking terminology, metadata, and internal consistency.

AI must not:

- Approve an architecture.
- Accept business, security, privacy, compliance, or operational risk.
- Invent requirements, constraints, evidence, or stakeholder agreement.
- Select technology without verified context.
- Receive confidential data unless its use is authorised.
- Replace threat modelling, benchmarks, prototypes, or qualified review.

Follow the AI Engineering Principles, especially `AP-001` and `AP-004`.

## 18. Common Mistakes

### Starting with Technology

Selecting a platform or pattern before identifying drivers turns preference into architecture.

### Treating Quality Attributes as Slogans

"Scalable" and "secure" do not guide design until expressed as scenarios and measures.

### Designing for Imagined Scale

Speculative distribution increases cost before evidence justifies it.

### Producing Diagrams Without Decisions

A diagram may describe structure while hiding why it exists, what it optimises, and what it sacrifices.

### Ignoring Operations

An architecture that cannot be deployed, observed, recovered, or supported is incomplete.

### Hiding Uncertainty

Unrecorded assumptions later appear as defects, delays, or architectural drift.

### Reviewing Too Late

Late review converts feedback into rework or encourages teams to defend sunk cost.

### Treating Approval as Permanent

Approval reflects a context and evidence set. Change the decision when those conditions change.

## 19. Best Practices

- Start with the problem, drivers, and constraints.
- Use workshops to build shared understanding, then record decisions asynchronously.
- Keep views small and audience-specific.
- Test the riskiest assumption before refining low-risk details.
- Prefer reversible decisions when evidence is weak.
- Separate facts, assumptions, preferences, and constraints.
- Include operations, security, quality, and delivery perspectives early.
- Record why alternatives were rejected.
- Review architecture at meaningful delivery and operational checkpoints.
- Remove obsolete diagrams and supersede outdated decisions.

## 20. Templates

### Architecture Brief

```text
Title:
Owner:
Status:
Business problem:
Desired outcomes:
Scope and boundary:
Stakeholders:
Architectural drivers:
Constraints:
Assumptions:
Current state:
Options:
Selected direction:
Material decisions:
Risks:
Evidence required:
Reviewers and approver:
```

### Architecture Option Record

```text
Decision:
Drivers and criteria:
Option:
Benefits:
Costs:
Risks:
Operational impact:
Security and data impact:
Reversibility:
Evidence:
Recommendation:
```

### Validation Record

```text
Question:
Decision affected:
Success threshold:
Method:
Environment and data:
Result:
Limitations:
Conclusion:
Owner:
Date:
```

Use the approved [ADR template](../../../templates/governance/adr-template.md) for durable decisions.

## 21. Examples

### Example: Choosing an Initial System Style

**Context:** One team is building a business application with moderate load, one deployment cadence, and no requirement for independent component scaling.

**Drivers:** Fast delivery, simple operation, clear domain boundaries, and low support cost.

**Options:** Layered monolith, modular monolith, independently deployed services.

**Decision:** Begin with a modular monolith.

**Reasoning:** It supports explicit boundaries without distributed-system overhead. The team can extract a module later if evidence shows a need for independent scale, ownership, or deployment.

**Review condition:** Reconsider when a module requires independent release, has materially different scaling needs, or is owned by a separate team.

### Example: Validating a Reliability Assumption

**Assumption:** A managed database failover will meet the 15-minute recovery target.

**Validation:** Run a controlled failover in a production-like environment and measure detection, failover, application recovery, and data loss.

**Outcome:** If the threshold fails, change the topology, recovery procedure, or requirement before approval.

## 22. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Architecture Principles](../01-principles/03-architecture-principles.md)
- [Security Principles](../01-principles/06-security-principles.md)
- [Observability Principles](../01-principles/07-observability-principles.md)
- [Performance Principles](../01-principles/08-performance-principles.md)

## 23. Related Standards

- [`PB-AUTHORING`](../03-standards/PB-AUTHORING.md)
- [`DOC-STYLE`](../03-standards/DOC-STYLE.md)
- [`STD-METADATA`](../03-standards/STD-METADATA.md)
- [`STD-REVIEW`](../03-standards/STD-REVIEW.md)
- [`STD-TRACEABILITY`](../03-standards/STD-TRACEABILITY.md)
- [`STD-VERSIONING`](../03-standards/STD-VERSIONING.md)
- [`TERM-STANDARD`](../03-standards/TERM-STANDARD.md)

## 24. Related References

- [`REF-IDENTIFIERS`](../04-reference/REF-IDENTIFIERS.md)
- [`REF-TERMINOLOGY`](../04-reference/REF-TERMINOLOGY.md)
- [`REF-ACRONYMS`](../04-reference/REF-ACRONYMS.md)

## 25. Related Playbooks

- [`PB-REQ`](PB-REQ.md) — Supplies validated requirements and quality attributes.
- [Technical Design Playbook](03-technical-design-playbook.md) — Converts architecture into implementation-ready design.
- [Security Playbook](09-security-playbook.md) — Applies the security workflow to architecture and delivery.
- [Observability Playbook](10-observability-playbook.md) — Defines operational signals and diagnostic capability.
- [Performance Playbook](11-performance-playbook.md) — Validates performance and efficiency.
- [Technical Decision Playbook](15-technical-decision-playbook.md) — Governs broader technical decisions.

Planned playbooks are linked for lifecycle navigation but are not authoritative until drafted and approved.

## 26. Metrics

Use metrics to improve the workflow, not to reward document volume.

| Metric | What It Reveals |
|---|---|
| Decision lead time | Whether material decisions are blocking delivery |
| Reopened decision rate | Whether context, evidence, or review was insufficient |
| Architecture-related rework | Cost caused by missing or weak early decisions |
| Validation pass rate | Quality of assumptions entering validation |
| Escaped architecture risks | Risks discovered only during delivery or operation |
| Review finding closure time | Whether governance actions are being resolved |
| Decision age beyond review condition | Whether architecture records remain current |

Interpret metrics with context. A healthy team may reopen decisions because new evidence emerged, not because the original process failed.

## 27. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.1.0 | 2026-07-30 | Invara Labs Engineering | Draft | Reframed the playbook as a nine-phase architecture standard operating procedure |
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Replaced the planned placeholder with the end-to-end architecture workflow |

## 28. Summary

Architecture work turns requirements and constraints into explicit, evidence-backed decisions that delivery teams can execute.

Start with business outcomes. Prioritise measurable drivers. Compare viable options. Validate the riskiest assumptions. Record trade-offs. Review with the people who must build and operate the system. Continue verifying architecture as delivery and production reveal new evidence.

> **Good architecture is not the most elaborate design. It is the simplest set of decisions that enables the required outcomes, controls the important risks, and can evolve when reality changes.**
