---
title: Change Management Playbook
id: PB-CHANGE-MANAGEMENT
version: 1.0.0
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
  - change-management
  - release
  - governance
  - operations
  - engineering
  - playbook
related:
  - PB-DEPLOYMENT
  - PB-OBSERVABILITY
  - PB-INCIDENT-MANAGEMENT
  - PB-AI-ENGINEERING
  - PB-AUTHORING
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

# Change Management Playbook

> **The standard operating procedure for planning, assessing, approving, implementing, and reviewing engineering changes while minimising operational risk and maintaining service reliability.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. Change Management Workflow
10. Change Lifecycle
11. Detailed Phase Activities
12. Change Management Concepts
13. Change Decision Framework
14. Deliverables
15. Quality Gates
16. Change Checklist
17. AI-Assisted Change Management
18. Change Governance
19. Risk Management
20. Change Classification
21. Change Approval
22. Implementation and Validation
23. Rollback and Recovery
24. Post-Implementation Review
25. Communication and Stakeholder Management
26. Security and Compliance
27. Common Mistakes
28. Best Practices
29. Templates
30. Examples
31. Related Principles
32. Related Standards
33. Related References
34. Related Playbooks
35. Metrics
36. Reference Implementation and Enterprise Appendices
37. Revision History
38. Summary

## 1. Overview

Change Management is the risk-proportionate governance of modifications to managed environments, production services, operational controls, and their supporting technology.

Its purpose is safe change enablement, not paperwork, delay, or a universal approval meeting.

Change Management is not:

- A generic ITIL implementation.
- A substitute for requirements, design, code review, testing, or deployment engineering.
- A requirement that every low-risk automated change receive manual approval.
- A forum for approving work after it has already happened.
- A guarantee that approved changes cannot fail.
- A mechanism for transferring accountability from engineers to a committee.

```text
Engineering Evidence
       │
       ▼
PB-CHANGE-MANAGEMENT
  classify · assess · authorise · coordinate
       │
       ▼
PB-DEPLOYMENT
  implement · verify · recover
       │
       ├──────────────► PB-OBSERVABILITY
       └── if harm ───► PB-INCIDENT-MANAGEMENT
```

Change control should be lightweight for proven, reversible, low-risk work and stronger when impact, uncertainty, irreversibility, security, data, or coordination risk increases.

## 2. Purpose

This playbook enables teams to:

- Define the intended outcome and scope of an operational change.
- Classify changes consistently.
- Assess business, technical, security, data, compliance, and operational risk.
- Match approval and evidence to risk.
- Coordinate schedules, dependencies, conflicts, support, and communication.
- Preserve the identity of approved artefacts and implementation plans.
- Ensure validation, rollback, roll-forward, and recovery are credible.
- Record decisions, execution evidence, outcomes, and exceptions.
- Review failed, emergency, high-risk, and materially surprising changes.
- Improve delivery controls without creating unnecessary bureaucracy.

## 3. Objectives

Following this playbook should produce:

- A complete, uniquely identified Change Record.
- Clear purpose, scope, ownership, affected services, and intended outcome.
- A defensible classification and risk rating.
- Evidence proportionate to impact and uncertainty.
- Appropriate technical, business, security, data, and operational approval.
- Coordinated scheduling and stakeholder readiness.
- A verified implementation and recovery path.
- Objective post-change validation.
- Transparent closure or escalation to Incident Management.
- Learning that improves standard changes, automation, and future risk decisions.

The objective is safe and effective flow, not maximum approval volume or zero emergency changes.

## 4. Scope

### In Scope

- Production application and service releases.
- Infrastructure, platform, network, storage, and cloud changes.
- Database schemas, migrations, data corrections, and retention changes.
- Configuration, feature flags, certificates, secrets references, and policy.
- Security patches, access controls, and compliance controls.
- Dependency, runtime, operating-system, and managed-service upgrades.
- Observability, alerting, routing, and operational tooling changes.
- Emergency fixes, rollbacks, failovers, and recovery changes.
- Material changes to release, support, ownership, or operational process.

### Proportionate Control

| Change Profile | Governance |
|---|---|
| Proven, repeatable, low-risk, automated | Pre-authorised Standard Change with monitored criteria |
| Material but planned and understood | Normal Change with explicit assessment and approval |
| High impact, complex, cross-service, data-sensitive, or difficult to reverse | Enhanced evidence, specialists, rehearsal, progressive execution, higher authority |
| Urgent action to prevent or reduce material harm | Emergency Change with expedited authority and mandatory reconciliation |

### Out of Scope

- Routine development work before it affects a managed environment.
- Architecture and technical-design approval.
- Test execution and code review.
- Active incident command.
- Tool-specific ticket, pipeline, or approval configuration.

An incident-related production action can be both an Incident action and an Emergency Change. The processes coordinate rather than replace one another.

## 5. When to Use This Playbook

Use this playbook whenever a proposed modification can affect:

- Production or shared managed environments.
- Customer, employee, partner, or business workflows.
- Service availability, performance, capacity, resilience, or recovery.
- Data confidentiality, integrity, availability, lifecycle, or residency.
- Security boundaries, identity, access, encryption, audit, or compliance.
- Dependencies, interfaces, schemas, messages, or compatibility.
- Operational ownership, support, alerting, or runbooks.
- Cost, licensing, vendor commitments, or contractual obligations.

Not every change needs the same path. The risk and classification decision determines the required controls.

## 6. Roles and Responsibilities

| Role | Responsibilities | Authority |
|---|---|---|
| Change Owner | Owns purpose, scope, record, evidence, coordination, and outcome | Submits and manages the change |
| Implementer | Executes approved steps and records evidence | Performs assigned implementation |
| Technical Reviewer | Reviews design, dependencies, compatibility, validation, and recovery | Accepts technical scope |
| Service Owner | Owns service outcome, support, and residual operational risk | Accepts service impact |
| Change Authority | Evaluates classification, risk, readiness, and approval | Approves, rejects, conditions, or escalates |
| Release Authority | Authorises production promotion under Deployment | Makes release decision |
| Security or Compliance Reviewer | Reviews sensitive controls and obligations | Accepts assigned specialist scope |
| Data Owner | Reviews migration, integrity, retention, backup, and reconciliation | Accepts assigned data scope |
| Platform or Environment Owner | Reviews capacity, access, infrastructure, and environment readiness | Accepts platform scope |
| Communications Owner | Coordinates stakeholder, support, customer, and maintenance communication | Approves assigned communications |
| Observer or Validator | Independently verifies outcome where risk requires | Accepts validation evidence |

### Accountability Rules

- Every change has one named Change Owner.
- The Change Authority must have competence and authority proportionate to risk.
- Approval is for an exact scope, evidence baseline, plan, window, and conditions.
- Self-approval is limited to formally pre-authorised Standard Changes or explicit policy.
- AI cannot classify final risk, approve a change, accept residual risk, or authorise implementation.

## 7. Inputs

Inputs should include:

- Change objective, business reason, urgency, and expected outcome.
- Affected services, environments, users, data, dependencies, owners, and regions.
- Requirements, architecture, technical design, code review, and test evidence where applicable.
- Release candidate, manifest, configuration, infrastructure, and migration identity.
- Impact, risk, security, privacy, compliance, and operational assessment.
- Implementation sequence, prerequisites, automation, access, and duration.
- Validation, monitoring, success, failure, and stop criteria.
- Rollback, roll-forward, recovery, backup, and reconciliation plans.
- Schedule, maintenance window, conflict analysis, support, and communication.
- Prior incidents, failed changes, known conditions, and related maintenance.

The Change Owner records missing inputs as risk rather than hiding them behind a generic “approved” state.

## 8. Entry Criteria

Before assessment:

- [ ] Change purpose, scope, owner, affected systems, and intended outcome are clear.
- [ ] Candidate, implementation, environment, and dependencies are identifiable.
- [ ] Relevant engineering and test evidence is available.
- [ ] Risk, impact, reversibility, novelty, and urgency can be assessed.
- [ ] Validation and recovery can be described.
- [ ] Required reviewers, authorities, stakeholders, and implementation window are identifiable.
- [ ] Conflicting, dependent, and prerequisite changes are visible.

Incomplete changes are returned as **Not Ready for Assessment** unless an emergency requires an expedited path.

## 9. Change Management Workflow

```text
Change Need
    │
    ▼
1. Identify and Record
    │
    ▼
2. Classify
    │
    ▼
3. Assess Risk and Impact
    │
    ▼
4. Review and Approve
    │
    ▼
5. Schedule and Coordinate
    │
    ▼
6. Implement
    │
    ▼
7. Validate and Observe
    │
    ▼
8. Review Outcome
    │
    ▼
9. Close and Learn
```

Failure or material harm transfers active coordination to `PB-INCIDENT-MANAGEMENT`; the Change Record remains the source of approved intent and execution history.

## 10. Change Lifecycle

| State | Meaning | Exit Condition |
|---|---|---|
| Draft | Need and scope are being defined | Entry criteria satisfied |
| Assessment | Classification, risk, impact, and evidence are reviewed | Approval decision |
| Approved | Exact change is authorised with conditions | Window and readiness confirmed |
| Scheduled | Coordination and implementation time are set | Execution begins |
| Implementing | Approved actions are in progress | Validation or recovery begins |
| Validating | Intended outcome and health are being verified | Success, failure, or incident decision |
| Reviewing | Outcome, surprises, and learning are assessed | Closure requirements met |
| Closed | Record, evidence, communication, and ownership are complete | Reopen only for correction or new evidence |
| Cancelled | Change will not proceed | Rationale and communication recorded |

Approval expires when scope, evidence, risk, timing, or environment changes materially.

## 11. Detailed Phase Activities

### Phase 1: Identify and Record

**Goal:** Create a complete, decision-ready description of the change.

**Activities:**

1. Define objective, reason, urgency, success, and non-goals.
2. Identify affected services, users, data, environments, dependencies, and owners.
3. Link candidate, requirements, design, tests, incidents, maintenance, and prior changes.
4. Describe implementation, validation, rollback, recovery, and communication.
5. Assign Change Owner and preliminary stakeholders.

**Outputs:** Draft Change Record, scope, objective, ownership, and evidence map.

### Phase 2: Classify

**Goal:** Select the governance path appropriate to the change.

**Activities:**

1. Determine whether the change qualifies as Standard, Normal, or Emergency.
2. Evaluate whether it matches an approved Standard Change model exactly.
3. Identify high-risk characteristics requiring enhanced review.
4. Prevent urgency or deadline pressure from being mislabelled as emergency.
5. Record classification rationale and authority.

**Outputs:** Change type, governance path, required evidence, reviewers, and approvals.

### Phase 3: Assess Risk and Impact

**Goal:** Understand credible harm, uncertainty, and recovery difficulty.

**Activities:**

1. Assess user, business, service, security, privacy, data, compliance, financial, and reputational impact.
2. Assess complexity, novelty, change size, dependency reach, coexistence, and environmental differences.
3. Evaluate detectability, blast radius, reversibility, backup, reconciliation, and recovery time.
4. Review timing, support coverage, conflicting changes, vendor risk, and capacity.
5. Rate inherent risk, controls, and residual risk.
6. Define additional evidence or treatment required.

**Outputs:** Risk assessment, impact analysis, control plan, residual risk, and escalation.

### Phase 4: Review and Approve

**Goal:** Make an explicit, evidence-based change decision.

**Activities:**

1. Confirm classification, scope, evidence, risk, implementation, validation, recovery, and communication.
2. Obtain technical, service, security, data, platform, business, or compliance review as required.
3. Resolve missing evidence, conflicts, and unacceptable risk.
4. Record Approve, Approve with Conditions, Reject, Return for Revision, or Escalate.
5. Bind approval to exact scope, candidate, plan, window, conditions, and authority.

**Outputs:** Approval record, conditions, authority, validity period, and readiness decision.

### Phase 5: Schedule and Coordinate

**Goal:** Ensure the organisation and environment are ready at the chosen time.

**Activities:**

1. Select a window using business impact, traffic, support, dependencies, and recovery needs.
2. Check change calendar, freezes, collisions, and dependent sequences.
3. Confirm implementers, validators, observers, decision makers, vendors, and support.
4. Notify stakeholders and publish maintenance or customer communication.
5. Reconfirm candidate, environment, access, backup, observability, and rollback readiness.
6. Conduct go/no-go for material changes.

**Outputs:** Schedule, coordination record, communications, and final readiness.

### Phase 6: Implement

**Goal:** Execute the authorised change through governed Deployment controls.

**Activities:**

1. Confirm exact target, candidate, approval, conditions, and start communication.
2. Follow the approved sequence and `PB-DEPLOYMENT`.
3. Record actors, times, jobs, commands, outputs, versions, and deviations.
4. Monitor implementation and operational signals.
5. Stop when a threshold, unexpected state, loss of observability, or authorisation boundary is breached.
6. Route material deviation for reapproval or emergency authority.

**Outputs:** Execution record, deployed state, deviations, and implementation outcome.

### Phase 7: Validate and Observe

**Goal:** Confirm the objective was achieved without unacceptable impact.

**Activities:**

1. Verify intended state, critical outcomes, data integrity, security, dependencies, and compatibility.
2. Run approved smoke, functional, operational, migration, and reconciliation checks.
3. Observe service, user, business, capacity, and alert signals for the defined window.
4. Compare actual results with success, failure, and stop criteria.
5. Decide Continue, Hold, Rollback, Roll Forward, Recover, or Declare Incident.
6. Record objective evidence and residual risk.

**Outputs:** Validation evidence, observation record, decision, and operational state.

### Phase 8: Review Outcome

**Goal:** Assess whether the change process and result were effective.

**Activities:**

1. Compare objective, plan, risk, duration, result, and user impact.
2. Review deviations, manual interventions, alerts, incidents, rollback, and recovery.
3. Evaluate whether classification and approval were appropriate.
4. Identify inaccurate assumptions, weak controls, and reusable improvements.
5. Determine whether a formal Post-Implementation Review is required.

**Outputs:** Outcome review, learning, improvement actions, and closure recommendation.

### Phase 9: Close and Learn

**Goal:** Complete traceability and return learning to normal engineering governance.

**Activities:**

1. Confirm validation, communication, documentation, inventory, and desired state are complete.
2. Reconcile emergency and manual changes into code and configuration.
3. Link incidents, defects, follow-up work, and maintenance.
4. Update Standard Change models where repeated evidence justifies it.
5. Record outcome, authority, closure time, residual risk, and owners.
6. Archive evidence according to policy.

**Outputs:** Closed Change Record, knowledge updates, governed follow-up, and metrics.

## 12. Change Management Concepts

### Change Enablement

The ability to deliver beneficial change at an acceptable level of risk. Control and flow are complementary when evidence and automation replace unnecessary ceremony.

### Standard Change

A low-risk, well-understood, repeatable change executed through a reviewed and pre-authorised model. It remains monitored and can lose Standard status if outcomes deteriorate.

### Normal Change

A planned change requiring assessment and explicit approval appropriate to its risk.

### Emergency Change

An urgent change necessary to prevent or reduce material harm. It uses expedited, not absent, governance.

### Inherent and Residual Risk

Inherent risk exists before controls. Residual risk remains after testing, automation, progressive delivery, recovery, and other treatment.

### Blast Radius

The credible scope of effect across users, services, regions, tenants, data, dependencies, and operations.

### Change Collision

Two or more changes interact, obscure causality, compete for resources, or make recovery unsafe.

### Separation of Approval and Execution

Approval decides whether the plan and risk are acceptable. Deployment executes the plan. Observability verifies behaviour. Incident Management coordinates adverse impact.

## 13. Change Decision Framework

### Need

- Does the change solve a validated problem or obligation?
- What happens if it is delayed or not performed?
- Is a smaller or safer change available?

### Risk

- What is the worst credible impact?
- How many users, services, data sets, and dependencies are exposed?
- How novel, complex, detectable, reversible, and recoverable is it?
- Which assumptions remain unverified?

### Readiness

- Is the exact candidate tested and reviewed?
- Are environment, access, capacity, support, communication, observability, and recovery ready?

### Decision Outcomes

| Decision | Meaning |
|---|---|
| Approve | Required evidence and controls satisfy authority |
| Approve with Conditions | Explicit conditions, owners, limits, expiry, and monitoring apply |
| Return for Revision | The change may proceed after identified gaps are corrected |
| Reject | Risk, value, timing, or readiness is unacceptable |
| Escalate | A higher or specialist authority must decide |

Approval is not permission to exceed scope or ignore stop conditions.

## 14. Deliverables

| Deliverable | Minimum Content |
|---|---|
| Change Record | ID, objective, owner, scope, type, status, timeline |
| Impact Analysis | Users, services, data, dependencies, operations |
| Risk Assessment | Inherent risk, controls, residual risk, authority |
| Evidence Package | Design, review, testing, candidate, readiness |
| Implementation Plan | Sequence, target, access, duration, ownership |
| Validation Plan | Success, failure, stop, evidence, observation |
| Recovery Plan | Rollback, roll forward, restore, reconciliation |
| Approval Record | Decision, authority, scope, conditions, validity |
| Communication Plan | Audiences, messages, channels, timing, owner |
| Outcome Review | Result, deviations, impact, learning, follow-up |

## 15. Quality Gates

### Gate A: Definition and Classification

- Purpose, scope, owner, affected systems, evidence, and type are clear.

### Gate B: Risk and Readiness

- Impact, risk, security, data, dependencies, timing, validation, observability, and recovery are credible.

### Gate C: Approval and Coordination

- Required authorities approve the exact change.
- Schedule, conflicts, people, environment, access, and communication are ready.

### Gate D: Implementation and Validation

- Execution remains within approved scope.
- Intended outcome, health, integrity, and observation criteria pass.

### Gate E: Review and Closure

- Outcome, deviations, incidents, residual risk, documentation, follow-up, and evidence are complete.

## 16. Change Checklist

### Before Approval

- [ ] Define objective, scope, candidate, impact, owner, and classification.
- [ ] Assess risk, security, data, dependencies, reversibility, and recovery.
- [ ] Provide test, implementation, validation, monitoring, and communication evidence.

### Before Implementation

- [ ] Confirm approval, conditions, window, environment, access, people, and conflicts.
- [ ] Confirm backup, rollback, recovery, observability, stop criteria, and escalation.

### Before Closure

- [ ] Validate outcome and stability.
- [ ] Record deviations, incidents, residual risk, and stakeholder communication.
- [ ] Reconcile desired state, documentation, evidence, follow-up, and ownership.

## 17. AI-Assisted Change Management

All AI-assisted work follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

AI may assist with:

- Summarising scope, evidence, prior incidents, and dependencies.
- Identifying candidate impacts, risks, conflicts, and missing controls.
- Comparing manifests, plans, configurations, and environments.
- Drafting validation, rollback, communication, and review records.
- Analysing change outcomes and recurring failure patterns.

Humans must:

- Protect credentials, source, personal data, client data, security evidence, and environment details.
- Validate every impact, risk, dependency, plan, command, and summary.
- Check for invented evidence and hidden assumptions.
- Prevent autonomous approval or privileged implementation.
- Retain classification, risk, approval, execution, recovery, and closure authority.

AI recommendations are advisory and must not become approval evidence without human validation.

## 18. Change Governance

Governance requires:

- Unique identifiers, ownership, classification, status, and timestamps.
- Traceability from need through evidence, approval, implementation, validation, incident, and closure.
- Risk-proportionate review and separation of duties.
- Approved Standard Change definitions with owners, criteria, controls, and periodic review.
- Explicit handling of conditions, exceptions, freezes, conflicts, and expiry.
- Controlled production access and auditable execution.
- Metrics that improve the system rather than punish change.

### Policy Exceptions

An exception records the control omitted, reason, risk, compensating control, authority, owner, expiry, and follow-up.

### Unauthorised Change

An unauthorised production change is assessed for immediate risk, reconciled into governed state, investigated, and handled according to security, incident, and accountability policy.

## 19. Risk Management

| Risk | Consequence | Control |
|---|---|---|
| Incomplete scope | Hidden impact | Service and dependency mapping |
| Wrong classification | Too little or too much control | Criteria and periodic calibration |
| Weak evidence | Approval rests on assumption | Traceable design, review, and testing |
| Change collision | Failure and unclear causality | Calendar and dependency coordination |
| Environment drift | Unexpected behaviour | Desired-state validation |
| Data irreversibility | Loss or corruption | Migration pattern, backup, reconciliation |
| Missing observability | Harm is not detected | Operational readiness gate |
| Recovery failure | Extended impact | Rehearsal and alternative recovery |
| Approval bottleneck | Unsafe bypass or delivery delay | Risk-tiered authority and pre-authorisation |
| Emergency normalisation | Chronic weak planning | Trend review and corrective action |
| Scope expansion | Unreviewed risk | Stop and reapprove material deviation |
| Premature closure | Hidden impact or debt | Observation, review, and reconciliation |

Risk factors include impact, likelihood, novelty, complexity, exposure, detectability, reversibility, data sensitivity, dependency reach, support readiness, and recovery time.

## 20. Change Classification

### Standard Change

Requirements:

- Documented, repeatable, low-risk procedure.
- Proven success history.
- Bounded scope and environment.
- Automated or strongly controlled execution.
- Defined validation, monitoring, and recovery.
- Pre-authorised owner and review cadence.

### Normal Change

Risk tiers may determine peer, service-owner, specialist, or senior authority approval.

### Emergency Change

Requires:

- Credible urgent harm or obligation.
- Emergency authority.
- Minimum safe evidence and exact scope.
- Verification, monitoring, recovery, and communication.
- Post-implementation review and reconciliation.

Deadline pressure, poor planning, or executive preference alone does not create an emergency.

## 21. Change Approval

Approval considers:

- Value, urgency, and cost of delay.
- Scope, evidence, risk, and residual uncertainty.
- Technical, security, data, compliance, operational, and business readiness.
- Timing, conflicts, support, communication, and maintenance windows.
- Validation, observability, rollback, roll-forward, and recovery.
- Prior failure, incident, or Standard Change performance.

Approval records:

- Exact change and candidate.
- Authority and date.
- Decision and rationale.
- Conditions, limits, expiry, and monitoring.
- Required implementation and validation roles.

A committee is optional. Competent, accountable authority is mandatory.

## 22. Implementation and Validation

Implementation follows [`PB-DEPLOYMENT`](PB-DEPLOYMENT.md) where deployment is involved.

Required controls:

- Confirm target, candidate, approval, conditions, and ownership.
- Execute approved automation and controlled manual steps.
- Record actual actions and deviations.
- Monitor technical, security, data, user, and business signals.
- Stop on breached criteria or loss of evidence.
- Validate intended outcome and absence of unacceptable side effects.
- Preserve traceability between Change and Deployment records.

Material deviation requires pause and reapproval unless emergency authority applies.

## 23. Rollback and Recovery

Every material change defines:

- Rollback, roll-forward, restore, failover, and reconciliation options.
- Trigger thresholds and decision authority.
- Last known-good state and required artefacts.
- Data, schema, message, cache, and external-side-effect treatment.
- Expected recovery time and potential data exposure.
- Verification, communication, and incident escalation.

Rollback is not automatically safest. The approved plan must account for irreversible data and mixed-version states.

Failed recovery or material harm invokes `PB-INCIDENT-MANAGEMENT`.

## 24. Post-Implementation Review

A formal review is required or strongly expected for:

- Failed, rolled-back, recovered, or incident-causing changes.
- Emergency and unauthorised changes.
- High-risk, high-impact, novel, or irreversible changes.
- Changes with significant deviation, surprising outcome, or stakeholder impact.
- Standard Changes whose failure or drift suggests reclassification.

Review:

- Did the change achieve its objective?
- Was classification and risk accurate?
- Did evidence, approval, timing, communication, implementation, validation, and recovery work?
- What changed unexpectedly?
- What should become automated, standardised, prevented, or monitored?

## 25. Communication and Stakeholder Management

The communication plan defines:

- Affected users, customers, support, service owners, vendors, executives, and specialists.
- Planned window, expected impact, action required, workaround, and contact.
- Start, progress, delay, failure, recovery, and completion messages.
- Communication owner, approver, channel, language, and timing.
- Sensitive, security, contractual, or regulatory restrictions.

Messages should state facts, expected impact, current status, and next update. Avoid technical detail that does not help the audience act.

## 26. Security and Compliance

Changes must:

- Use authorised, least-privilege, time-bounded access.
- Protect credentials and use approved secret stores.
- Preserve artefact integrity, provenance, signatures, and dependency controls where required.
- Assess data classification, privacy, residency, retention, encryption, and audit.
- Include required security, privacy, legal, compliance, and segregation-of-duty review.
- Preserve evidence of approvals and privileged actions.
- Coordinate vulnerability, breach, or regulatory urgency through specialist authority.
- Revoke temporary access and reconcile emergency changes.

An approved change is not exempt from security or legal obligations.

## 27. Common Mistakes

- Treating Change Management as ticket completion.
- Applying one approval path to every risk level.
- Labelling unplanned work as an emergency to bypass controls.
- Approving vague scope or mutable artefacts.
- Reviewing deployment mechanics but not user, data, or dependency impact.
- Scheduling conflicting high-risk changes.
- Assuming test success proves environment readiness.
- Declaring rollback without analysing data and compatibility.
- Allowing approval to survive material scope changes.
- Closing before validation and observation finish.
- Failing to reconcile manual or emergency changes into desired state.
- Measuring change volume without reliability outcomes.
- Using AI-generated risk lists as validated assessment.

## 28. Best Practices

- Keep changes small, focused, compatible, observable, and reversible.
- Replace repeated manual approval with proven automation and Standard Change models.
- Assess cost of delay alongside operational risk.
- Build once and preserve exact candidate identity.
- Use progressive delivery to reduce exposure.
- Define success, failure, stop, and recovery before implementation.
- Coordinate dependencies and avoid unnecessary change collisions.
- Rehearse high-risk migrations and recovery.
- Make approval evidence concise, linked, and decision-ready.
- Review failures and surprises without blame.
- Revoke Standard status when evidence no longer supports it.
- Improve controls at the shared system level.

## 29. Templates

### Change Request

```markdown
# Change <ID>: <Title>

## Objective and Business Reason
## Scope and Affected Services
## Change Type and Urgency
## Candidate and Evidence
## Impact and Risk
## Implementation and Validation
## Rollback, Recovery, and Reconciliation
## Schedule, Roles, and Communication
## Approval and Conditions
## Outcome and Closure
```

### Approval Record

```markdown
**Change and candidate:**
**Classification and risk:**
**Evidence reviewed:**
**Decision:** Approve / Conditional / Revise / Reject / Escalate
**Conditions and expiry:**
**Authority and date:**
```

### Post-Implementation Review

```markdown
## Objective and Outcome
## Timeline and Evidence
## Deviations and Impact
## Classification and Risk Accuracy
## Validation and Recovery
## Lessons and Actions
```

## 30. Examples

### Example: Standard Change

A certificate rotation uses an automated, tested procedure with bounded targets, prechecks, progressive execution, verification, expiry alerting, and rollback.

After a sustained success history, the model is pre-authorised. Each execution remains identified, monitored, and auditable.

### Example: Normal Database Change

A schema change uses expand-migrate-contract, compatibility tests, representative rehearsal, backup, integrity checks, progressive migration, and a roll-forward recovery plan.

Data, service, and Release authorities approve the exact sequence and observation window.

### Example: Emergency Change

A critical exposure requires disabling a vulnerable feature. Emergency authority approves the smallest effective flag change with verification, monitoring, rollback, restricted communication, and later reconciliation.

The urgency reduces lead time; it does not remove evidence or accountability.

### Example: Reapproval

A planned low-risk configuration change unexpectedly requires a database migration.

The Change Owner pauses. Because impact, evidence, recovery, and authority changed materially, the original approval no longer applies.

## 31. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Architecture Principles](../01-principles/03-architecture-principles.md)
- [Security Principles](../01-principles/06-security-principles.md)
- [Observability Principles](../01-principles/07-observability-principles.md)
- [Performance Principles](../01-principles/08-performance-principles.md)

## 32. Related Standards

- [Playbook Authoring Standard](../03-standards/PB-AUTHORING.md)
- [Engineering Traceability Standard](../03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](../03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](../03-standards/STD-VERSIONING.md)
- [Engineering Terminology Standard](../03-standards/TERM-STANDARD.md)
- [Documentation Style Guide](../03-standards/DOC-STYLE.md)
- Change, risk, security, communication, and operational standards are planned and non-authoritative.

## 33. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)
- Change-type, risk-matrix, approval, rollback, and change-calendar references are planned and non-authoritative.

## 34. Related Playbooks

- [Deployment Playbook](PB-DEPLOYMENT.md) executes approved production promotion.
- [Observability Playbook](PB-OBSERVABILITY.md) supplies validation and operational evidence.
- [Incident Management Playbook](PB-INCIDENT-MANAGEMENT.md) governs harmful or failed changes requiring coordinated response.
- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted change work.
- [Testing Playbook](PB-TESTING.md) supplies verification evidence.
- [Architecture Playbook](PB-ARCH.md) and [Technical Design Playbook](PB-TECH-DESIGN.md) supply approved intent.
- Maintenance is planned as the final core playbook and will generate preventive, adaptive, corrective, and lifecycle changes.

## 35. Metrics

Use metrics to improve safe flow, not reward bypass or punish teams that report failure.

| Metric | What It Reveals | Guardrail |
|---|---|---|
| Change lead time | Assessment-to-value flow | Segment waiting, execution, and observation |
| Change success rate | Outcomes meeting closure criteria | Define conditional and partial success |
| Change failure rate | Changes causing rollback, recovery, degradation, or incident | Segment impact and cause |
| Emergency change rate | Planning, vulnerability, and operational pressure | Some emergencies are legitimate |
| Standard Change adoption | Proven automation and pre-authorisation | Do not force unsuitable work into Standard |
| Approval turnaround | Governance responsiveness | Pair with decision quality |
| Reapproval rate | Scope and readiness quality | Reapproval can be correct control |
| Rollback and recovery rate | Change risk and control effectiveness | Successful rollback limits harm |
| Time to validate | Evidence speed | Do not shorten required observation |
| Post-Implementation Review completion | Learning flow | Measure action effectiveness too |
| Change collision rate | Coordination quality | Define material interaction |
| Unauthorised change rate | Governance and access weakness | Encourage transparent reporting |

## 36. Reference Implementation and Enterprise Appendices

`PB-CHANGE-MANAGEMENT` is the reference implementation for safe-change-enablement playbooks.

### 36.1 Change Request Template

- Identifier, title, owner, status, urgency.
- Objective, scope, affected services, users, data, dependencies.
- Type, risk, candidate, evidence, implementation, validation.
- Recovery, schedule, communication, approval, outcome.

### 36.2 Change Readiness Checklist

- [ ] Scope, candidate, ownership, evidence, and dependencies are complete.
- [ ] Classification and risk are defensible.
- [ ] Environment, people, access, schedule, and communication are ready.
- [ ] Validation, observability, stop, rollback, and recovery are credible.

### 36.3 Risk Assessment Matrix

| Impact / Likelihood | Low | Medium | High |
|---|---|---|---|
| Low impact | Low | Low/Medium | Medium |
| Medium impact | Low/Medium | Medium | High |
| High impact | Medium | High | Critical |

Increase control for low detectability, irreversibility, sensitive data, wide dependencies, or weak recovery.

### 36.4 Approval Matrix

| Risk | Minimum Authority |
|---|---|
| Low Standard | Pre-authorised model owner |
| Low/Medium Normal | Qualified peer and Service Owner as policy requires |
| High | Service, technical, operational, and required specialists |
| Critical | Senior Change/Release Authority and specialist/business authority |
| Emergency | Designated Emergency Change Authority |

### 36.5 Rollback Checklist

- [ ] Trigger, authority, last known-good state, and artefacts are defined.
- [ ] Data, schema, messages, caches, and side effects are addressed.
- [ ] Access, automation, support, communication, and verification are ready.
- [ ] Alternative roll-forward or recovery exists when rollback is unsafe.

### 36.6 Validation Checklist

- [ ] Intended state and objective are achieved.
- [ ] Critical user, service, security, data, and dependency outcomes pass.
- [ ] Observability and alerting remain healthy.
- [ ] Required observation window passes.
- [ ] Residual risk and conditions have owners.

### 36.7 Communication Template

```markdown
**Change and window:**
**Affected audience and expected impact:**
**Action or workaround:**
**Current status:**
**Owner/contact:**
**Next update or completion:**
```

### 36.8 Change Maturity Model

| Level | Characteristics |
|---|---|
| 1. Reactive | Untracked changes, manual approvals, unclear ownership |
| 2. Repeatable | Records, basic risk, schedules, rollback, and evidence |
| 3. Governed | Classification, tiered authority, traceability, PIR, compliance |
| 4. Enabled | Automated evidence, Standard Changes, progressive delivery, fast recovery |
| 5. Adaptive | Operational learning continuously improves safe flow and controls |

### 36.9 Change Classification Matrix

| Characteristic | Standard | Normal | Emergency |
|---|---|---|---|
| Urgency | Planned | Planned | Immediate material harm |
| Procedure | Proven and fixed | Change-specific | Minimum safe |
| Risk | Low and bounded | Any assessed tier | Accepted urgent residual risk |
| Approval | Pre-authorised | Explicit authority | Emergency authority |
| Review | Periodic model review | Risk-based | Mandatory reconciliation/PIR |

### 36.10 Deliverables Checklist

- [ ] Change Record, impact, risk, evidence, implementation, and validation.
- [ ] Recovery, schedule, communication, approval, and execution evidence.
- [ ] Outcome review, incidents, follow-up, desired-state reconciliation, and closure.

### 36.11 Post-Implementation Review Template

- Objective and result.
- Planned versus actual timeline.
- User, service, data, security, and business impact.
- Deviations, incidents, rollback, and recovery.
- Classification, risk, approval, and control effectiveness.
- Learning, actions, owners, and evidence.

### 36.12 Change Closure Checklist

- [ ] Intended outcome and stability are verified.
- [ ] Stakeholders receive completion or failure communication.
- [ ] Incidents, defects, residual risks, and actions are linked.
- [ ] Documentation, inventory, configuration, and desired state are reconciled.
- [ ] Required PIR and emergency review are complete or governed.
- [ ] Evidence, closure authority, and time are recorded.

## 37. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Change Management Playbook with nine-phase safe-change workflow, classification, approval, risk, recovery, communication, security, five quality gates, metrics, and twelve enterprise appendices |

## 38. Summary

`PB-CHANGE-MANAGEMENT` governs safe enablement of changes to managed environments and production systems.

It requires teams to:

- Define and identify each change.
- Classify and assess it according to risk and impact.
- Match evidence and approval to uncertainty.
- Coordinate timing, people, dependencies, and communication.
- Execute through governed Deployment controls.
- Validate outcomes and invoke Incident Management when harm occurs.
- Review surprises, reconcile state, and improve future controls.

Good Change Management makes low-risk change easier and high-risk change safer. It creates accountable flow, not ceremony.
