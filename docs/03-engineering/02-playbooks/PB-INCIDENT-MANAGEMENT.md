---
title: Incident Management Playbook
id: PB-INCIDENT-MANAGEMENT
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
  - incident
  - operations
  - sre
  - reliability
  - engineering
  - playbook
related:
  - PB-OBSERVABILITY
  - PB-DEPLOYMENT
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

# Incident Management Playbook

> **The standard operating procedure for detecting, assessing, responding to, resolving, communicating, and learning from production incidents while minimising customer impact and improving operational resilience.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. Incident Management Workflow
10. Incident Lifecycle
11. Detailed Phase Activities
12. Incident Management Concepts
13. Incident Decision Framework
14. Deliverables
15. Quality Gates
16. Incident Response Checklist
17. AI-Assisted Incident Management
18. Incident Governance
19. Risk Management
20. Incident Classification and Prioritisation
21. Communication and Escalation
22. Root Cause Analysis
23. Corrective and Preventive Actions
24. Post-Incident Review
25. Knowledge Management
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

An incident is an unplanned event that degrades or threatens a production service, user outcome, security property, data integrity, or operational objective and requires coordinated response.

Incident Management prioritises:

1. Protect people, users, data, and trust.
2. Reduce active impact.
3. Restore a safe and stable service.
4. Communicate facts and uncertainty.
5. Preserve evidence.
6. Learn and improve without blame.

It is not:

- A generic IT service-desk process.
- The same as diagnosing a normal defect.
- A forum for architecture redesign during active impact.
- A reason to bypass security, evidence, or authorisation without recording it.
- Complete as soon as a dashboard turns green.
- A mechanism for assigning personal blame.

```text
PB-OBSERVABILITY
       │ detects and informs
       ▼
PB-INCIDENT-MANAGEMENT
       │ coordinates response and learning
       ▼
Change and Maintenance Improvement
```

## 2. Purpose

This playbook enables teams to:

- Detect and validate incidents quickly.
- Classify impact and urgency consistently.
- Establish clear command, roles, channels, and decision authority.
- Contain harm and restore service safely.
- Coordinate technical, product, security, support, legal, and communication work.
- Maintain accurate stakeholder and customer communication.
- Preserve a trustworthy timeline and evidence.
- Separate mitigation from root-cause analysis.
- Identify systemic causes and contributing conditions.
- Track corrective and preventive actions to verified completion.
- Turn every significant incident into organisational learning.

## 3. Objectives

Following this playbook should produce:

- A timely incident declaration and severity.
- A named Incident Commander and response structure.
- A shared incident record, timeline, communication channel, and current status.
- Controlled containment, mitigation, recovery, and verification.
- Clear internal and external communication.
- Preserved technical and decision evidence.
- An evidence-based root-cause analysis where required.
- Prioritised corrective and preventive actions with owners.
- A reviewed post-incident record and reusable knowledge.

The objective is safe restoration and learning, not the fastest possible closure metric or proving a single root cause.

## 4. Scope

### In Scope

- Service outages and severe degradation.
- Failed or harmful deployments.
- Data loss, corruption, duplication, delay, or integrity risk.
- Security or privacy events requiring engineering response.
- Infrastructure, platform, network, database, and dependency failures.
- Capacity exhaustion, runaway cost, queue backlog, and resource saturation.
- Incorrect business behaviour with material user impact.
- Monitoring, alerting, certificate, scheduled-job, and automation failures.
- Near misses that reveal credible high-impact risk.

### Proportionate Response

| Event Profile | Expected Response |
|---|---|
| Low, contained operational issue | Named owner, tracked restoration, concise record |
| Material user or service impact | Incident Commander, dedicated channel, severity, regular updates |
| Critical, widespread, security, safety, or data impact | Full command structure, executive and specialist escalation, formal communications |
| Near miss | Evidence capture, risk assessment, learning and preventive action without artificial emergency |

### Out of Scope

- Planned maintenance and approved deployment without adverse impact.
- Normal feature work and routine defect handling.
- Vendor-specific incident tooling.
- Complete forensic, legal, regulatory, or law-enforcement procedure.
- Long-term implementation of improvement work.

Security, privacy, safety, and regulatory events may invoke parallel specialist processes. This playbook coordinates the engineering response without replacing those authorities.

## 5. When to Use This Playbook

Declare or consider an incident when:

- Users cannot complete a critical journey.
- Availability, latency, error, integrity, or security objectives are materially breached.
- Impact crosses teams, services, regions, tenants, or dependencies.
- Coordination and communication exceed normal operational work.
- Immediate action is required to prevent worsening harm.
- A deployment or change must be stopped, rolled back, or recovered.
- Evidence suggests unauthorised access, data exposure, corruption, or loss.
- The situation is uncertain but the credible impact is high.

When uncertain, favour early declaration. An incident can be downgraded or closed; delayed coordination cannot recover lost time.

## 6. Roles and Responsibilities

| Role | Responsibilities | Authority |
|---|---|---|
| Incident Commander | Owns objectives, roles, priorities, decisions, cadence, escalation, and closure | Directs incident response |
| Technical Lead | Coordinates investigation, hypotheses, mitigation, recovery, and verification | Recommends technical actions |
| Operations Lead | Executes platform, deployment, failover, rollback, and recovery actions | Controls assigned operational actions |
| Communications Lead | Maintains internal, customer, executive, and support updates | Publishes approved status |
| Scribe | Records timeline, facts, decisions, actions, owners, and evidence | Maintains incident record |
| Service Owner | Supplies service context, accepts restored operation and residual risk | Confirms service ownership |
| On-Call Responder | Validates detection, begins triage, and escalates | Declares within assigned authority |
| Security or Privacy Lead | Owns security containment, evidence, disclosure, and specialist obligations | Directs assigned security scope |
| Product or Business Lead | Clarifies customer and business impact and priorities | Confirms business impact |
| Support or Customer Lead | Supplies reports and coordinates customer handling | Manages assigned customer channel |
| Executive Sponsor | Removes organisational blockers and accepts exceptional business risk | Owns executive decisions |

### Role Rules

- The Incident Commander coordinates; they should not be the primary investigator during material incidents.
- One person may hold multiple roles only when incident size permits.
- Handoffs require explicit acknowledgement and current-state transfer.
- Responders work from shared objectives and recorded assignments.
- AI cannot be Incident Commander, declare recovery, approve risky action, or own communication.

## 7. Inputs

Inputs may include:

- Alerts, user reports, support cases, synthetic checks, and anomaly detection.
- Logs, metrics, traces, events, health, profiles, and audit records.
- Service ownership, architecture, dependencies, data flows, and critical journeys.
- SLOs, severity criteria, runbooks, recovery objectives, and escalation paths.
- Deployment, configuration, feature-flag, infrastructure, and change history.
- Recent code, dependency, certificate, capacity, and vendor changes.
- Known issues, defects, maintenance, and prior incidents.
- Customer, contractual, regulatory, privacy, and security obligations.

Do not delay declaration while waiting for perfect inputs. Record uncertainty and improve evidence as response proceeds.

## 8. Entry Criteria

Incident response begins when:

- [ ] A credible adverse event or high-impact threat is detected.
- [ ] Initial scope, affected outcome, and evidence are recorded.
- [ ] A preliminary severity and owner are assigned.
- [ ] An incident record and shared response channel exist.
- [ ] Required responders and specialists are notified.
- [ ] Immediate safety, security, data, and containment needs are assessed.
- [ ] Next update time is set.

Missing information is not a reason to delay declaration when credible impact exists.

## 9. Incident Management Workflow

```text
Incident Detected
       │
       ▼
1. Detect and Validate
       │
       ▼
2. Assess Severity
       │
       ▼
3. Declare and Mobilise
       │
       ▼
4. Contain Impact
       │
       ▼
5. Investigate
       │
       ▼
6. Restore Service
       │
       ▼
7. Verify Stability
       │
       ▼
8. Analyse Causes
       │
       ▼
9. Define and Track CAPA
       │
       ▼
10. Review, Learn, and Close
```

Containment, investigation, communication, and recovery often proceed in parallel under one command structure.

## 10. Incident Lifecycle

| State | Meaning | Exit Condition |
|---|---|---|
| Detected | A credible adverse signal exists | Validated or dismissed |
| Declared | Coordinated response is active | Impact contained or response cancelled |
| Contained | Harm is limited but service may remain degraded | Restoration action succeeds |
| Mitigated | User impact is materially reduced | Stable service and integrity are verified |
| Monitoring | Recovery is observed for recurrence or delayed impact | Stability window passes |
| Resolved | Active incident response is no longer required | Learning and follow-up remain |
| Reviewed | Causes, response, and actions are reviewed | Required CAPA is governed |
| Closed | Records, communication, ownership, and required gates are complete | Reopen only on new evidence |

Resolution and closure are different. Service restoration can precede full analysis and action completion.

## 11. Detailed Phase Activities

### Phase 1: Detect and Validate

**Goal:** Establish whether a credible incident exists and begin safe action.

**Activities:**

1. Acknowledge the alert or report.
2. Verify signal freshness, scope, environment, and obvious telemetry failure.
3. Identify affected user outcome, service, region, tenant, data, or dependency.
4. Capture initial time, evidence, reporter, and recent change.
5. Begin immediate protection when delay creates harm.
6. Escalate uncertainty with high credible impact.

**Outputs:** Validated event, initial record, owner, and assessment request.

### Phase 2: Assess Severity

**Goal:** Match response urgency and structure to current impact and risk.

**Activities:**

1. Assess safety, security, privacy, data, availability, business, customer, and reputational impact.
2. Estimate scope, duration, trajectory, detectability, and workaround.
3. Determine contractual, regulatory, executive, or customer notification needs.
4. Assign preliminary severity and response targets.
5. Reassess severity as evidence changes.

**Outputs:** Severity, rationale, affected scope, escalation, and update cadence.

### Phase 3: Declare and Mobilise

**Goal:** Establish command, coordination, communication, and shared situational awareness.

**Activities:**

1. Declare the incident and assign Incident Commander.
2. Assign Technical, Operations, Communications, Scribe, and specialist roles.
3. Create incident channel, bridge, record, timeline, and action board.
4. State current impact, severity, known facts, uncertainty, objectives, and next update.
5. Notify required responders, owners, support, executives, vendors, and specialists.
6. Stop or coordinate conflicting production changes.

**Outputs:** Declaration, command structure, response workspace, notifications, and objectives.

### Phase 4: Contain Impact

**Goal:** Prevent further user, data, security, or service harm.

**Activities:**

1. Limit traffic, disable a feature, isolate a component, revoke access, or stop a harmful process.
2. Preserve evidence before destructive action where safe.
3. Protect data integrity and prevent repeated side effects.
4. Apply a known-safe workaround when available.
5. Evaluate containment side effects and downstream impact.
6. Record authority, action, time, outcome, and reversibility.

**Outputs:** Containment state, reduced blast radius, evidence, and updated risk.

### Phase 5: Investigate

**Goal:** Generate enough evidence to choose the safest restoration action.

**Activities:**

1. Build a precise timeline of symptoms, changes, and system behaviour.
2. Compare healthy and unhealthy cohorts, versions, regions, and dependencies.
3. Correlate logs, metrics, traces, events, deployments, configuration, and audit activity.
4. Form explicit hypotheses with confirming and disconfirming tests.
5. Assign investigations to avoid duplicated or conflicting work.
6. Use the Debugging Playbook for focused technical diagnosis where appropriate.
7. Separate facts, hypotheses, decisions, and unknowns.

**Outputs:** Investigation evidence, tested hypotheses, affected scope, and mitigation options.

### Phase 6: Restore Service

**Goal:** Restore a safe user outcome with minimum additional risk.

**Activities:**

1. Compare rollback, roll forward, failover, restore, restart, scale, configuration, and traffic options.
2. Select action using impact, reversibility, evidence, time, data risk, and authority.
3. Define expected result, stop condition, verification, owner, and fallback.
4. Execute through controlled access and recorded steps.
5. Communicate material action before and after execution.
6. Escalate failed or worsening recovery immediately.

**Outputs:** Mitigation or recovery action, evidence, impact change, and next decision.

### Phase 7: Verify Stability

**Goal:** Confirm that recovery is real, complete enough, and durable.

**Activities:**

1. Verify critical user journeys, data integrity, security, dependencies, queues, and side effects.
2. Compare service and business signals with known-good baselines.
3. Confirm alerts, support reports, and affected cohorts recover.
4. Reconcile delayed, duplicated, lost, or corrupted work.
5. Observe for the defined stability window.
6. Record residual degradation, workaround, and ownership.
7. Obtain Service Owner and Incident Commander resolution decision.

**Outputs:** Stability evidence, resolved or ongoing status, residual risk, and final active-response communication.

### Phase 8: Analyse Causes

**Goal:** Explain how the incident occurred and why safeguards did not prevent or limit it.

**Activities:**

1. Preserve the factual timeline and evidence.
2. Identify triggering event, direct causes, contributing conditions, and latent systemic factors.
3. Analyse detection, escalation, decision, communication, containment, and recovery.
4. Examine organisational, process, design, test, change, dependency, and observability conditions.
5. Validate claims against evidence and record uncertainty.
6. Avoid blame and hindsight simplification.

**Outputs:** Root Cause Analysis, causal model, contributing factors, and lessons.

### Phase 9: Define and Track CAPA

**Goal:** Reduce recurrence and improve detection, containment, recovery, and resilience.

**Activities:**

1. Convert findings into corrective and preventive actions.
2. Prioritise by expected risk reduction, urgency, scope, and feasibility.
3. Assign owner, due date, acceptance evidence, dependency, and tracking location.
4. Include code, design, tests, observability, runbooks, training, platform, vendor, and process changes.
5. Avoid action lists consisting only of reminders or retraining.
6. Verify effectiveness after implementation.

**Outputs:** CAPA plan, owners, priorities, evidence criteria, and governance route.

### Phase 10: Review, Learn, and Close

**Goal:** Complete accountability, share learning, and close the incident record.

**Activities:**

1. Conduct a blameless post-incident review for qualifying incidents.
2. Agree facts, causes, response strengths, gaps, and actions.
3. Publish an audience-appropriate postmortem.
4. Update runbooks, known issues, architecture, tests, dashboards, alerts, and training.
5. Confirm communications, evidence, retention, and regulatory obligations.
6. Transfer CAPA to normal work governance.
7. Close only after required gates and ownership are complete.

**Outputs:** Reviewed postmortem, knowledge updates, governed CAPA, closure decision, and archived record.

## 12. Incident Management Concepts

### Event, Alert, Incident, and Problem

- **Event:** An observed state change.
- **Alert:** A notification that defined action may be required.
- **Incident:** A production event requiring coordinated response.
- **Problem:** An underlying or recurring condition requiring longer-term management.

### Impact, Urgency, and Severity

Impact describes harm and scope. Urgency describes how quickly action is required. Severity selects the response level from both.

### Containment, Mitigation, Recovery, and Resolution

- **Containment:** Limits further harm.
- **Mitigation:** Reduces active impact.
- **Recovery:** Restores service or data.
- **Resolution:** Ends active coordinated response after stability is verified.

### Incident Command

Incident command creates one coordinating authority, clear roles, shared objectives, controlled decisions, and predictable communication.

### Blamelessness

Blameless learning examines why actions made sense with the information, incentives, tools, and constraints present at the time. It does not remove accountability for deliberate misconduct.

### Root Cause

Complex incidents rarely have one root cause. Useful analysis models triggering events, direct technical causes, contributing conditions, and systemic safeguards.

### Near Miss

A near miss caused little or no impact because of chance or a late control but reveals credible future harm.

## 13. Incident Decision Framework

### Declare

Declare when coordinated response is likely to reduce credible impact or uncertainty. Do not wait for complete diagnosis.

### Severity

Use current impact, not anticipated embarrassment. Reclassify as facts change.

### Mitigation Choice

| Question | Consideration |
|---|---|
| Will it reduce active harm? | Prioritise user and data outcomes |
| Is it reversible? | Prefer controlled, observable actions |
| What evidence supports it? | Separate fact from hypothesis |
| What can it worsen? | Model dependencies and side effects |
| How will success be verified? | Define thresholds before action |
| Who authorises it? | Use incident and specialist authority |

### Communicate

Communicate when stakeholders need information to act, support users, meet obligations, or maintain trust. State facts, impact, action, uncertainty, and next update.

### Resolve

Resolve active response only when service and data stability are verified, monitoring is effective, residual risk has an owner, and required communication is complete.

## 14. Deliverables

| Deliverable | Minimum Content |
|---|---|
| Incident Record | Identifier, severity, impact, owners, status, channels |
| Timeline | Signals, decisions, actions, communications, and evidence |
| Situation Report | Facts, impact, unknowns, objectives, action, next update |
| Communications Log | Audience, content, approver, channel, and time |
| Recovery Record | Action, authority, result, verification, and data disposition |
| Incident Report | Scope, duration, impact, response, outcome, and residual risk |
| Root Cause Analysis | Causal evidence, contributors, safeguards, uncertainty |
| CAPA Plan | Action, rationale, priority, owner, due date, acceptance evidence |
| Postmortem | Timeline, causes, response review, lessons, and actions |
| Knowledge Updates | Runbooks, known issues, dashboards, alerts, tests, architecture |

## 15. Quality Gates

### Gate A: Declaration and Command

- Incident, severity, impact, Incident Commander, roles, record, channel, and cadence exist.

### Gate B: Impact Control

- Immediate safety, security, privacy, data, and service harm is assessed.
- Containment and recovery decisions are authorised and recorded.

### Gate C: Stable Resolution

- Critical outcomes, integrity, dependencies, and affected cohorts are verified.
- Stability window passes and residual risk has ownership.

### Gate D: Evidence and Learning

- Timeline, communications, causal analysis, response review, and uncertainty are complete.

### Gate E: Governed Closure

- CAPA has priority, owners, dates, and acceptance evidence.
- Required communications, knowledge, retention, and approvals are complete.

## 16. Incident Response Checklist

### First Response

- [ ] Validate signal and record initial impact.
- [ ] Assign severity, Incident Commander, roles, channel, and next update.
- [ ] Protect people, users, data, security, and evidence.
- [ ] Stop conflicting or harmful changes.

### Active Response

- [ ] Maintain facts, unknowns, objectives, timeline, actions, and owners.
- [ ] Contain impact before pursuing perfect diagnosis.
- [ ] Define expected result and fallback for each risky action.
- [ ] Communicate at agreed cadence.

### Resolution and Learning

- [ ] Verify service, data, users, dependencies, and stability window.
- [ ] Record residual risk and operational owner.
- [ ] Complete RCA, CAPA, postmortem, knowledge, and required notices.
- [ ] Close through explicit authority.

## 17. AI-Assisted Incident Management

All AI-assisted work follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

AI may assist with:

- Summarising telemetry and incident channels.
- Correlating alerts, deployments, changes, and affected cohorts.
- Drafting timelines, situation reports, and communications.
- Suggesting hypotheses, queries, and possible mitigations.
- Clustering prior incidents and known issues.
- Reviewing causal analysis and action coverage.

Humans must:

- Protect credentials, personal data, client data, security evidence, and confidential communication.
- Verify every fact, timeline entry, hypothesis, query, action, and draft.
- Label probabilistic suggestions and uncertainty.
- Prevent autonomous privileged remediation without approved safety control.
- Retain severity, declaration, mitigation, communication, recovery, risk, and closure authority.

AI output is supporting analysis, not incident evidence until validated.

## 18. Incident Governance

Governance requires:

- Unique incident identity, timestamped record, severity, ownership, and status.
- Defined command roles, handoff, escalation, and decision authority.
- Traceability across signals, changes, actions, communications, evidence, causes, and CAPA.
- Controlled production access and recorded emergency actions.
- Evidence preservation, integrity, classification, access, and retention.
- Required security, legal, privacy, regulatory, contractual, and customer coordination.
- Blameless review with accountable action ownership.
- Periodic trend, recurrence, and CAPA review.

An emergency can justify an expedited control, not an invisible action. Record what occurred and reconcile temporary changes into governed state.

## 19. Risk Management

| Risk | Consequence | Control |
|---|---|---|
| Delayed declaration | Impact grows without coordination | Low declaration threshold |
| Wrong severity | Resources or communication mismatch | Evidence-based reassessment |
| Unclear command | Conflicting actions and delay | One Incident Commander |
| Tunnel vision | Plausible causes are missed | Explicit hypotheses and disconfirmation |
| Risky mitigation | Incident worsens | Expected result, stop, fallback, authority |
| Evidence loss | Causes and obligations cannot be established | Early preservation and controlled action |
| Poor communication | Confusion and loss of trust | Cadence, audience, approver, facts |
| Premature resolution | Recurrence or hidden integrity damage | Stability and reconciliation criteria |
| Single-cause RCA | Systemic conditions persist | Causal and safeguard analysis |
| Weak CAPA | Recurrence remains likely | Risk-reduction priority and evidence |
| Responder fatigue | Error and health impact | Rotations, handoffs, relief, humane cadence |
| Security disclosure | Additional harm | Need-to-know channels and specialist lead |

## 20. Incident Classification and Prioritisation

### Severity Model

| Severity | Typical Impact | Response |
|---|---|---|
| SEV-1 Critical | Catastrophic or widespread outage; severe safety, security, privacy, or data impact | Immediate full command, executive and specialist escalation |
| SEV-2 High | Major customer or service impact with urgent coordination | Immediate command and frequent updates |
| SEV-3 Medium | Contained material degradation with workaround | Coordinated owner response |
| SEV-4 Low | Limited operational impact without urgent coordination | Normal tracked handling |

Organisation-specific thresholds remain subject to a future approved severity reference.

### Classification Dimensions

- Service availability and performance.
- Customer, tenant, region, and transaction scope.
- Data confidentiality, integrity, and availability.
- Security, safety, regulatory, and contractual exposure.
- Financial, reputational, support, and dependency impact.
- Workaround, trajectory, and recovery difficulty.

Severity does not measure individual performance or team importance.

## 21. Communication and Escalation

Every update should state:

- Incident identifier, status, severity, and start time.
- Confirmed impact and affected scope.
- Known facts and important uncertainty.
- Current mitigation and recovery activity.
- Workaround where appropriate.
- Next update time.

### Communication Audiences

| Audience | Need |
|---|---|
| Responders | Current facts, objectives, assignments, decisions |
| Support | User impact, workaround, approved language |
| Customers | Impact, action, service expectation, next update |
| Executives | Business impact, risk, decisions, assistance needed |
| Security/Legal/Privacy | Evidence and obligation-specific detail |
| Vendors/Partners | Dependency impact and coordinated action |

Do not speculate, assign blame, expose sensitive detail, or promise resolution times without evidence.

Escalation may be technical, organisational, executive, vendor, security, legal, privacy, or regulatory.

## 22. Root Cause Analysis

RCA begins after service is safe enough for deliberate analysis.

It should:

- Define impact and the actual sequence of events.
- Distinguish trigger, direct cause, contributing factors, and latent conditions.
- Explain why safeguards, tests, reviews, deployment controls, monitoring, and recovery did or did not work.
- Evaluate decisions using information available at the time.
- Support claims with evidence and name uncertainty.
- Identify conditions the organisation can change.

Useful methods include:

- Timeline and change analysis.
- Five Whys used without forcing a single chain.
- Fault tree or causal graph.
- Barrier and control analysis.
- Counterfactual testing.

“Human error” is not a sufficient root cause.

## 23. Corrective and Preventive Actions

CAPA types may include:

- Immediate correction and cleanup.
- Permanent technical fix.
- Detection and alert improvement.
- Containment and recovery improvement.
- Test, review, design, or change control.
- Capacity, dependency, and resilience work.
- Documentation, runbook, training, and ownership.
- Platform or organisational improvement.

Every action defines:

- Incident and causal finding.
- Expected risk reduction.
- Priority and rationale.
- Owner and due date.
- Acceptance and effectiveness evidence.
- Dependencies and status.

Actions should favour systemic guardrails over reminders to “be more careful.”

## 24. Post-Incident Review

A formal review is expected for:

- Critical and high-severity incidents.
- Security, privacy, data integrity, safety, or regulatory events.
- Repeated or high-risk near misses.
- Incidents with significant communication, recovery, or control failure.

The review covers:

1. Intended system behaviour and context.
2. Impact and timeline.
3. Detection, response, communication, and recovery.
4. Causal and contributing conditions.
5. What worked well.
6. What made response harder.
7. CAPA and learning.

Facilitation should create psychological safety while maintaining factual and action accountability.

## 25. Knowledge Management

Incident learning should update:

- Service catalogue and ownership.
- Architecture and dependency maps.
- Runbooks and recovery procedures.
- Known errors and troubleshooting guidance.
- Alerts, dashboards, SLOs, and telemetry.
- Test cases, failure injection, and regression suites.
- Deployment, change, maintenance, and access controls.
- Training and onboarding.

Sensitive postmortems may require separate internal and external versions.

Knowledge requires an owner, audience, review date, classification, and retirement path.

## 26. Security and Compliance

For suspected security, privacy, fraud, safety, or regulated-data events:

- Engage the designated specialist authority immediately.
- Preserve evidence with chain-of-custody and integrity controls where required.
- Restrict channels, recordings, access, and distribution.
- Avoid tipping off an adversary or changing evidence unnecessarily.
- Coordinate containment with forensic and legal needs.
- Track notification and reporting deadlines.
- Use approved customer, regulator, insurer, and law-enforcement communication.
- Record access, decisions, disclosure, retention, and destruction.

Engineering restoration does not replace breach assessment, regulatory reporting, or legal authority.

## 27. Common Mistakes

- Waiting for proof before declaring a high-impact incident.
- Allowing the main investigator to coordinate the whole response.
- Pursuing root cause before containing user harm.
- Running multiple uncoordinated changes.
- Treating every observation as fact.
- Failing to record decisions and exact times.
- Communicating speculation or unrealistic recovery estimates.
- Silencing users or support while dashboards look healthy.
- Closing when service is restored but data remains inconsistent.
- Performing RCA to find a person to blame.
- Creating dozens of low-value action items.
- Leaving CAPA without priority, evidence, or governance.
- Using AI summaries as authoritative timelines.
- Ignoring responder fatigue and handoff quality.

## 28. Best Practices

- Declare early and reclassify as evidence changes.
- Use one Incident Commander and explicit roles.
- State impact, objective, owner, and next update repeatedly.
- Mitigate harm before optimising diagnosis.
- Make one controlled change at a time when practical.
- Record hypotheses and disconfirming evidence.
- Compare healthy and unhealthy cohorts.
- Predefine action success, stop, and fallback.
- Keep communication factual, empathetic, and regular.
- Verify user outcomes and data, not only infrastructure.
- Preserve evidence and reconcile emergency changes.
- Review systems and conditions, not personalities.
- Track fewer, stronger actions to verified completion.
- Exercise incident roles, runbooks, failover, and communication.

## 29. Templates

### Incident Record

```markdown
# Incident <ID>: <Title>

## Status, Severity, and Impact
## Incident Commander and Roles
## Start, Detection, Declaration, Mitigation, Resolution
## Current Facts and Unknowns
## Objectives and Actions
## Timeline and Decisions
## Communications
## Recovery and Stability
## Residual Risk and Follow-Up
```

### Situation Update

```markdown
**Status and severity:**
**Confirmed impact:**
**Current action:**
**Known facts / uncertainty:**
**Workaround:**
**Next update:**
```

### RCA and CAPA

```markdown
## Impact and Timeline
## Trigger and Direct Causes
## Contributing and Latent Conditions
## Safeguard and Response Analysis
## Evidence and Uncertainty
## Corrective and Preventive Actions
```

## 30. Examples

### Example: Deployment Incident

Error rate rises after a canary expands. Observability identifies the affected version and region.

The on-call declares an incident, the Incident Commander stops exposure, the Technical Lead confirms a contract incompatibility, and Deployment rolls back. Stability is verified across user outcomes before resolution.

### Example: Data Integrity Incident

A retry defect creates duplicate financial records while availability remains normal.

The team contains new writes, preserves evidence, identifies affected records, restores safe processing, reconciles data, verifies downstream reports, and communicates the integrity impact. A green uptime chart never substitutes for data recovery.

### Example: Third-Party Failure

A critical provider becomes unavailable. The response activates a degraded mode, communicates limitations, monitors vendor recovery, and prevents queue overflow.

RCA distinguishes the provider trigger from internal contributors such as missing isolation and untested failover.

### Example: Near Miss

A certificate alert is missed, but an engineer notices it before expiry.

The team records a near miss, fixes routing and ownership, adds expiry SLOs and tests, and avoids inventing customer impact merely to justify learning.

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
- Incident, alerting, communication, security, and CAPA standards are planned and non-authoritative.

## 33. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)
- Incident severity, RCA, postmortem, communication, and escalation references are planned and non-authoritative.

## 34. Related Playbooks

- [Observability Playbook](PB-OBSERVABILITY.md) supplies detection and operational evidence.
- [Deployment Playbook](PB-DEPLOYMENT.md) governs rollback and recovery of released change.
- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted incident work.
- [Debugging Playbook](08-debugging-playbook.md) provides focused diagnosis.
- [Security Playbook](09-security-playbook.md) will govern broader security response.
- [Testing Playbook](PB-TESTING.md) consumes escaped defects as regression learning.
- Change Management and Maintenance playbooks are planned and will govern follow-up work.

## 35. Metrics

Use metrics to improve the response system, not rank responders or discourage declaration.

| Metric | What It Reveals | Guardrail |
|---|---|---|
| Time to detect | Observability effectiveness | Measure from actual impact where possible |
| Time to acknowledge | Routing and ownership | Acknowledgement is not understanding |
| Time to declare | Coordination threshold | Do not reward under-declaration |
| Time to contain | Ability to limit harm | Segment containment type |
| Time to mitigate or recover | Restoration capability | Separate user, data, and full recovery |
| Time to communicate | Stakeholder readiness | Quality matters with speed |
| Incident frequency and impact | Reliability trend | Normalise by scale and change |
| Recurrence rate | Learning effectiveness | Use causal similarity, not title |
| Detection source | Blind spots | User reports are important evidence |
| RCA completion time | Learning flow | Do not rush evidence quality |
| CAPA completion and effectiveness | Improvement delivery | Completion without effectiveness is insufficient |
| Responder load and handoffs | Sustainability | Protect health and avoid blame |

## 36. Reference Implementation and Enterprise Appendices

`PB-INCIDENT-MANAGEMENT` is the reference implementation for coordinated operational-response playbooks.

### 36.1 Incident Severity Matrix

| Severity | Impact | Command | Communication |
|---|---|---|---|
| SEV-1 | Catastrophic or widespread | Full immediate structure | Continuous internal, frequent executive/customer as required |
| SEV-2 | Major material impact | Incident Commander and dedicated roles | Regular stakeholder updates |
| SEV-3 | Contained degradation | Coordinated owner response | Targeted updates |
| SEV-4 | Limited impact | Normal owner | Record and notify as needed |

### 36.2 Incident Response Checklist

- [ ] Detect, validate, classify, declare, and assign command.
- [ ] Protect users, data, security, and evidence.
- [ ] Contain, investigate, recover, and verify stability.
- [ ] Communicate facts and next update.
- [ ] Analyse, improve, learn, and close.

### 36.3 Communication Matrix

| Audience | Owner | Trigger | Cadence | Approval |
|---|---|---|---|---|
| Responders | Incident Commander | Declaration | Continuous/current | Incident Commander |
| Support | Communications Lead | User impact | Each material change | Approved comms owner |
| Customers | Communications Lead | Policy/impact threshold | Published commitment | Required authority |
| Executives | Incident Commander | Severity threshold | Agreed cadence | Executive channel owner |
| Security/Legal | Specialist lead | Relevant suspicion | Obligation-driven | Specialist authority |

### 36.4 Escalation Matrix

Escalate by:

- Severity, trajectory, duration, or expanding scope.
- Missing expertise or authority.
- Failed mitigation or recovery.
- Security, privacy, safety, data, legal, or regulatory impact.
- Vendor, customer, executive, or cross-team dependency.
- Responder fatigue or unavailable ownership.

### 36.5 RCA Template

- Impact and factual timeline.
- Trigger and direct technical causes.
- Contributing and latent conditions.
- Detection, safeguard, response, and recovery analysis.
- Evidence, uncertainty, and counterfactuals.
- Corrective and preventive opportunities.

### 36.6 CAPA Template

| Finding | Action | Risk Reduction | Priority | Owner | Due | Acceptance Evidence | Status |
|---|---|---|---|---|---|---|---|

### 36.7 Postmortem Template

- Executive summary.
- User and business impact.
- Timeline and response.
- Causes and contributing factors.
- What worked and what hindered response.
- CAPA and learning.
- Distribution, classification, and approval.

### 36.8 Incident Timeline Template

| Time and Zone | Source | Fact, Decision, Action, or Communication | Owner | Evidence/Outcome |
|---|---|---|---|---|

Use one authoritative clock and distinguish observed time from recorded time.

### 36.9 Incident Maturity Model

| Level | Characteristics |
|---|---|
| 1. Ad Hoc | Hero-driven response, unclear roles, incomplete records |
| 2. Repeatable | On-call, severity, channels, runbooks, basic reviews |
| 3. Governed | Command, evidence, communications, RCA, CAPA, compliance |
| 4. Resilient | Exercises, automation, rapid containment, reliable recovery, trend learning |
| 5. Adaptive | Systemic risk and operational learning continuously shape design and investment |

### 36.10 Knowledge Capture Checklist

- [ ] Timeline, causes, evidence, and uncertainty are preserved.
- [ ] Runbooks, known issues, architecture, tests, alerts, and dashboards are updated.
- [ ] Sensitive and external versions are separated.
- [ ] Owners, review dates, classification, and discoverability exist.

### 36.11 Deliverables Checklist

- [ ] Incident record, command roles, timeline, and communications.
- [ ] Containment, recovery, stability, and residual-risk evidence.
- [ ] Incident Report, RCA, CAPA, and postmortem.
- [ ] Knowledge updates, required notices, and closure record.

### 36.12 Incident Closure Checklist

- [ ] Service, users, data, security, and dependencies are stable.
- [ ] Incident Commander and Service Owner agree active response can end.
- [ ] Required communication and regulatory obligations are complete.
- [ ] Timeline, evidence, RCA, postmortem, and knowledge meet policy.
- [ ] CAPA has owners, priority, dates, and acceptance evidence.
- [ ] Emergency changes are reconciled into governed state.
- [ ] Closure authority and time are recorded.

## 37. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Incident Management Playbook with ten-phase response workflow, incident command, classification, communication, RCA, CAPA, security, five quality gates, metrics, and twelve enterprise appendices |

## 38. Summary

`PB-INCIDENT-MANAGEMENT` governs coordinated engineering response when production behaviour creates material impact or risk.

It requires teams to:

- Detect, assess, declare, and establish command early.
- Protect users, data, security, and evidence.
- Contain impact and restore service through controlled decisions.
- Communicate facts, uncertainty, action, and cadence.
- Verify stability before ending active response.
- Analyse systemic causes without blame.
- Track effective corrective and preventive action.
- preserve reusable operational knowledge.

An incident is not successful because it closed quickly. It is successful when harm is reduced, service is safely restored, stakeholders are informed, evidence is preserved, and the organisation becomes more resilient.
