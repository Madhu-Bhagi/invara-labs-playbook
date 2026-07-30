---
title: Maintenance Playbook
id: PB-MAINTENANCE
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
  - maintenance
  - lifecycle
  - operations
  - sustainment
  - engineering
  - playbook
related:
  - PB-OBSERVABILITY
  - PB-INCIDENT-MANAGEMENT
  - PB-CHANGE-MANAGEMENT
  - PB-DEPLOYMENT
  - PB-AI-ENGINEERING
  - PB-PLATFORM-ENGINEERING
  - PB-SECURITY-ENGINEERING
  - PB-DATA-ENGINEERING
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

# Maintenance Playbook

> **The standard operating procedure for sustaining software systems throughout their operational lifecycle by managing corrective, adaptive, preventive, and perfective maintenance while ensuring reliability, security, maintainability, and long-term business value.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. Maintenance Workflow
10. Maintenance Lifecycle
11. Detailed Phase Activities
12. Maintenance Concepts
13. Maintenance Decision Framework
14. Deliverables
15. Quality Gates
16. Maintenance Checklist
17. AI-Assisted Maintenance
18. Maintenance Governance
19. Risk Management
20. Maintenance Categories
21. Dependency and Platform Management
22. Technical Debt Management
23. Deprecation and End-of-Life Management
24. Continuous Improvement
25. Security and Compliance
26. Common Mistakes
27. Best Practices
28. Templates
29. Examples
30. Related Principles
31. Related Standards
32. Related References
33. Related Playbooks
34. Metrics
35. Reference Implementation and Enterprise Appendices
36. Revision History
37. Summary

## 1. Overview

Maintenance is the continuous engineering stewardship of software after its initial release.

It preserves and improves the system’s:

- Business fitness and user value.
- Reliability, resilience, and recoverability.
- Security, privacy, and compliance.
- Performance, capacity, and cost efficiency.
- Compatibility with dependencies, platforms, data, and integrations.
- Maintainability, testability, operability, and knowledge.
- Supported lifecycle and responsible retirement.

Maintenance is not:

- A bug-fixing guide.
- Unplanned work performed only when something breaks.
- A backlog where all inconvenient engineering work is hidden.
- Permanent preservation of every legacy system.
- Automatic upgrading to every latest version.
- Exempt from requirements, design, review, testing, change, deployment, or incident controls.

```text
Operational Evidence and Business Need
                 │
                 ▼
           PB-MAINTENANCE
     assess · prioritise · sustain · retire
                 │
                 ▼
 Existing Engineering and Operations Playbooks
                 │
                 └──────────────► Operational Evidence
```

Maintenance closes the lifecycle loop: production evidence changes future requirements, architecture, design, implementation, testing, deployment, operations, and investment.

## 2. Purpose

This playbook enables teams to:

- Maintain a current inventory of owned software and lifecycle obligations.
- Detect maintenance need before it becomes avoidable failure.
- Balance corrective, adaptive, preventive, and perfective work.
- Prioritise risk reduction and business value against cost and opportunity.
- Govern dependencies, runtimes, platforms, integrations, and vendor support.
- Make technical debt visible and decision-ready.
- Plan upgrades, modernisation, migration, deprecation, replacement, and retirement.
- Preserve security and compliance throughout operational life.
- Validate that maintenance achieves its intended outcome.
- Improve system health and reduce recurring operational toil.
- Retire systems, data, access, infrastructure, and obligations responsibly.

## 3. Objectives

Following this playbook should produce:

- Named ownership and an accurate lifecycle inventory.
- Periodic health and sustainability assessments.
- A prioritised maintenance portfolio linked to evidence and risk.
- Planned dependency, platform, security, debt, and lifecycle work.
- Changes executed through the normal engineering lifecycle.
- Measured improvement in reliability, security, compatibility, maintainability, and value.
- Controlled deprecation and end-of-life decisions.
- Current documentation, runbooks, tests, and knowledge.
- Reduced unsupported technology, hidden debt, and emergency maintenance.

The objective is sustainable value, not indefinite asset life, zero technical debt, or upgrade activity for its own sake.

## 4. Scope

### In Scope

- Corrective maintenance for defects and incorrect behaviour.
- Adaptive maintenance for changed platforms, dependencies, regulations, integrations, and business environments.
- Preventive maintenance that reduces credible future risk.
- Perfective maintenance that improves performance, maintainability, usability, operability, or cost.
- Security patches and vulnerability remediation.
- Dependency, framework, runtime, database, operating-system, cloud, and vendor upgrades.
- Technical debt assessment and reduction.
- Capacity, performance, resilience, observability, and operational-toil improvement.
- Data lifecycle, migration, archival, retention, and cleanup.
- Deprecation, replacement, end-of-support, end-of-life, and retirement.
- Documentation, knowledge, ownership, and runbook maintenance.

### Proportionate Maintenance

| Asset Profile | Expected Control |
|---|---|
| Low-impact, simple, internally owned | Periodic health review, supported components, basic debt and security controls |
| Customer-facing or material workflow | Active roadmap, dependency cadence, operational objectives, debt budget, tested recovery |
| Critical, regulated, security-sensitive, or high-data-impact | Formal lifecycle evidence, specialists, stronger support, resilience, compliance, and retirement governance |
| Legacy or declining-value | Explicit sustain, modernise, replace, isolate, or retire decision with time-bound risk |

### Out of Scope

- Unrelated new product development.
- Initial system architecture and implementation.
- Vendor-specific upgrade commands.
- Active incident command.
- Production change approval and deployment execution.

Maintenance may create requirements, designs, code, tests, changes, deployments, and incidents; it does not replace the playbooks governing those activities.

## 5. When to Use This Playbook

Apply this playbook:

- Throughout the operational life of every supported software asset.
- On a periodic lifecycle-health cadence.
- When operational signals or incidents reveal degradation or recurring toil.
- When vulnerabilities or security advisories appear.
- Before dependencies, platforms, vendors, certificates, or contracts lose support.
- When user needs, regulations, integrations, traffic, data, or cost change.
- When technical debt materially affects delivery or reliability.
- Before major upgrade, migration, modernisation, replacement, or retirement decisions.
- When ownership, knowledge, support, or documentation becomes uncertain.

Maintenance begins when a system enters supported use and ends only when retirement obligations are complete.

## 6. Roles and Responsibilities

| Role | Responsibilities | Authority |
|---|---|---|
| Service or Product Owner | Owns value, supported outcomes, lifecycle state, and investment trade-offs | Accepts product and service lifecycle decisions |
| Maintenance Owner | Coordinates inventory, health, backlog, plans, evidence, and reviews | Owns maintenance portfolio |
| Technical Owner | Assesses architecture, code, dependencies, debt, compatibility, and options | Recommends technical direction |
| Operations Owner | Supplies reliability, capacity, toil, support, recovery, and cost evidence | Accepts operational readiness |
| Security or Compliance Owner | Assesses vulnerabilities, support, obligations, and remediation | Accepts assigned specialist risk |
| Data Owner | Owns data integrity, retention, migration, archival, and disposal | Accepts data lifecycle decisions |
| Platform Owner | Owns runtime, infrastructure, environment, vendor, and platform lifecycle | Accepts platform compatibility |
| Change and Release Authority | Governs operational implementation and production promotion | Approves assigned changes/releases |
| Finance or Commercial Owner | Supplies cost, contract, licence, vendor, and investment evidence | Accepts commercial scope |
| Knowledge Owner | Maintains documentation, runbooks, support knowledge, and handover | Accepts knowledge readiness |

### Accountability Rules

- Every supported asset has one accountable owner.
- Ownership includes lifecycle, security, support, data, and retirement—not only feature delivery.
- Risk acceptance must be time-bounded and held by authorised roles.
- AI cannot own lifecycle decisions, accept unsupported technology risk, or approve retirement.

## 7. Inputs

Inputs should include:

- Asset inventory, ownership, criticality, users, data, dependencies, and lifecycle state.
- Product roadmap, service objectives, customer commitments, and business value.
- Observability, SLO, capacity, performance, cost, support, and usage evidence.
- Incidents, defects, problem patterns, near misses, and corrective actions.
- Vulnerabilities, advisories, exploitability, licences, and compliance obligations.
- Dependency, framework, runtime, platform, database, integration, and vendor support status.
- Technical debt, code quality, test health, architecture, and documentation quality.
- Change failure, deployment, recovery, and operational-toil evidence.
- Skills, staffing, knowledge concentration, contracts, and budget.
- Deprecation, replacement, migration, data, communication, and retirement constraints.

## 8. Entry Criteria

Before a maintenance activity is planned:

- [ ] Asset, owner, lifecycle state, objective, and maintenance category are identified.
- [ ] Evidence and trigger are recorded.
- [ ] Affected users, services, data, dependencies, and obligations are known.
- [ ] Urgency, impact, security, support, compatibility, and operational risk can be assessed.
- [ ] Sustain, improve, modernise, replace, isolate, deprecate, or retire options can be considered.
- [ ] Required engineering and operational authorities are identifiable.

Unknown ownership or lifecycle state is itself a maintenance risk and must be resolved.

## 9. Maintenance Workflow

```text
Operational and Lifecycle Evidence
              │
              ▼
1. Identify Maintenance Need
              │
              ▼
2. Assess Health and Impact
              │
              ▼
3. Prioritise Portfolio
              │
              ▼
4. Plan Maintenance
              │
              ▼
5. Implement Changes
              │
              ▼
6. Validate Results
              │
              ▼
7. Deploy Through Governance
              │
              ▼
8. Monitor Outcomes
              │
              ▼
9. Update Knowledge and Lifecycle
              │
              ▼
10. Close and Improve
              └──────────────► Continuous Review
```

## 10. Maintenance Lifecycle

| Lifecycle State | Meaning | Primary Decision |
|---|---|---|
| Emerging | New asset entering supported use | Establish ownership and baseline |
| Active | Receiving normal investment and change | Balance value, reliability, and health |
| Sustaining | Stable value with selective improvement | Maintain support and reduce risk |
| Constrained | Material debt, support, skill, cost, or compatibility risk | Modernise, isolate, replace, or accept temporarily |
| Deprecated | New adoption is discouraged and migration is active | Complete transition |
| End of Support | Normal changes and assistance cease under defined terms | Enforce remaining obligations |
| Retired | Service and access are removed | Verify data, cost, dependency, and evidence closure |

Lifecycle state is explicit, owned, dated, and reviewed. “Legacy” alone is not a decision.

## 11. Detailed Phase Activities

### Phase 1: Identify Maintenance Need

**Goal:** Detect and record evidence that an asset requires sustainment action.

**Activities:**

1. Review telemetry, SLOs, incidents, defects, support, usage, cost, security, and capacity.
2. Monitor dependency, platform, vendor, certificate, licence, and support milestones.
3. Review technical debt, test instability, build health, documentation, and ownership.
4. Capture customer, regulatory, integration, and roadmap change.
5. Classify the need as corrective, adaptive, preventive, perfective, or lifecycle.
6. Assign owner and initial urgency.

**Outputs:** Maintenance Need Record, evidence, category, owner, and initial scope.

### Phase 2: Assess Health and Impact

**Goal:** Understand current sustainability, risk, value, and available options.

**Activities:**

1. Assess business value, criticality, usage, user impact, and cost of failure.
2. Assess reliability, security, performance, capacity, supportability, and recoverability.
3. Assess dependency, platform, skill, vendor, test, architecture, debt, and knowledge risk.
4. Identify affected data, integrations, downstream consumers, and obligations.
5. Compare sustain, remediate, modernise, replace, isolate, deprecate, and retire options.
6. Record uncertainty and evidence gaps.

**Outputs:** Lifecycle Health Assessment, impact analysis, risk, options, and recommendation.

### Phase 3: Prioritise Portfolio

**Goal:** Allocate maintenance capacity to the highest-value risk reduction and improvement.

**Activities:**

1. Compare urgency, exploitability, support deadlines, failure impact, recurrence, and cost of delay.
2. Estimate business value, risk reduction, effort, dependency, and opportunity cost.
3. Balance mandatory, corrective, preventive, adaptive, and perfective work.
4. Reserve capacity for recurring maintenance rather than waiting for crisis.
5. Escalate risks that exceed product or team authority.
6. Record priority, rationale, target window, and deferred risk.

**Outputs:** Prioritised Maintenance Portfolio, capacity allocation, risk acceptance, and roadmap.

### Phase 4: Plan Maintenance

**Goal:** Create a safe, traceable engineering and lifecycle plan.

**Activities:**

1. Define objective, scope, success, non-goals, owners, and timeline.
2. Identify requirements, design, implementation, tests, migration, compatibility, and documentation.
3. Plan dependency order, coexistence, data, rollback, roll-forward, and recovery.
4. Define security, compliance, licence, vendor, and communication controls.
5. Choose incremental, progressive, strangler, replace, deprecate, or retire strategy.
6. Route the planned work through applicable engineering playbooks.

**Outputs:** Maintenance Plan, engineering work package, validation, migration, and lifecycle plan.

### Phase 5: Implement Changes

**Goal:** Produce maintainable, review-ready maintenance changes.

**Activities:**

1. Follow approved requirements, design, coding, AI, review, and documentation practices.
2. Make the smallest coherent change that achieves the maintenance objective.
3. Preserve compatibility or provide an explicit migration contract.
4. Update automated tests and operational controls.
5. Remove obsolete code, configuration, dependencies, flags, and workarounds when safe.
6. Preserve traceability to maintenance need and risk.

**Outputs:** Reviewed implementation, migrations, tests, documentation, and change package.

### Phase 6: Validate Results

**Goal:** Prove that maintenance improves the target outcome without unacceptable regression.

**Activities:**

1. Verify functional behaviour, compatibility, security, performance, resilience, and data integrity.
2. Test upgrades, migrations, rollback, recovery, coexistence, and supported environments.
3. Validate vulnerability, licence, policy, and support status.
4. Compare before-and-after baselines.
5. Verify documentation, runbooks, alerts, dashboards, and support readiness.
6. Record residual risk and limitations.

**Outputs:** Test evidence, compatibility report, security validation, operational readiness, and release recommendation.

### Phase 7: Deploy Through Governance

**Goal:** Introduce the maintenance change safely into managed environments.

**Activities:**

1. Classify and approve the operational change through `PB-CHANGE-MANAGEMENT`.
2. Execute promotion, verification, rollback, and recovery through `PB-DEPLOYMENT`.
3. Use progressive exposure where uncertainty or impact warrants it.
4. Coordinate consumers, vendors, support, migrations, and communications.
5. Record actual state, deviations, and release outcome.
6. Invoke Incident Management if material harm occurs.

**Outputs:** Approved Change Record, deployed maintenance release, validation, and operational handoff.

### Phase 8: Monitor Outcomes

**Goal:** Determine whether the maintenance objective and expected risk reduction were achieved.

**Activities:**

1. Observe service, user, security, capacity, cost, support, and business signals.
2. Compare actual outcome with the baseline and success criteria.
3. Detect regression, new debt, compatibility issues, and shifted bottlenecks.
4. Review incident, alert, defect, and user feedback.
5. Verify action effectiveness over the defined observation window.
6. Create follow-up when benefits are incomplete or side effects emerge.

**Outputs:** Outcome Report, effectiveness evidence, residual risk, and follow-up.

### Phase 9: Update Knowledge and Lifecycle

**Goal:** Keep the asset’s lifecycle truth current and discoverable.

**Activities:**

1. Update inventory, ownership, version, support dates, dependencies, and lifecycle state.
2. Update architecture, design, runbooks, troubleshooting, tests, and operational documentation.
3. Record removed, deprecated, migrated, and remaining interfaces or components.
4. Update technical debt and maintenance backlog.
5. Communicate consumer, support, security, and retirement implications.
6. Preserve decisions and evidence.

**Outputs:** Current lifecycle record, dependency inventory, documentation, and knowledge.

### Phase 10: Close and Improve

**Goal:** Complete the activity and improve the sustainment system.

**Activities:**

1. Confirm objective, gates, evidence, communication, and ownership.
2. Close or replan residual work and accepted risk.
3. Review estimation, automation, validation, deployment, and coordination.
4. Improve recurring schedules, standard changes, tooling, and preventive controls.
5. Archive evidence according to policy.
6. Feed learning into the next lifecycle-health review.

**Outputs:** Closure Record, improvement actions, updated scorecard, and next review date.

## 12. Maintenance Concepts

### Corrective Maintenance

Restores intended behaviour after defects or failures.

### Adaptive Maintenance

Keeps software useful when external conditions change, including platforms, dependencies, interfaces, regulations, data, and business processes.

### Preventive Maintenance

Reduces credible future failure, security, support, or operability risk before active impact.

### Perfective Maintenance

Improves performance, maintainability, usability, cost, operability, or value without primarily correcting a defect.

### Technical Debt

A current or future cost created by a technical decision, constraint, shortcut, or changed context. Debt is not synonymous with old code or disliked design.

### Obsolescence

Loss of support, compatibility, skills, security, or economic fitness despite continued function.

### Modernisation

Targeted improvement of architecture, runtime, platform, delivery, or operations to meet current needs. It is an option, not an automatic rewrite.

### Retirement

The governed removal of a system and its operational, data, access, financial, contractual, and support obligations.

## 13. Maintenance Decision Framework

### Decision Questions

1. What evidence shows a maintenance need?
2. What value or obligation does the asset still serve?
3. What happens if action is delayed?
4. Is the risk local or systemic?
5. Is maintenance technically and economically sustainable?
6. Would isolation, modernisation, replacement, deprecation, or retirement create better value?
7. What migration and data obligations remain?

### Strategic Options

| Option | Use When |
|---|---|
| Sustain | Asset remains fit with routine maintenance |
| Improve | Targeted work creates worthwhile value or risk reduction |
| Modernise | Core capability remains valuable but technology or design is unsustainable |
| Replace | Another solution meets needs with better lifecycle economics |
| Isolate | Immediate replacement is infeasible but exposure can be reduced |
| Deprecate | Consumers need time and a supported migration path |
| Retire | Value or obligation no longer justifies continued operation |
| Accept Temporarily | Risk is authorised, time-bounded, monitored, and has an exit plan |

Avoid sunk-cost reasoning. Evaluate future value, future cost, and transition risk.

## 14. Deliverables

| Deliverable | Minimum Content |
|---|---|
| Asset Lifecycle Record | Owner, state, criticality, users, data, dependencies, support dates |
| Maintenance Need Record | Trigger, evidence, category, impact, urgency |
| Lifecycle Health Assessment | Value, risk, support, security, debt, options |
| Maintenance Portfolio | Priority, capacity, target, rationale, deferred risk |
| Maintenance Plan | Scope, strategy, engineering work, validation, migration, recovery |
| Dependency Report | Versions, support, advisories, licences, owners, upgrade path |
| Technical Debt Register | Context, consequence, evidence, treatment, owner |
| Validation and Outcome Report | Baseline, result, regression, risk reduction |
| Deprecation or EOL Plan | Consumers, dates, migration, communication, data, retirement |
| Closure Record | Evidence, lifecycle updates, residual work, next review |

## 15. Quality Gates

### Gate A: Ownership and Health

- Asset, value, criticality, owner, lifecycle state, dependencies, and evidence are current.

### Gate B: Decision and Priority

- Options, risk, obligations, value, cost, urgency, and deferred consequences support the decision.

### Gate C: Engineering Readiness

- Scope, compatibility, security, data, tests, migration, recovery, and documentation are credible.

### Gate D: Change and Outcome

- Approved implementation is deployed and validated.
- Operational evidence shows the intended result without unacceptable regression.

### Gate E: Lifecycle Closure

- Inventory, ownership, debt, support, documentation, communication, and next review are current.
- Retirement obligations are complete where applicable.

## 16. Maintenance Checklist

### Assess

- [ ] Confirm owner, value, lifecycle state, support, dependencies, and evidence.
- [ ] Classify maintenance category and evaluate sustain, modernise, replace, or retire.
- [ ] Assess security, data, compatibility, skills, cost, operations, and debt.

### Execute

- [ ] Plan through applicable engineering playbooks.
- [ ] Validate compatibility, migration, security, performance, recovery, and documentation.
- [ ] Govern operational change and deployment.

### Close

- [ ] Measure outcome and risk reduction.
- [ ] Update inventory, lifecycle, debt, dependencies, knowledge, and communication.
- [ ] Assign residual work and next review.

## 17. AI-Assisted Maintenance

All AI-assisted work follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

AI may assist with:

- Inventory and dependency analysis.
- Advisory, changelog, licence, and compatibility summarisation.
- Technical debt clustering and impact discovery.
- Upgrade, migration, test, and deprecation planning.
- Code modernisation and documentation updates.
- Operational trend and lifecycle-option analysis.

Humans must:

- Validate package identity, version support, advisories, licences, compatibility, and migration claims.
- Protect source, credentials, client data, production telemetry, and proprietary context.
- Review generated code, tests, configuration, and removal plans.
- Challenge rewrite bias, latest-version bias, and invented urgency.
- Retain priority, architecture, risk, support, deprecation, and retirement authority.

AI may reveal candidates; it cannot decide that an asset is safe to upgrade or retire.

## 18. Maintenance Governance

Governance requires:

- Complete asset and dependency ownership.
- Defined lifecycle states, support dates, review cadence, and evidence.
- Traceability from operational need to maintenance outcome.
- Risk-proportionate engineering, change, deployment, and specialist controls.
- Time-bounded support and risk exceptions.
- A visible portfolio balancing features, corrective work, preventive work, upgrades, and debt.
- Review of unsupported technology, recurring failure, concentration of knowledge, and retirement obligations.
- Evidence-based lifecycle decisions.

### Exceptions

An exception records scope, risk, compensating control, authority, owner, expiry, monitoring, and exit plan.

“We have always used it” is not acceptable lifecycle evidence.

## 19. Risk Management

| Risk | Consequence | Control |
|---|---|---|
| Reactive-only maintenance | Preventable incidents and emergencies | Planned preventive portfolio |
| Unsupported dependency | Security and compatibility exposure | Inventory, support dates, upgrade cadence |
| Upgrade regression | User or service harm | Compatibility tests and progressive change |
| Hidden technical debt | Slow delivery and brittle recovery | Evidence-based debt register |
| Knowledge concentration | Unsafe support and change | Documentation, pairing, ownership rotation |
| Platform obsolescence | Forced migration or outage | Lifecycle horizon and staged modernisation |
| Patch delay | Exploitable exposure | Risk-based patch targets and exception |
| Perpetual workaround | Complexity and operational toil | Expiry and permanent treatment |
| Rewrite bias | Costly loss of proven behaviour | Incremental options and economic evidence |
| Retirement without discovery | Broken consumers or lost obligations | Dependency, data, contract, and access mapping |
| Zombie asset | Ongoing cost and attack surface | Ownership enforcement and retirement |
| Maintenance starvation | Risk compounds invisibly | Capacity allocation and leadership review |

## 20. Maintenance Categories

| Category | Trigger | Typical Outcome |
|---|---|---|
| Corrective | Defect, failure, incorrect result | Restored behaviour and regression protection |
| Adaptive | External environment changed | Compatibility and continued support |
| Preventive | Credible future risk | Reduced failure, security, or support risk |
| Perfective | Improvement opportunity | Better performance, cost, usability, or maintainability |
| Lifecycle | Support or value transition | Modernisation, deprecation, replacement, or retirement |

One activity may span categories. Classification helps portfolio balance; it does not create separate engineering standards.

## 21. Dependency and Platform Management

Maintain an inventory of:

- Direct and material transitive dependencies.
- Frameworks, runtimes, operating systems, databases, and platforms.
- APIs, data contracts, vendors, services, and build tools.
- Version, owner, purpose, licence, source, support dates, and known risk.

### Upgrade Decisions

Consider:

- Security and exploitability.
- Vendor and community support.
- Compatibility and migration effort.
- Reliability and performance.
- Licence and commercial terms.
- Ecosystem and skills.
- Cost of delay and skipped-version accumulation.

### Controls

- Automate discovery and update proposals, not blind adoption.
- Pin and verify versions according to ecosystem needs.
- Test supported upgrade paths and representative data.
- Use canaries and progressive rollout.
- Remove unused dependencies.
- Track exceptions to supported-version policy.

## 22. Technical Debt Management

Each material debt item should state:

- Context and evidence.
- Current consequence.
- Expected future cost or risk.
- Affected users, systems, delivery, reliability, security, or operations.
- Treatment options and incremental path.
- Owner, priority, trigger, and review date.

### Debt Decisions

| Treatment | Use When |
|---|---|
| Repay now | Current risk or drag exceeds competing work |
| Reduce incrementally | Value is clear but broad replacement is unnecessary |
| Contain | Exposure can be bounded until planned treatment |
| Accept temporarily | Risk is understood, authorised, and time-bounded |
| Remove by retirement | Capability no longer justifies remediation |

Code age, style preference, or use of an older pattern is not sufficient evidence of debt.

## 23. Deprecation and End-of-Life Management

### Required Decisions

- What is deprecated: feature, API, version, service, platform, integration, or product?
- Why and under whose authority?
- Who consumes it?
- What supported alternative exists?
- What are deprecation, migration, support-end, and retirement dates?
- What data, access, infrastructure, contract, cost, and compliance obligations remain?

### Retirement Sequence

1. Discover consumers, dependencies, data, and obligations.
2. Approve lifecycle decision and migration plan.
3. Announce deprecation and freeze new adoption.
4. Support migration and measure remaining use.
5. Enforce end-of-support according to commitment.
6. Disable progressively where safe.
7. Archive, migrate, or delete data under policy.
8. Remove traffic, access, credentials, infrastructure, alerts, licences, and cost.
9. Verify no dependency or obligation remains.
10. Close and preserve required evidence.

Retirement is incomplete while hidden consumers, sensitive data, access, or financial commitments remain.

## 24. Continuous Improvement

Maintenance improvement should target:

- Fewer recurring incidents and defects.
- Faster, safer upgrades and recovery.
- Lower operational toil and alert noise.
- Better test, build, deployment, and documentation health.
- Reduced unsupported technology and concentration risk.
- Improved performance, capacity, and cost.
- Clearer lifecycle decisions and earlier retirement.

Use incident reviews, change outcomes, dependency trends, security findings, user feedback, and scorecards to adjust preventive work and capacity.

Repeated manual maintenance is a candidate for automation only when the procedure and safety conditions are understood.

## 25. Security and Compliance

Maintenance must:

- Monitor applicable vulnerabilities and security advisories.
- Prioritise using exploitability, exposure, asset criticality, and compensating controls.
- Maintain supported versions and time-bounded exceptions.
- Preserve software provenance, dependency integrity, licences, and audit evidence.
- Review identity, access, secrets, certificates, encryption, and security configuration.
- Maintain privacy, retention, residency, archival, deletion, and legal-hold obligations.
- Validate that patches and upgrades preserve security controls.
- Remove retired credentials, access paths, data, infrastructure, and vendor accounts.

Patch speed matters, but uncontrolled change can also create security risk. Use expedited governance appropriate to credible urgency.

## 26. Common Mistakes

- Treating maintenance as leftover capacity.
- Performing only corrective work.
- Upgrading because a newer version exists without a clear objective.
- Delaying upgrades until forced by end of support.
- Calling every disliked design technical debt.
- Maintaining systems with no accountable owner.
- Accepting permanent security or support exceptions.
- Rewriting instead of incrementally reducing risk.
- Removing code before discovering consumers and data obligations.
- Measuring tickets closed rather than health improved.
- Failing to update tests, runbooks, and lifecycle records.
- Automating dependency merges without compatibility evidence.
- Keeping zombie services because retirement ownership is unclear.
- Using AI modernisation output without behavioural verification.

## 27. Best Practices

- Reserve explicit capacity for maintenance.
- Keep asset, dependency, ownership, and support inventories current.
- Review lifecycle health before deadlines become emergencies.
- Make small, frequent, reversible upgrades.
- Separate dependency discovery from adoption authority.
- Use operational evidence to prioritise debt.
- Prefer incremental modernisation over speculative rewrites.
- Build compatibility and migration tests.
- Remove obsolete code, flags, workarounds, access, and infrastructure.
- Make deprecation timelines realistic and measurable.
- Treat retirement as a full engineering project.
- Measure risk reduction and value, not maintenance activity.
- Preserve human lifecycle judgement when AI assists.

## 28. Templates

### Maintenance Plan

```markdown
# Maintenance Plan

## Asset, Owner, and Lifecycle State
## Need, Evidence, and Category
## Value, Impact, Risk, and Urgency
## Options and Decision
## Scope, Engineering Work, and Dependencies
## Compatibility, Data, Security, and Compliance
## Validation, Change, Deployment, and Recovery
## Outcome Measures, Knowledge, and Next Review
```

### Lifecycle Health Assessment

```markdown
**Asset and owner:**
**Business value and criticality:**
**Reliability and operations:**
**Security and compliance:**
**Dependencies and support:**
**Architecture, tests, debt, and knowledge:**
**Cost and skills:**
**Lifecycle recommendation:**
```

### Deprecation Notice

```markdown
**Capability and affected versions:**
**Reason:**
**Supported alternative:**
**Deprecation date:**
**Migration support:**
**End-of-support date:**
**Retirement date:**
**Owner and contact:**
```

## 29. Examples

### Example: Preventive Runtime Upgrade

A runtime remains functional but reaches end of support in six months.

The team assesses dependencies, builds compatibility tests, upgrades incrementally, uses progressive deployment, observes performance and errors, updates inventory, and removes the expiring runtime before urgency becomes an emergency.

### Example: Evidence-Based Debt

A shared client causes repeated incidents, slow changes, and duplicated recovery logic.

The debt record links incidents and lead-time evidence. The team extracts one bounded interface, migrates consumers gradually, measures outcomes, and avoids a speculative platform rewrite.

### Example: Security Patch

A critical advisory affects an internet-exposed component.

Security evaluates exploitability and compensating controls. The team uses an expedited Change path, validates compatibility and security, deploys progressively, monitors outcomes, and records the supported version.

### Example: Retirement

Usage of an old reporting service reaches zero after migration.

The team verifies consumers, archives required data, removes credentials, scheduled jobs, infrastructure, dashboards, alerts, licences, and support commitments, then records the asset as Retired.

## 30. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Architecture Principles](../01-principles/03-architecture-principles.md)
- [Coding Principles](../01-principles/04-coding-principles.md)
- [Testing Principles](../01-principles/05-testing-principles.md)
- [Security Principles](../01-principles/06-security-principles.md)
- [Observability Principles](../01-principles/07-observability-principles.md)
- [Performance Principles](../01-principles/08-performance-principles.md)

## 31. Related Standards

- [Playbook Authoring Standard](../03-standards/PB-AUTHORING.md)
- [Engineering Traceability Standard](../03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](../03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](../03-standards/STD-VERSIONING.md)
- [Engineering Terminology Standard](../03-standards/TERM-STANDARD.md)
- [Documentation Style Guide](../03-standards/DOC-STYLE.md)
- Maintenance, dependency, lifecycle, security, and deprecation standards are planned and non-authoritative.

## 32. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)
- Lifecycle, technical-debt, dependency, supported-version, deprecation, and EOL references are planned and non-authoritative.

## 33. Related Playbooks

- [Observability Playbook](PB-OBSERVABILITY.md) supplies operational health evidence.
- [Incident Management Playbook](PB-INCIDENT-MANAGEMENT.md) supplies corrective and preventive learning.
- [Change Management Playbook](PB-CHANGE-MANAGEMENT.md) governs operational maintenance changes.
- [Deployment Playbook](PB-DEPLOYMENT.md) governs promotion and recovery.
- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted maintenance.
- [Requirements Playbook](PB-REQ.md), [Architecture Playbook](PB-ARCH.md), and [Technical Design Playbook](PB-TECH-DESIGN.md) govern material intent and design change.
- [Coding Playbook](PB-CODING.md), [Code Review Playbook](PB-CODE-REVIEW.md), and [Testing Playbook](PB-TESTING.md) govern implementation and verification.
- [Platform Engineering Playbook](PB-PLATFORM-ENGINEERING.md) governs platform-product sustainment, evolution, and retirement context.
- [Security Engineering Playbook](PB-SECURITY-ENGINEERING.md) governs security risk, vulnerability, patch, credential, and control context.
- [Data Engineering Playbook](PB-DATA-ENGINEERING.md) governs data-product contract, quality, lineage, retention, and consumer context.

## 34. Metrics

Use metrics to improve sustainability and lifecycle decisions, not reward activity or punish owners of older systems.

| Metric | What It Reveals | Guardrail |
|---|---|---|
| Supported asset coverage | Inventory and support health | Confirm ownership and actual support |
| Dependency freshness | Upgrade exposure | Newest is not always required |
| End-of-support horizon | Upcoming lifecycle risk | Weight by criticality and migration time |
| Vulnerability remediation time | Security maintenance flow | Segment severity, exploitability, and exception |
| Technical debt trend | Known delivery and reliability drag | Use evidence, not item count |
| Preventive/corrective ratio | Portfolio balance | No universal target |
| Maintenance lead time | Flow from need to validated outcome | Segment waiting and implementation |
| Upgrade success and rollback rate | Compatibility and process quality | Safe rollback is useful control |
| Recurring incident rate | Corrective action effectiveness | Use causal similarity |
| Operational toil | Repetitive human maintenance burden | Preserve necessary human control |
| Lifecycle review coverage | Governance completeness | Quality matters more than attendance |
| Retirement completion | Removal of cost, access, data, and obligation | Avoid rewarding premature shutdown |

## 35. Reference Implementation and Enterprise Appendices

`PB-MAINTENANCE` is the reference implementation for long-term software stewardship.

### 35.1 Maintenance Planning Checklist

- [ ] Asset, owner, lifecycle state, value, criticality, and evidence are current.
- [ ] Category, options, priority, risk, and target outcome are explicit.
- [ ] Engineering, compatibility, data, security, change, deployment, and recovery are planned.
- [ ] Outcome measures, knowledge updates, and next review are defined.

### 35.2 Dependency Upgrade Checklist

- [ ] Purpose, version, support, licence, advisories, owner, and alternatives are known.
- [ ] Direct and material transitive impact is assessed.
- [ ] Migration notes, compatibility, build, tests, performance, security, and rollback pass.
- [ ] Progressive release, observation, inventory, and cleanup are complete.

### 35.3 Technical Debt Assessment Matrix

| Consequence / Frequency | Low | Medium | High |
|---|---|---|---|
| Low consequence | Observe | Opportunistic improvement | Plan targeted reduction |
| Medium consequence | Opportunistic | Prioritise | High-priority treatment |
| High consequence | Plan | High priority | Immediate or strategic action |

Adjust for security, support deadlines, knowledge concentration, and recovery difficulty.

### 35.4 Lifecycle Decision Matrix

| Value | Sustainability | Direction |
|---|---|---|
| High | High | Sustain and improve |
| High | Low | Modernise, isolate, or replace |
| Low | High | Consolidate, reduce investment, or retire |
| Low | Low | Deprecate and retire unless obligation requires support |

### 35.5 Security Patch Checklist

- [ ] Applicability, exploitability, exposure, criticality, and workaround are assessed.
- [ ] Version, source, integrity, compatibility, tests, and controls are verified.
- [ ] Change path matches urgency and risk.
- [ ] Deployment, monitoring, rollback, and exception evidence are complete.

### 35.6 Platform Compatibility Checklist

- [ ] Supported runtimes, operating systems, databases, browsers, devices, APIs, and regions are defined.
- [ ] Contracts, data, time, locale, network, security, capacity, and recovery are tested.
- [ ] Coexistence and migration windows are safe.
- [ ] Unsupported combinations are communicated and removed.

### 35.7 End-of-Life Planning Template

- Asset, owner, authority, reason, and lifecycle dates.
- Consumers, dependencies, data, contracts, and obligations.
- Supported alternative and migration plan.
- Communication, freeze, disablement, and support policy.
- Data archival/deletion, access removal, infrastructure and cost closure.
- Verification, evidence, and final approval.

### 35.8 Maintenance Maturity Model

| Level | Characteristics |
|---|---|
| 1. Reactive | Maintenance follows failure; ownership and inventory are incomplete |
| 2. Managed | Backlog, patching, upgrades, and periodic reviews exist |
| 3. Governed | Lifecycle, dependency, debt, security, change, and retirement are controlled |
| 4. Preventive | Evidence, automation, capacity, and incremental modernisation reduce emergencies |
| 5. Adaptive | Portfolio investment continuously follows value, health, and lifecycle economics |

### 35.9 Lifecycle Health Scorecard

| Dimension | Evidence |
|---|---|
| Value and usage | Outcomes, users, commitments, roadmap |
| Reliability and operations | SLOs, incidents, recovery, toil |
| Security and compliance | Advisories, support, controls, obligations |
| Technology and dependencies | Versions, compatibility, platform horizon |
| Engineering health | Tests, build, debt, change safety |
| Ownership and knowledge | Owners, skills, docs, runbooks |
| Economics | Run cost, maintenance cost, alternative cost |
| Lifecycle | State, dates, migration, retirement readiness |

### 35.10 Deliverables Checklist

- [ ] Asset and Lifecycle Health records.
- [ ] Maintenance need, portfolio, plan, dependency, and debt records.
- [ ] Engineering, validation, change, deployment, and outcome evidence.
- [ ] Deprecation/EOL, knowledge, closure, and next-review records.

### 35.11 Continuous Improvement Tracker

| Evidence | Improvement | Expected Outcome | Owner | Target | Validation | Status |
|---|---|---|---|---|---|---|

Track effectiveness, not only completion.

### 35.12 Maintenance Closure Checklist

- [ ] Maintenance objective and expected risk reduction are verified.
- [ ] Functional, security, compatibility, performance, data, and operational outcomes pass.
- [ ] Inventory, versions, lifecycle, support, debt, documentation, and ownership are current.
- [ ] Residual risk and follow-up have owners and dates.
- [ ] Stakeholders and consumers receive required communication.
- [ ] Change, deployment, incident, and evidence records are linked.
- [ ] Next lifecycle review is scheduled or retirement is fully verified.

## 36. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.3 | 2026-07-30 | Invara Labs Engineering | Draft | Linked data-product sustainment and retirement to `PB-DATA-ENGINEERING` |
| 1.0.2 | 2026-07-30 | Invara Labs Engineering | Draft | Linked security sustainment and vulnerability context to `PB-SECURITY-ENGINEERING` |
| 1.0.1 | 2026-07-30 | Invara Labs Engineering | Draft | Linked platform sustainment and retirement to `PB-PLATFORM-ENGINEERING` |
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Maintenance Playbook with ten-phase sustainment workflow, maintenance categories, dependency, debt, deprecation, EOL, security, five quality gates, metrics, and twelve enterprise appendices |

## 37. Summary

`PB-MAINTENANCE` governs long-term software stewardship from supported operation through responsible retirement.

It requires teams to:

- Maintain ownership, inventory, lifecycle state, and health evidence.
- Balance corrective, adaptive, preventive, perfective, and lifecycle work.
- Govern dependencies, platforms, security, technical debt, and knowledge.
- Route maintenance through the established engineering and operations lifecycle.
- Measure outcomes and risk reduction.
- Modernise, replace, deprecate, or retire when continued sustainment no longer creates sufficient value.

With this Draft, the core lifecycle playbook set now covers requirements through long-term stewardship. Formal review and approval remain required before the lifecycle set is considered Stable.
