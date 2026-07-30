---
title: Testing Playbook
id: PB-TESTING
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
  - testing
  - quality
  - verification
  - validation
  - engineering
  - playbook
related:
  - PB-CODE-REVIEW
  - PB-CODING
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

# Testing Playbook

> **The standard operating procedure for verifying and validating software to ensure it satisfies requirements, technical design, security, quality, and production readiness.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. Testing Workflow
10. Testing Lifecycle
11. Detailed Phase Activities
12. Testing Concepts
13. Testing Decision Framework
14. Deliverables
15. Quality Gates
16. Testing Checklist
17. AI-Assisted Testing
18. Testing Governance
19. Risk Management
20. Test Levels and Test Types
21. Defect Management
22. Testing Standards Integration
23. Common Mistakes
24. Best Practices
25. Templates
26. Examples
27. Related Principles
28. Related Standards
29. Related References
30. Related Playbooks
31. Metrics
32. Reference Implementation and Enterprise Appendices
33. Revision History
34. Summary

## 1. Overview

Testing is the engineering discipline of reducing uncertainty through objective evidence.

It verifies that implemented software conforms to its requirements and design, and validates that the resulting behaviour is useful, safe, accessible, reliable, and ready for its intended environment.

Testing is not:

- A tutorial for Selenium, JUnit, Playwright, or another tool.
- A final inspection performed only after implementation.
- The sole responsibility of a quality-assurance role.
- A substitute for clear requirements, sound design, disciplined coding, or code review.
- A claim that software contains no defects.
- Business acceptance, deployment approval, or production authorisation.

This playbook consumes the reviewed change produced by `PB-CODE-REVIEW` and produces a governed test outcome for the Deployment stage.

```text
Reviewed Revision
        │
        ▼
PB-TESTING
        │
        ▼
Tested Release Candidate
        │
        ▼
PB-DEPLOYMENT
```

Testing begins before execution. Requirements analysis, risk assessment, test design, environment control, evidence capture, defect handling, regression, and exit decisions are all part of the testing process.

## 2. Purpose

This playbook enables teams to:

- Verify functional and non-functional requirements.
- Validate business outcomes and acceptance criteria.
- Detect defects before they affect users.
- Select test effort proportionate to change and product risk.
- Build reliable, maintainable automated verification.
- Use exploratory and manual testing where human observation adds value.
- Produce reproducible, reviewable evidence.
- Manage defects consistently from discovery through closure.
- Preserve traceability from requirement to test outcome.
- Make an explicit readiness recommendation without taking deployment authority.
- Learn from escaped defects and improve the engineering system.

## 3. Objectives

Following this playbook should produce:

- An approved test scope and risk model.
- Clear coverage across requirements, design, quality attributes, and operational risks.
- Controlled environments and representative test data.
- Repeatable test cases and automated suites where appropriate.
- Recorded results tied to the tested revision and configuration.
- Reproducible, classified defects.
- Verified fixes and proportionate regression evidence.
- An explicit test-exit decision with residual risk.
- A deployment-ready testing handoff.

The objective is confidence appropriate to the risk, not maximum test count, maximum coverage percentage, or the absence of all known defects.

## 4. Scope

### In Scope

Apply this playbook to:

- New features, enhancements, and defect fixes.
- Refactoring and technical-debt changes.
- APIs, user interfaces, services, modules, data flows, and integrations.
- Database schemas, migrations, transformations, and reporting.
- Configuration, infrastructure, delivery pipeline, and dependency changes.
- Functional and non-functional verification.
- Automated, exploratory, and governed manual testing.
- Release candidates, hotfixes, and recovery changes.

### Proportionate Testing

| Change Profile | Expected Testing |
|---|---|
| Small, local, reversible | Focused automated checks, targeted exploration, affected regression |
| Material feature or contract | Requirement-based test plan, integration and system testing, full impacted regression |
| High-risk security, data, availability, regulated, or cross-system | Specialist testing, production-like evidence, failure and recovery validation, formal exit review |
| Emergency change | Minimum safe critical-path and regression evidence, explicit authority, documented follow-up |

### Out of Scope

This playbook does not:

- Approve requirements, architecture, technical design, or code review.
- Define framework-specific test syntax or tool configuration.
- Replace security assessment, accessibility expertise, performance engineering, or user acceptance authority.
- Authorise production deployment.
- Define incident response after a production failure.
- Guarantee defect-free software.

## 5. When to Use This Playbook

Use this playbook whenever a software or system change can alter behaviour, risk, data, operations, or user outcomes.

Apply it to:

- Planned releases and continuous-delivery changes.
- Features, fixes, refactoring, migrations, configuration, and infrastructure.
- Dependency and platform upgrades.
- Security remediation and compliance changes.
- Performance, reliability, accessibility, and observability work.
- Hotfixes and rollback validation.

Testing may be tailored when:

- The change is documentation-only with no executable effect.
- An experiment is isolated from users and production data.
- An emergency authority invokes an approved expedited path.

Tailoring must record the rationale, omitted coverage, residual risk, compensating controls, owner, and expiry or follow-up.

## 6. Roles and Responsibilities

| Role | Responsibilities | Decision Authority |
|---|---|---|
| Test Owner | Owns strategy, scope, risk, evidence, defects, and test-exit recommendation | Recommends pass, conditional exit, failure, or escalation |
| Engineer | Builds testability, supplies implementation evidence, fixes defects, maintains automated tests | Confirms technical resolution |
| Independent Tester or Reviewer | Executes objective verification outside the author’s assumptions | Accepts assigned test evidence |
| Product Owner | Clarifies intended outcomes and acceptance criteria | Owns business acceptance |
| Architecture or Design Owner | Clarifies constraints and assesses design deviations | Owns design disposition |
| Security Specialist | Defines and evaluates specialist security scope | Accepts assigned security evidence |
| Accessibility Specialist | Evaluates conformance and user impact where required | Accepts assigned accessibility evidence |
| Performance or Reliability Specialist | Evaluates load, resilience, capacity, and recovery | Accepts assigned specialist evidence |
| Environment or Platform Owner | Provides controlled environments, dependencies, access, and observability | Confirms environment fitness |
| Release or Deployment Authority | Consumes test recommendation and residual risk | Authorises or rejects deployment |

### Accountability Rules

- One named Test Owner coordinates each material testing effort.
- Authors may test their own work, but risk may require independent verification.
- Specialist evidence must be approved by qualified specialists.
- Product acceptance and deployment authority remain separate from test execution.
- AI may assist but cannot own scope, close a defect, accept risk, or approve exit.

## 7. Inputs

Required inputs should include:

- Approved requirements and acceptance criteria.
- Architecture decisions and approved technical design.
- Reviewed revision and Code Review outcome.
- Source, build, configuration, migrations, and dependency manifests.
- Implementation test evidence.
- Known risks, assumptions, constraints, and residual review conditions.
- Test strategy or organisational quality policy.
- Supported platforms, environments, integrations, and compatibility targets.
- Security, privacy, accessibility, performance, reliability, and compliance needs.
- Representative test data and data-handling rules.
- Rollout, rollback, recovery, and observability expectations.

Missing inputs are risks. The Test Owner resolves, documents, or escalates them before relying on results.

## 8. Entry Criteria

Testing may begin when:

- [ ] The test target and exact revision are identifiable.
- [ ] Required Code Review scopes are complete.
- [ ] The software builds and deploys to the test environment.
- [ ] Requirements and acceptance criteria are testable.
- [ ] Design, contracts, migrations, and known risks are available.
- [ ] The test scope, owner, independence, and specialist needs are defined.
- [ ] Environments, dependencies, tools, access, and observability are ready.
- [ ] Test data is representative, lawful, controlled, and resettable.
- [ ] Blocking environment or implementation defects are absent.
- [ ] Required baseline and regression suites are available.

If entry criteria fail, record the item as **Not Ready**, assign an owner, and do not interpret incomplete execution as product evidence.

## 9. Testing Workflow

```text
Reviewed Change
      │
      ▼
1. Plan Testing
      │
      ▼
2. Design Test Cases
      │
      ▼
3. Prepare Environment and Data
      │
      ▼
4. Execute Testing
      │
      ▼
5. Report and Triage Defects
      │
      ▼
6. Verify Fixes
      │
      ▼
7. Execute Regression
      │
      ▼
8. Evaluate Exit Criteria
      │
      ▼
Test Outcome and Deployment Handoff
```

The workflow may iterate. A material fix, design change, environment correction, or new risk can return work to an earlier phase.

## 10. Testing Lifecycle

Testing occurs across the engineering lifecycle:

| Lifecycle Stage | Testing Contribution |
|---|---|
| Requirements | Make outcomes, rules, examples, and acceptance criteria testable |
| Architecture | Identify quality attributes, failure modes, boundaries, and testability needs |
| Technical Design | Define contracts, states, instrumentation, data, and test seams |
| Coding | Build automated checks and local evidence |
| Code Review | Verify test intent, adequacy, maintainability, and change readiness |
| Testing | Execute independent and system-level verification and validation |
| Deployment | Run pre-deployment, smoke, canary, and rollback checks |
| Operations | Observe real behaviour and convert failures into regression protection |

```text
Plan → Design → Prepare → Execute → Verify → Report → Decide → Learn
  ▲                                                        │
  └──────────────────── evidence and feedback ─────────────┘
```

## 11. Detailed Phase Activities

### Phase 1: Plan Testing

**Goal:** Define what must be proven, why it matters, and how much evidence is proportionate.

**Activities:**

1. Review requirements, design, reviewed revision, risks, and known conditions.
2. Identify affected users, workflows, components, contracts, data, platforms, and operations.
3. Model failure impact, likelihood, detectability, reversibility, and exposure.
4. Select applicable test levels, types, independence, and specialists.
5. Define environments, data, tools, observability, evidence, and schedule.
6. Define entry, suspension, resumption, and exit criteria.
7. Map requirements and risks to planned tests.

**Outputs:** Test Plan, risk model, scope, traceability baseline, ownership, and entry decision.

### Phase 2: Design Test Cases

**Goal:** Translate requirements and risks into precise, reviewable verification.

**Activities:**

1. Define positive, negative, boundary, state-transition, error, recovery, and abuse cases.
2. Use equivalence classes, boundary analysis, decision tables, state models, and exploratory charters as appropriate.
3. Define preconditions, data, actions, expected results, tolerances, and evidence.
4. Cover permissions, concurrency, retries, time, locale, compatibility, and accessibility where relevant.
5. Identify which cases should be automated, exploratory, manual, simulated, or specialist-led.
6. Review cases for omissions, duplication, maintainability, and false confidence.

**Outputs:** Test cases, automation backlog, exploratory charters, test-data specification, and coverage map.

### Phase 3: Prepare Environment and Data

**Goal:** Establish a controlled and representative test system.

**Activities:**

1. Provision the required version, configuration, dependencies, integrations, and feature flags.
2. Verify environment identity, health, time, certificates, access, and observability.
3. Create lawful, minimal, representative, resettable test data.
4. Mask or synthesize sensitive data unless approved controls explicitly permit its use.
5. Establish baselines, mocks, service virtualization, simulators, and fault controls.
6. Run readiness and smoke checks.
7. Record material differences from production.

**Outputs:** Environment record, data record, readiness evidence, baseline, and limitations.

### Phase 4: Execute Testing

**Goal:** Produce objective evidence against the planned scope.

**Activities:**

1. Confirm the exact test target and environment baseline.
2. Execute automated, exploratory, manual, and specialist tests.
3. Record result, time, revision, environment, data, and evidence.
4. Investigate unexpected behaviour without silently changing expected results.
5. Distinguish product failures, test defects, environment failures, and inconclusive results.
6. Protect evidence from selective reporting.
7. Pause when continuing would corrupt data, invalidate evidence, or create unsafe impact.

**Outputs:** Execution log, results, evidence, coverage status, observations, and candidate defects.

### Phase 5: Report and Triage Defects

**Goal:** Turn observed failures into reproducible, prioritised engineering work.

**Activities:**

1. Reproduce and isolate the observation.
2. Record expected and actual behaviour, steps, evidence, revision, environment, and data.
3. Classify category and severity independently from delivery priority.
4. Assess affected requirements, users, data, systems, and release risk.
5. Route the defect to the responsible owner.
6. Link duplicates without losing distinct evidence.
7. Escalate critical safety, security, privacy, or integrity risks immediately.

**Outputs:** Defect records, triage decisions, ownership, release impact, and updated traceability.

### Phase 6: Verify Fixes

**Goal:** Confirm that a claimed resolution corrects the defect on the current revision.

**Activities:**

1. Review the root cause and intended correction.
2. Reproduce the original failure against the fixed revision.
3. Verify the expected outcome and affected edge cases.
4. Confirm that automated regression protection exists where valuable.
5. Check related components, data, contracts, and operational behaviour.
6. Reopen defects that are incomplete, non-reproducible, or fixed only symptomatically.

**Outputs:** Verified or reopened defect, resolution evidence, and updated regression scope.

### Phase 7: Execute Regression

**Goal:** Establish that the change and its fixes did not damage existing behaviour.

**Activities:**

1. Select regression scope from impact analysis, dependency graph, defect history, and change risk.
2. Run required automated suites on the current candidate.
3. Execute targeted exploratory regression for high-risk interactions.
4. Verify data compatibility, migrations, rollback, and supported configurations.
5. Investigate flaky, skipped, quarantined, or inconclusive tests.
6. Record exclusions and residual risk.

**Outputs:** Regression report, stability evidence, exclusions, and remaining risk.

### Phase 8: Evaluate Exit Criteria

**Goal:** Make a transparent testing outcome and prepare the Deployment handoff.

**Activities:**

1. Reconcile planned versus executed scope.
2. Confirm required evidence, coverage, specialist outcomes, and defect disposition.
3. Evaluate unmet criteria, known limitations, environmental gaps, and residual risk.
4. Select a decision: Pass, Pass with Conditions, Fail, or Escalate.
5. Record the exact tested revision and evidence baseline.
6. Prepare the Test Summary Report and release recommendation.
7. Hand the outcome to Deployment and retain test records.

**Outputs:** Test decision, Test Summary Report, residual-risk record, and Deployment handoff.

## 12. Testing Concepts

### Verification and Validation

- **Verification:** Did we build the software according to its requirements, contracts, and design?
- **Validation:** Does the resulting software solve the intended problem safely and usefully?

Both are required. Conformance without user value is insufficient; user value without controlled conformance is unsafe.

### Test Basis

The test basis is the approved source used to determine expected behaviour: requirements, examples, contracts, design, policies, risk controls, and accepted product decisions.

### Test Oracle

A test oracle determines the expected result. It may be an explicit requirement, model, invariant, trusted calculation, reference system, or approved expert judgement.

### Coverage

Coverage describes what has been exercised or evaluated. Code coverage is one signal, not proof of meaningful behaviour coverage.

Useful coverage views include:

- Requirements and acceptance criteria.
- Risks and failure modes.
- States, transitions, rules, and boundaries.
- Components, contracts, integrations, and platforms.
- Data classes, permissions, and quality attributes.

### Determinism and Repeatability

Deterministic tests produce the same result under the same controlled conditions. Tests involving time, concurrency, networks, randomness, or external services require explicit control or tolerances.

### Test Independence

Independence reduces shared assumptions. The required degree depends on risk and can range from author verification to qualified specialist assessment.

### False Positives and False Negatives

- A false positive reports failure when the product is correct.
- A false negative reports success when the product is incorrect.

Both reduce trust. Test quality includes the ability to detect real problems without generating misleading noise.

### Shift Left and Shift Right

- **Shift left:** verify earlier through requirements examples, design analysis, static checks, and implementation tests.
- **Shift right:** validate safely in realistic delivery and operational conditions through canaries, observability, experiments, and production feedback.

Neither removes the need for governed pre-release testing.

## 13. Testing Decision Framework

### Scope Decision

Ask:

1. What changed directly?
2. What can change indirectly through dependencies, data, configuration, or shared infrastructure?
3. Which users and business outcomes could be affected?
4. What is the worst credible failure?
5. How detectable and reversible is it?
6. Which evidence would materially reduce uncertainty?

### Technique Decision

| Need | Preferred Approach |
|---|---|
| Fast isolated logic feedback | Unit or component tests |
| Contract and boundary confidence | Contract and integration tests |
| End-to-end user outcome | System or end-to-end tests |
| Unknown or emergent behaviour | Exploratory testing |
| Repeated stable verification | Automation |
| Perception, usability, or complex visual behaviour | Qualified human evaluation plus objective checks |
| Capacity and latency | Performance testing |
| Abuse and control failure | Security testing |
| Inclusive use | Accessibility testing |
| Failure and recovery | Resilience and recovery testing |

### Exit Decision

| Decision | Meaning |
|---|---|
| Pass | Required scope and exit criteria are satisfied; no unresolved blocking defect |
| Pass with Conditions | Policy permits exit with explicit conditions, authority, owner, and expiry |
| Fail | Required evidence or criteria are not satisfied, or risk is unacceptable |
| Escalate | A product, architecture, compliance, or risk authority must decide |

Testing may recommend release readiness. Deployment authority makes the release decision.

## 14. Deliverables

| Deliverable | Minimum Content |
|---|---|
| Test Plan | Scope, basis, risk, approach, levels, owners, environment, data, criteria |
| Coverage Map | Requirement and risk links to planned and executed tests |
| Test Cases or Charters | Preconditions, actions, data, expected results, evidence |
| Environment Record | Version, configuration, dependencies, differences, readiness |
| Test Data Record | Source, classification, controls, reset, retention |
| Execution Results | Revision, environment, outcome, evidence, exceptions |
| Defect Records | Reproduction, expected/actual, impact, severity, priority, owner |
| Regression Report | Scope, results, exclusions, instability, residual risk |
| Test Summary Report | Planned versus executed scope, results, defects, recommendation |
| Deployment Handoff | Tested candidate, conditions, known limitations, checks, rollback notes |

Deliverables may be separate records or governed sections of one system, provided ownership, traceability, and retention remain clear.

## 15. Quality Gates

### Gate A: Test Readiness

- Entry criteria are satisfied.
- Scope, risk, ownership, environment, data, and evidence expectations are defined.

### Gate B: Design Adequacy

- Requirements and material risks map to tests.
- Positive, negative, boundary, failure, recovery, and quality-attribute cases are proportionate.

### Gate C: Execution Integrity

- Results identify revision, environment, data, and evidence.
- Failures, skips, flakes, exclusions, and inconclusive outcomes are visible.

### Gate D: Defect and Regression Control

- Blocking defects are resolved or escalated.
- Fixes are verified and impacted regression is complete on the current candidate.

### Gate E: Test Exit

- Planned versus executed scope is reconciled.
- Residual risk, limitations, conditions, and recommendation are explicit.
- Deployment receives a complete handoff.

Failure of a gate stops progression unless authorised tailoring records the omitted control and compensating action.

## 16. Testing Checklist

### Before Testing

- [ ] Confirm test basis, revision, scope, risks, and owners.
- [ ] Confirm environments, dependencies, access, observability, and data controls.
- [ ] Review Code Review conditions and known limitations.
- [ ] Define exit, suspension, and resumption criteria.

### During Testing

- [ ] Execute against the recorded baseline.
- [ ] Capture objective evidence and unexpected observations.
- [ ] Separate product, test, environment, and data failures.
- [ ] Record skips, flakes, exclusions, and inconclusive results.
- [ ] Escalate safety, security, privacy, and integrity risks promptly.

### Before Exit

- [ ] Verify fixes and impacted regression on the current candidate.
- [ ] Reconcile coverage and defect disposition.
- [ ] Record residual risk, conditions, limitations, and ownership.
- [ ] Prepare the Test Summary Report and Deployment handoff.

## 17. AI-Assisted Testing

All AI-assisted testing follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

AI may assist with:

- Deriving candidate cases from requirements and designs.
- Identifying boundaries, combinations, and failure modes.
- Generating synthetic test data.
- Drafting test code, fixtures, mocks, and exploratory charters.
- Summarising results and clustering similar failures.
- Suggesting regression scope from change information.
- Reviewing traceability and missing coverage.

Engineers must:

- Protect source code, credentials, personal data, client data, and proprietary context.
- Validate every generated case, oracle, assertion, script, and summary.
- Check for invented requirements and self-confirming tests.
- Ensure generated data is lawful and representative.
- Independently reproduce material AI-identified defects.
- Retain human authority for defect closure, exit decisions, and risk acceptance.

AI-generated volume is not coverage. A small set of risk-relevant tests is more valuable than many redundant cases.

## 18. Testing Governance

Testing governance requires:

- A named owner and defined decision authorities.
- Risk-proportionate scope, independence, and specialist involvement.
- Approved test basis and controlled changes to expected results.
- Traceability across requirements, tests, defects, results, and release candidates.
- Reproducible evidence tied to exact revisions and environments.
- Transparent treatment of skips, flakes, exclusions, and inconclusive results.
- Separation between test recommendation, business acceptance, and deployment authority.
- Retention and access consistent with contractual, legal, security, and organisational policy.

### Changes During Testing

Any material change to the candidate, requirements, design, configuration, environment, data, or expected result must trigger impact analysis and proportionate re-testing.

Expected results must not be changed merely to make a failing test pass.

### Exceptions

Exceptions require:

- Scope and rationale.
- Risk and affected evidence.
- Compensating control.
- Named authority and owner.
- Expiry, follow-up, or removal condition.

## 19. Risk Management

### Testing Risks

| Risk | Consequence | Control |
|---|---|---|
| Inadequate scope | Important behaviour remains unverified | Requirement and risk traceability |
| Unrealistic environment | Results do not represent release conditions | Record differences and use production-like controls |
| Poor test data | Critical classes and privacy risks are missed | Governed data design and review |
| Flaky automation | Teams ignore failures or waste investigation time | Quarantine with owner and deadline; fix root cause |
| False oracle | Incorrect behaviour is accepted | Review expected results against approved basis |
| Excessive mocking | Integration failures remain hidden | Balance isolated and real-boundary tests |
| Environment contamination | Results become non-repeatable | Reset, isolation, and baseline checks |
| Confirmation bias | Tests prove the implementation rather than the requirement | Independent design and exploratory testing |
| Late specialist testing | Security, accessibility, or performance failures arrive too late | Plan specialists from risk analysis |
| Coverage theatre | Metrics appear strong while important risk is untested | Combine multiple coverage views with outcomes |

### Risk-Based Prioritisation

Prioritise using:

- Failure impact.
- Failure likelihood.
- Exposure and frequency.
- Detectability.
- Reversibility and recovery time.
- Change size and novelty.
- Dependency and data reach.
- Defect history.
- Regulatory, contractual, security, and safety obligations.

Risk determines depth and sequence; it does not justify silently omitting mandatory controls.

## 20. Test Levels and Test Types

### Test Levels

| Level | Focus |
|---|---|
| Unit | Small logic units and invariants in isolation |
| Component | A deployable or cohesive component through its public boundary |
| Contract | Compatibility between consumers and providers |
| Integration | Interaction among real components, services, data stores, or infrastructure |
| System | Behaviour of the assembled system against requirements |
| End-to-End | Critical user or business journeys across the delivery chain |
| Acceptance | Fitness for agreed business outcomes under authorised ownership |

### Functional Test Types

- Positive and negative scenarios.
- Boundary and equivalence testing.
- Decision-table and state-transition testing.
- API, UI, workflow, and data validation.
- Smoke, sanity, exploratory, and regression testing.

### Non-Functional Test Types

- Security and privacy.
- Performance, capacity, scalability, and endurance.
- Reliability, resilience, recovery, and failover.
- Accessibility and compatibility.
- Installation, migration, rollback, and configuration.
- Observability, auditability, and operability.

### Selection Principles

- Test behaviour at the lowest level that provides credible evidence.
- Do not force all confidence through slow end-to-end tests.
- Do not use isolated tests to claim integration or user-journey confidence.
- Automate stable, repeatable, high-value verification.
- Preserve human exploration for ambiguity, perception, and emergent risk.

## 21. Defect Management

### Defect Record

Each material defect should include:

- Identifier and concise title.
- Tested revision, environment, configuration, and data.
- Preconditions and reproduction steps.
- Expected and actual behaviour.
- Evidence and frequency.
- Requirement, design, risk, and test links.
- Impact, severity, priority, owner, and status.
- Workaround, release effect, and resolution evidence.

### Severity and Priority

Severity describes impact; priority describes when the organisation should act. They must be recorded separately.

| Severity | General Meaning |
|---|---|
| Critical | Catastrophic safety, security, privacy, integrity, legal, or availability impact; no acceptable workaround |
| High | Major requirement failure or serious user/system impact |
| Medium | Material but contained impact with a viable workaround |
| Low | Limited impact that does not prevent intended use |

Organisation-specific thresholds belong in a future approved severity reference.

### Defect Lifecycle

```text
Observed → Reproduced → Triaged → Assigned → Resolved
    → Ready for Verification → Verified → Closed
                         └──────────────→ Reopened
```

### Closure Rules

- Closure requires evidence on the current revision.
- “Cannot reproduce” requires documented attempts and environment details.
- Duplicate status must link the controlling record.
- Deferred defects require risk acceptance, owner, target, and visibility in the release decision.
- Test defects and environment defects must be fixed and tracked; they are not product passes.

## 22. Testing Standards Integration

This playbook governs the testing process.

Existing authorities:

- [`PB-AUTHORING`](../03-standards/PB-AUTHORING.md) governs playbook structure.
- [`STD-TRACEABILITY`](../03-standards/STD-TRACEABILITY.md) governs evidence relationships.
- [`STD-METADATA`](../03-standards/STD-METADATA.md) governs document metadata.
- [`STD-VERSIONING`](../03-standards/STD-VERSIONING.md) governs document evolution.
- [`TERM-STANDARD`](../03-standards/TERM-STANDARD.md) and [`DOC-STYLE`](../03-standards/DOC-STYLE.md) govern terminology and style.

Planned specialised authorities may later define:

- Testing standards and automation-code conventions.
- Security, performance, accessibility, and test-data controls.
- Defect severity and priority models.
- Framework, tool, environment, and reporting practices.

Until approved, planned artefacts are not authoritative. Teams must use project-specific, reviewed conventions that do not conflict with this playbook or existing standards.

## 23. Common Mistakes

- Testing only the happy path.
- Deriving expected results from the implementation instead of the test basis.
- Treating code coverage as proof of quality.
- Automating unstable or low-value scenarios without a maintenance plan.
- Relying entirely on end-to-end tests.
- Mocking away the integrations that carry the highest risk.
- Using production personal data without explicit controls.
- Ignoring flaky, skipped, quarantined, or inconclusive tests.
- Changing expected results to match defects.
- Closing defects without verifying the current revision.
- Re-running only the failed test after a broad fix.
- Treating testers as a downstream quality gate rather than engineering partners.
- Reporting pass rates without scope, exclusions, and risk.
- Using AI-generated cases or assertions without human verification.
- Allowing a test pass to become implicit deployment approval.

## 24. Best Practices

- Start from user outcomes, requirements, and risks.
- Design for testability before implementation.
- Keep tests focused, readable, deterministic, and independent.
- Use stable public behaviour rather than incidental implementation detail.
- Control time, randomness, concurrency, networks, and external dependencies.
- Use production-like boundaries where integration risk matters.
- Make failures diagnostic and evidence easy to reproduce.
- Keep test data minimal, representative, lawful, and resettable.
- Review test code with production-code discipline.
- Run fast checks early and expensive checks when risk justifies them.
- Convert escaped defects into durable regression protection.
- Track and remove flakes rather than normalising them.
- Use metrics to improve the system, not rank individuals.
- Preserve explicit human decisions at test exit.

## 25. Templates

### Test Plan

```markdown
# Test Plan

## Target and Revision
## Test Basis
## Scope and Exclusions
## Risk Assessment
## Test Levels and Types
## Environments and Dependencies
## Test Data and Privacy
## Roles and Independence
## Entry, Suspension, Resumption, and Exit Criteria
## Evidence and Traceability
## Schedule and Constraints
```

### Test Case

```markdown
**ID:**
**Requirement/Risk:**
**Objective:**
**Preconditions:**
**Data:**
**Steps:**
**Expected Result:**
**Evidence:**
**Automation Status:**
```

### Defect Report

```markdown
**ID and title:**
**Revision/environment:**
**Preconditions/data:**
**Steps to reproduce:**
**Expected behaviour:**
**Actual behaviour:**
**Evidence/frequency:**
**Impact/severity/priority:**
**Requirement and test links:**
**Owner/status:**
```

### Test Summary Report

```markdown
# Test Summary Report

## Candidate and Environment
## Planned and Executed Scope
## Results and Evidence
## Defect Disposition
## Regression Outcome
## Exclusions and Limitations
## Residual Risk and Conditions
## Test Exit Decision
## Deployment Recommendation
```

## 26. Examples

### Example: Risk-Based Scope

A change adds a discount rule to one service but affects order totals, tax, payment authorisation, refunds, invoices, reporting, and customer messages.

The team tests the rule at unit level, contracts at integration level, critical purchase and refund journeys at system level, and targeted regression across financial outputs. It does not equate the small code diff with low business risk.

### Example: False Confidence

An API has 95% line coverage, but every test uses an administrator identity and valid payload.

Testing adds permission, invalid-state, boundary, concurrency, idempotency, and failure-recovery cases. Coverage percentage changes little, while meaningful confidence increases substantially.

### Example: Defect Verification

A timeout fix changes retries across a shared client.

The tester reproduces the original timeout, verifies the fixed call, checks retry limits and duplicate side effects, then runs regression for all consumers of the shared client before closing the defect.

### Example: Conditional Exit

A low-frequency browser rendering defect remains on a non-critical internal page. Policy permits conditional exit.

The Test Owner records affected users, workaround, evidence, owner, target release, monitoring, expiry, and authorised risk acceptance. Deployment still decides whether to release.

## 27. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Architecture Principles](../01-principles/03-architecture-principles.md)
- [Coding Principles](../01-principles/04-coding-principles.md)
- [Testing Principles](../01-principles/05-testing-principles.md)
- [Security Principles](../01-principles/06-security-principles.md)
- [Observability Principles](../01-principles/07-observability-principles.md)
- [Performance Principles](../01-principles/08-performance-principles.md)

## 28. Related Standards

- [Playbook Authoring Standard](../03-standards/PB-AUTHORING.md)
- [Engineering Traceability Standard](../03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](../03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](../03-standards/STD-VERSIONING.md)
- [Engineering Terminology Standard](../03-standards/TERM-STANDARD.md)
- [Documentation Style Guide](../03-standards/DOC-STYLE.md)
- Testing, security, and documentation implementation standards are planned and non-authoritative.

## 29. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)
- Test-level, defect-severity, and test-data references are planned and non-authoritative.

## 30. Related Playbooks

- [Code Review Playbook](PB-CODE-REVIEW.md) supplies the reviewed revision and known conditions.
- [Coding Playbook](PB-CODING.md) supplies implementation tests and technical evidence.
- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted testing.
- [Requirements Playbook](PB-REQ.md) supplies outcomes and acceptance criteria.
- [Architecture Playbook](PB-ARCH.md) supplies quality attributes and system boundaries.
- [Technical Design Playbook](PB-TECH-DESIGN.md) supplies contracts, data, errors, and operational design.
- [Debugging Playbook](08-debugging-playbook.md) governs systematic defect diagnosis.
- [Security Playbook](09-security-playbook.md) will govern broader security assessment.
- [Deployment Playbook](12-deployment-playbook.md) consumes the test recommendation and governs release.
- [Observability Playbook](10-observability-playbook.md) will govern operational evidence.

## 31. Metrics

Use metrics to improve confidence and flow, not to rank individuals or reward test volume.

| Metric | What It Reveals | Guardrail |
|---|---|---|
| Requirement and risk coverage | Planned verification breadth | Review quality, not percentage alone |
| Test pass rate | Outcome within executed scope | Always show skips, exclusions, and inconclusive tests |
| Defect discovery by phase | Where feedback arrives | More early defects may indicate stronger testing |
| Escaped defect rate | Important failures missed before release | Segment by cause, severity, and detectability |
| Defect reopen rate | Fix or verification quality | Distinguish product, test, and environment causes |
| Mean time to verify | Flow from fix to evidence | Do not optimise speed at the expense of scope |
| Regression duration and stability | Delivery feedback quality | Track flakes and queue delay separately |
| Automation coverage | Repeatable verification | Measure valuable scenarios, not raw case count |
| Flaky test rate and age | Trust and maintenance debt | Require owner and remediation deadline |
| Environment failure rate | Evidence reliability | Separate infrastructure from product outcomes |
| Residual-risk recurrence | Effectiveness of accepted conditions | Review expired and repeated exceptions |

Do not use test count, coverage percentage, pass rate, or defects per tester as individual performance targets.

## 32. Reference Implementation and Enterprise Appendices

`PB-TESTING` is the reference implementation for governed verification and validation playbooks.

### 32.1 Testing Readiness Checklist

- [ ] Reviewed revision and test basis are stable and linked.
- [ ] Scope, risks, owners, specialists, environments, and data are ready.
- [ ] Entry, suspension, resumption, and exit criteria are explicit.
- [ ] Required tools, access, observability, and baseline suites pass.
- [ ] Known limitations and Code Review conditions are visible.

### 32.2 Test Plan Template

| Field | Required Content |
|---|---|
| Target | Product, change, revision, release candidate |
| Basis | Requirements, design, contracts, risks |
| Scope | Levels, types, platforms, exclusions |
| Approach | Techniques, automation, exploration, specialists |
| Resources | Owners, environment, data, tools |
| Control | Entry, suspension, resumption, exit |
| Evidence | Results, traceability, retention, reporting |

### 32.3 Test Case Template

- Identifier and objective.
- Requirement or risk link.
- Preconditions and controlled data.
- Actions and expected outcomes.
- Evidence and result.
- Automation status and owner.
- Revision and environment.

### 32.4 Defect Report Template

- Reproducible steps and frequency.
- Expected and actual behaviour.
- Revision, environment, configuration, and data.
- Evidence and affected requirement.
- Severity, priority, release impact, and owner.
- Resolution, verification, and closure evidence.

### 32.5 Regression Checklist

- [ ] Change and dependency impact analysis completed.
- [ ] Original failure and nearby boundaries retested.
- [ ] Required automated suites pass on the current candidate.
- [ ] Contracts, data, configuration, migration, and rollback are covered.
- [ ] High-risk interactions receive exploratory regression.
- [ ] Flakes, skips, exclusions, and limitations are recorded.

### 32.6 Test Exit Criteria Checklist

- [ ] Required scope and specialist evidence are complete.
- [ ] Blocking defects are resolved or formally escalated.
- [ ] Fix verification and regression are complete.
- [ ] Planned versus executed coverage is reconciled.
- [ ] Residual risk, conditions, and limitations are authorised.
- [ ] Test Summary Report and Deployment handoff are complete.

### 32.7 Test Traceability Matrix

| Source | Test | Result | Defect | Exit Disposition |
|---|---|---|---|---|
| Requirement, risk, design, contract, or control | Case, suite, or charter | Pass, fail, blocked, skipped, inconclusive | Linked record or none | Satisfied, conditioned, failed, escalated |

Traceability must identify the tested revision and environment.

### 32.8 Testing Maturity Model

| Level | Characteristics |
|---|---|
| 1. Reactive | Testing occurs late; evidence and ownership are inconsistent |
| 2. Repeatable | Basic plans, cases, defects, and regression exist |
| 3. Governed | Risk, traceability, environments, data, and exit criteria are controlled |
| 4. Measured | Quality, flow, flakes, escapes, and systemic gaps drive improvement |
| 5. Adaptive | Continuous evidence, production feedback, and learning optimise confidence |

### 32.9 Risk-Based Testing Matrix

| Impact / Likelihood | Low | Medium | High |
|---|---|---|---|
| Low impact | Focused checks | Targeted regression | Expanded component and integration |
| Medium impact | Targeted regression | Full impacted scope | Independent and specialist testing |
| High impact | Independent verification | Production-like failure testing | Formal strategy, specialists, recovery, and authority |

Regulatory, security, privacy, safety, and contractual obligations can override the matrix.

### 32.10 Automation Decision Matrix

| Characteristic | Automate | Retain Human-Led |
|---|---|---|
| Frequent, stable, deterministic, objective | Yes | As supplementary exploration |
| High-volume combinations or data | Yes | Review model and oracle |
| Rare, rapidly changing, subjective | Selectively | Usually |
| Visual, usability, accessibility perception | Objective checks | Qualified human judgement |
| Destructive or expensive environment action | Only with strong controls | Governed execution |

Automation requires an owner, diagnostic failures, maintainability, and retirement criteria.

### 32.11 Deliverables Checklist

- [ ] Test Plan and risk model.
- [ ] Cases, charters, data, and environment records.
- [ ] Coverage and traceability.
- [ ] Execution results and evidence.
- [ ] Defect records and verification.
- [ ] Regression report.
- [ ] Test Summary Report.
- [ ] Deployment handoff.

### 32.12 Release Recommendation Checklist

- [ ] Exact candidate, configuration, and environment are identified.
- [ ] Required gates and exit criteria are satisfied.
- [ ] Known defects, exclusions, limitations, and residual risks are explicit.
- [ ] Conditions have authority, owner, expiry, and monitoring.
- [ ] Smoke, rollback, recovery, and production verification needs are stated.
- [ ] Business acceptance and deployment authority are identified separately.
- [ ] Recommendation is Pass, Pass with Conditions, Fail, or Escalate.

## 33. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Testing Playbook with eight-phase verification workflow, risk-based scope, test and defect governance, five quality gates, AI controls, metrics, and twelve enterprise appendices |

## 34. Summary

`PB-TESTING` governs how Invara Labs verifies and validates software.

It requires teams to:

- Plan from requirements, design, risk, and user outcomes.
- Create controlled, representative, and traceable tests.
- Execute against an identifiable revision and environment.
- Report defects with reproducible evidence.
- Verify fixes and proportionate regression.
- Make a transparent test-exit decision.
- Hand tested software, evidence, conditions, and residual risk to Deployment.

Testing provides evidence of readiness. It does not replace engineering quality, business acceptance, risk ownership, or deployment authority.
