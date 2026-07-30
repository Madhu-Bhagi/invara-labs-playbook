---
title: Code Review Playbook
id: PB-CODE-REVIEW
version: 1.0.2
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
  - code-review
  - peer-review
  - engineering
  - quality
  - governance
  - playbook
related:
  - PB-CODING
  - PB-TESTING
  - PB-DEPLOYMENT
  - PB-AI-ENGINEERING
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

# Code Review Playbook

> **The standard operating procedure for reviewing software changes to ensure correctness, maintainability, security, performance, and readiness for integration into the product.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. Code Review Workflow
10. Review Lifecycle
11. Detailed Phase Activities
12. Review Concepts
13. Review Decision Framework
14. Deliverables
15. Quality Gates
16. Review Checklist
17. AI-Assisted Review
18. Review Governance
19. Risk Management
20. Security Review
21. Reviewer Accountability
22. Review Standards Integration
23. Review Findings Classification
24. Common Mistakes
25. Best Practices
26. Templates
27. Examples
28. Related Principles
29. Related Standards
30. Related References
31. Related Playbooks
32. Metrics
33. Reference Implementation and Enterprise Appendices
34. Revision History
35. Summary

## 1. Overview

Code review is an independent engineering verification activity performed before a software change is accepted into a shared product baseline.

It is not:

- A tutorial for a particular pull-request platform.
- A formatting debate.
- A substitute for author self-review or automated validation.
- A guarantee that no defects remain.
- Permission to redesign approved architecture through comments.
- A performance assessment of the author.

Code review consumes the review-ready package produced by `PB-CODING`. It verifies that the implemented change:

- Satisfies requirements and approved technical design.
- Preserves architecture, contracts, data integrity, and ownership.
- Is correct across normal, boundary, failure, and recovery behaviour.
- Is secure, maintainable, testable, observable, and proportionate.
- Has credible evidence and traceability.
- Can proceed to broader verification under `PB-TESTING`.

```text
Review-Ready Change
        │
        ▼
PB-CODE-REVIEW
        │
        ▼
Reviewed Change
        │
        ▼
PB-TESTING
```

Approval means the required reviewers found no unresolved blocking issue within the defined review scope. It does not approve production deployment.

## 2. Purpose

This playbook helps teams:

- Verify implementation correctness and completeness.
- Detect defects while changes remain inexpensive to correct.
- Preserve architecture and technical-design intent.
- Evaluate security, data, performance, reliability, and operational risk.
- Improve readability, maintainability, testability, and ownership.
- Apply review effort proportionate to change risk.
- Provide objective, respectful, actionable feedback.
- Resolve disagreements through evidence and authority.
- Preserve findings, decisions, approvals, and traceability.
- Share system knowledge without turning review into informal training.
- Produce a reliable handoff to Testing.

## 3. Objectives

Following this playbook should produce:

- A verified review scope and baseline.
- Appropriate independent and specialist reviewers.
- Evidence-based functional, architecture, security, and maintainability evaluation.
- Classified, actionable review findings.
- Updated implementation and validation evidence.
- Recorded resolution of blocking and conditional findings.
- A human approval, rejection, revision, or escalation decision.
- Traceability from requirements and design through review.
- A reviewed change ready for the next verification stage.

The objective is not comment volume or rapid approval. It is an efficient, defensible quality decision.

## 4. Scope

### In Scope

Apply this playbook to review of:

- Product features and enhancements.
- Defect and root-cause fixes.
- Refactoring and technical-debt changes.
- APIs, integrations, services, modules, libraries, and user interfaces.
- Data schemas, migrations, queries, and transformations.
- Configuration, build, automation, CI/CD, and infrastructure definitions.
- Security, performance, reliability, and observability changes.
- Implementation-affecting documentation.
- Hotfixes and emergency changes through proportionate expedited controls.

### Proportionate Review

| Change Profile | Expected Review |
|---|---|
| Small, local, reversible | Qualified peer, focused evidence, normal automated gates |
| Material feature, contract, or integration | Code owner plus domain reviewers, full package and traceability |
| High-risk security, data, infrastructure, regulated, or cross-team | Independent specialists, formal findings, stronger evidence and approval |
| Emergency change | Minimum safe independent review, explicit authority, post-change follow-up |

### Out of Scope

This playbook does not:

- Approve requirements, architecture, or technical design.
- Replace author self-review, automated tests, security testing, or system testing.
- Define programming-language or framework standards.
- Authorise production deployment.
- Accept business, security, privacy, legal, or operational risk outside reviewer authority.
- Require all reviewers to inspect every concern when ownership is explicitly divided.

## 5. When to Use This Playbook

Use this playbook before a governed software change is merged, integrated, promoted as a release candidate, or otherwise accepted into a shared baseline.

Use it for:

- Pull requests and merge requests.
- Changes submitted through another governed review mechanism.
- Release and maintenance branches.
- Hotfix and emergency patches.
- Infrastructure and configuration changes.
- Generated, vendored, AI-assisted, or externally contributed code.

Re-enter review when:

- The author changes material behaviour after approval.
- Testing reveals an implementation defect.
- A dependency, migration, contract, security control, or design assumption changes.
- A resolved finding introduces significant new code.

Return upstream when a finding exposes an unresolved requirement, architecture, or technical-design decision.

## 6. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| Author | Provides review-ready work, context, evidence, responses, revisions, and ownership |
| Primary Reviewer | Evaluates the complete change, records findings, verifies resolution, and recommends disposition |
| Code Owner | Protects owned components, contracts, conventions, compatibility, and long-term maintainability |
| Architecture or Design Owner | Evaluates design alignment and material deviation |
| Security or Privacy Reviewer | Evaluates trust boundaries, controls, dependencies, data handling, and residual risk |
| Data Owner | Evaluates schema, integrity, transaction, migration, retention, recovery, and access |
| Quality Engineer | Evaluates test strategy, independence, coverage, and downstream verification needs |
| Platform or Operations Reviewer | Evaluates build, infrastructure, configuration, deployment, observability, and recovery |
| Approver | Makes the final review decision within delegated authority |
| Moderator or Engineering Lead | Resolves deadlock, ensures proportionality, and escalates authority or risk |

### Responsibility Rules

- Authors remain accountable for implementation quality.
- Reviewers are accountable for performing the agreed review scope diligently.
- Approval authority must match risk and ownership.
- High-risk changes require independence and relevant expertise.
- A reviewer may approve only concerns within their competence and authority.
- AI may assist under `PB-AI-ENGINEERING`; it cannot approve or accept risk.

## 7. Inputs

| Input | Required Information |
|---|---|
| Review package | Why, what, how, scope, exclusions, reviewer focus, rollout, rollback |
| Submitted revision | Stable commit or revision identifier and complete diff |
| Requirements | Intended behaviour, acceptance criteria, priorities, and traceability |
| Architecture and technical design | Boundaries, contracts, decisions, constraints, risks, and quality thresholds |
| Validation evidence | Build, static analysis, tests, security checks, migration rehearsal, benchmarks |
| Implementation artefacts | Code, tests, configuration, migrations, infrastructure, documentation, dependencies |
| Ownership data | Author, code owners, domain specialists, approver, and escalation path |
| Risk information | Security, data, compatibility, performance, operational, customer, and rollback impact |
| Applicable standards | Approved coding, security, API, logging, testing, documentation, and repository rules |

Reviewers inspect authoritative sources rather than relying only on the author's summary.

## 8. Entry Criteria

Before formal review begins:

- The change is marked ready, not known-incomplete.
- The author completed self-review.
- Scope and acceptance criteria are clear.
- Required design and decision links are available.
- The diff is focused and commits are understandable.
- Baseline build and required automated checks pass, or exceptions are authorised and visible.
- Tests, configuration, migrations, infrastructure, and documentation are included as applicable.
- Risks, rollout, rollback, and known limitations are disclosed.
- Required reviewers and owners are identifiable.
- The submitted revision is stable enough to review.

If these criteria fail, return the package to the author as Not Ready rather than spending review effort reconstructing missing context.

## 9. Code Review Workflow

| Phase | Objective | Exit Decision |
|---|---|---|
| 1. Prepare the Review | Confirm readiness, scope, risk, authority, evidence, and review plan | Is the package ready for meaningful review? |
| 2. Functional Review | Verify intended behaviour, business rules, contracts, failures, and tests | Is the implementation functionally credible? |
| 3. Architecture and Design Review | Verify boundaries, decisions, dependencies, data, and design integrity | Does implementation preserve approved design? |
| 4. Security and Operational Review | Evaluate security, privacy, dependencies, performance, reliability, and operability | Are cross-cutting risks acceptably controlled? |
| 5. Maintainability Review | Evaluate clarity, focus, reuse, complexity, testability, and ownership | Can the change be understood and evolved safely? |
| 6. Provide and Resolve Feedback | Classify findings, discuss evidence, revise, and escalate | Are required changes and decisions explicit? |
| 7. Verify Updates | Re-review changed areas and repeat affected evidence | Are findings resolved without regression? |
| 8. Approve, Reject, or Escalate | Make and record the human review decision | May the change proceed to Testing or integration? |

```text
Review Request
      │
      ▼
Prepare and Scope
      │
      ▼
Functional Review
      │
      ▼
Architecture and Design Review
      │
      ▼
Security and Operational Review
      │
      ▼
Maintainability Review
      │
      ▼
Findings and Discussion
      │
      ▼
Author Updates
      │
      ▼
Verification
      │
      ▼
Approve / Reject / Escalate
```

Review concerns may run in parallel when ownership is clear. The approval decision waits for all required scopes.

## 10. Review Lifecycle

```text
Requested
    │
    ▼
Ready for Review
    │
    ▼
Under Review
    │
    ▼
Changes Requested
    │
    ▼
Reverification
    │
    ▼
Approved / Rejected / Escalated
    │
    ▼
Merged or Handed to Testing
```

A material change after approval invalidates affected approval and evidence. The author must notify reviewers and request re-review.

Approval history belongs to the governed review system. Chat messages and undocumented verbal approval do not replace the record.

## 11. Detailed Phase Activities

### Phase 1: Prepare the Review

**Objective:** Establish a review plan proportionate to the change.

**Activities:**

1. Verify entry criteria and submitted revision.
2. Read the review package, requirements, design, decisions, and risk notes.
3. Inspect change size, affected components, owners, contracts, data, dependencies, and operational impact.
4. Select primary, code-owner, and specialist reviewers.
5. Divide review concerns without creating gaps.
6. Identify automated evidence and manual analysis required.
7. Return Not Ready packages promptly with specific missing prerequisites.

**Outputs:**

- Review scope and baseline.
- Reviewer assignments.
- Risk-based review plan.

**Exit criteria:**

- Required context and evidence are available.
- Review ownership and authority are clear.
- The package is ready for substantive review.

### Phase 2: Functional Review

**Objective:** Verify the implementation expresses the intended behaviour.

**Activities:**

1. Trace code paths to requirements and acceptance criteria.
2. Evaluate business rules, invariants, calculations, state transitions, and side effects.
3. Inspect normal, boundary, invalid, duplicate, concurrent, failure, and recovery behaviour.
4. Verify interface semantics, errors, compatibility, idempotency, ordering, retries, and timeouts.
5. Assess whether tests derive from requirements and risks.
6. Look for missing behaviour, accidental behaviour, unreachable code, and incorrect assumptions.
7. Reproduce or run focused evidence when uncertainty is material.

**Outputs:**

- Functional findings.
- Test-gap findings.
- Functional readiness assessment.

**Exit criteria:**

- Intended behaviour is represented.
- Material functional gaps are classified.
- Evidence is adequate for the reviewed risk.

### Phase 3: Architecture and Design Review

**Objective:** Ensure implementation preserves approved structural and technical intent.

**Activities:**

1. Compare boundaries, responsibilities, dependencies, and ownership with architecture and TDD.
2. Review contracts, schemas, data flows, sequences, and state.
3. Detect hidden coupling, duplicated capability, bypassed abstractions, and architectural drift.
4. Verify use of existing suitable components and patterns.
5. Evaluate migration, coexistence, compatibility, rollback, and reversibility.
6. Identify decisions that require design clarification or ADR governance.
7. Return material deviations upstream rather than approving them through code review.

**Outputs:**

- Architecture and design findings.
- Deviation or escalation record.
- Alignment assessment.

**Exit criteria:**

- Implementation conforms to approved design.
- Deviations are resolved or governed upstream.
- Ownership and dependency direction remain coherent.

### Phase 4: Security and Operational Review

**Objective:** Evaluate cross-cutting risks that affect trust and production behaviour.

**Activities:**

1. Inspect validation, authentication, authorisation, ownership, least privilege, and secrets.
2. Review data classification, privacy, logging, errors, audit, retention, and deletion.
3. Review dependencies, packages, licences, build scripts, and supply-chain impact.
4. Evaluate timeouts, retries, idempotency, concurrency, transactions, resource limits, and degradation.
5. Verify logs, metrics, traces, health, alerts, and diagnostic context.
6. Review configuration, migration, rollout, rollback, backup, recovery, and support impact.
7. Require qualified specialist review where risk exceeds general competence.

**Outputs:**

- Security, privacy, data, and operational findings.
- Specialist review requirements.
- Cross-cutting risk assessment.

**Exit criteria:**

- Blocking cross-cutting risks are identified.
- Required specialist scopes are complete.
- Residual risk is owned by authorised humans.

### Phase 5: Maintainability Review

**Objective:** Determine whether future engineers can understand, test, operate, and change the implementation safely.

**Activities:**

1. Evaluate names, structure, control flow, responsibilities, and dependency direction.
2. Identify unnecessary complexity, abstraction, configuration, indirection, and dependencies.
3. Check duplication and opportunities to use existing capabilities.
4. Evaluate test seams, deterministic behaviour, and failure diagnosability.
5. Review comments and documentation for maintained intent rather than restatement.
6. Assess technical debt, ownership, change concentration, and future compatibility.
7. Distinguish mandatory maintainability issues from preference.

**Outputs:**

- Maintainability findings.
- Simplification and ownership recommendations.
- Long-term readiness assessment.

**Exit criteria:**

- Blocking maintainability problems are classified.
- Feedback references outcomes or approved guidance.
- Personal style is not imposed as a requirement.

### Phase 6: Provide and Resolve Feedback

**Objective:** Communicate findings clearly and reach evidence-based resolution.

**Activities:**

1. Classify each finding by type, severity, and blocking status.
2. State location, issue, impact, evidence, and required outcome.
3. Separate required changes, suggestions, questions, and praise.
4. Avoid vague comments, personal language, and unexplained directives.
5. Let the author respond with a fix, clarification, evidence, or escalation.
6. Resolve disagreements through requirements, design, standards, experiments, or decision authority.
7. Track unresolved findings and due conditions.

**Outputs:**

- Findings log.
- Discussion and decision rationale.
- Author revision plan.

**Exit criteria:**

- Every finding has a clear required response.
- Blocking status is unambiguous.
- Disagreements have an owner and resolution path.

### Phase 7: Verify Updates

**Objective:** Confirm agreed corrections are complete and have not introduced regressions.

**Activities:**

1. Inspect all changes since the reviewed baseline.
2. Verify each blocking and conditional finding.
3. Re-run affected builds, tests, analysis, migration, and security evidence.
4. Check whether a local correction moves the problem elsewhere.
5. Identify newly introduced behaviour or scope.
6. Request specialist re-review when their concern changed materially.
7. Update finding states and traceability.

**Outputs:**

- Verified findings.
- Current validation evidence.
- Re-review record.

**Exit criteria:**

- Required findings are resolved.
- Evidence matches the current revision.
- No material unreviewed change remains.

### Phase 8: Approve, Reject, or Escalate

**Objective:** Record a defensible review decision within the reviewers' authority.

**Possible outcomes:**

- **Approved** — all required scopes and gates pass.
- **Approved with Conditions** — only when policy permits and conditions cannot undermine pre-merge safety.
- **Changes Requested** — correctable blocking findings remain.
- **Rejected** — the approach is unsuitable or requires substantial rework.
- **Escalated** — authority, design, risk, or disagreement exceeds the review.

**Activities:**

1. Confirm required reviewer decisions and automated gates.
2. Review unresolved findings, exceptions, and residual risks.
3. Confirm approval applies to the current revision.
4. Record decision, reviewers, date, conditions, and downstream needs.
5. Hand the reviewed change and evidence to Testing or integration.

**Outputs:**

- Review decision.
- Approval and condition record.
- Reviewed change and downstream handoff.

**Exit criteria:**

- The decision and authority are explicit.
- Blocking findings are resolved.
- Downstream Testing receives current artefacts and known risks.

## 12. Review Concepts

### Independent Review

Independence means the reviewer can challenge the work without merely confirming their own implementation. Required independence increases with risk.

### Review Scope

A review scope identifies concerns, artefacts, baseline, reviewers, evidence, and exclusions. Dividing scopes is acceptable only when their union covers the change.

### Review Baseline

Approval applies to an immutable revision. Material changes after review require affected re-review.

### Finding

A finding records a specific issue or question with location, impact, evidence, severity, blocking status, owner, and resolution.

### Blocking Finding

A blocking finding prevents approval because correctness, safety, required quality, or governing authority is not satisfied.

### Suggestion

A suggestion is non-blocking. It may improve the change but does not represent a required quality failure.

### Review Evidence

Evidence includes code analysis, requirements, design, standards, tests, builds, static checks, benchmarks, migration results, or controlled experiments.

### Approval

Approval is a human decision that the current revision meets required review scopes. It is not authorship transfer, risk acceptance beyond authority, or deployment approval.

## 13. Review Decision Framework

For every concern:

1. Identify the required outcome or risk.
2. Locate evidence in requirements, design, code, standards, or behaviour.
3. Determine whether the issue is real, material, and within scope.
4. Classify severity and blocking status separately.
5. State the required outcome rather than prescribing one implementation unnecessarily.
6. Escalate decisions outside reviewer authority.
7. Verify the resolution against the current revision.

| Condition | Decision |
|---|---|
| Required scope missing or package incomplete | Not Ready |
| Blocking correctness, security, data, compatibility, or design issue | Changes Requested |
| Approach fundamentally conflicts with approved direction | Reject or return upstream |
| Evidence is disputed and authority unclear | Escalate |
| Only non-blocking suggestions remain | Approve when other gates pass |
| Required scopes and gates pass | Approve current revision |

## 14. Deliverables

| Deliverable | Minimum Content |
|---|---|
| Review Scope | Baseline, concerns, exclusions, reviewers, and authority |
| Findings Log | Location, category, severity, impact, evidence, blocking status, owner, state |
| Review Comments | Clear, respectful, actionable feedback |
| Updated Implementation | Author revisions linked to findings |
| Verification Record | Re-review and affected validation evidence |
| Review Decision | Outcome, revision, reviewers, date, conditions, rationale |
| Traceability Update | Links between requirements, design, code, tests, findings, and decision |
| Testing Handoff | Reviewed revision, evidence, residual risks, and test focus |

## 15. Quality Gates

### Gate A: Review Ready

- Entry criteria, revision, context, evidence, scope, owners, and risks are clear.

### Gate B: Correctness Ready

- Functional, contract, architecture, data, and design review identifies no unresolved blocker.

### Gate C: Quality and Risk Ready

- Security, privacy, dependencies, performance, reliability, operations, maintainability, and testability are acceptably addressed.

### Gate D: Findings Resolved

- Blocking findings are fixed or escalated; affected evidence passes on the current revision.

### Gate E: Decision Ready

- Required independent and specialist reviewers have decided; traceability and downstream handoff are complete.

## 16. Review Checklist

### Readiness

- [ ] Package, scope, revision, requirements, design, evidence, and risks are clear.
- [ ] Required owners and specialist reviewers are assigned.

### Correctness and Design

- [ ] Business behaviour, contracts, edge cases, failures, and tests are credible.
- [ ] Architecture, boundaries, data, dependencies, migration, and compatibility are preserved.

### Risk and Quality

- [ ] Security, privacy, dependency, performance, reliability, and operational concerns are addressed.
- [ ] Code is readable, focused, testable, and free of unjustified complexity.
- [ ] Documentation and traceability match implementation.

### Decision

- [ ] Findings are classified, actionable, and resolved.
- [ ] Evidence matches the current revision.
- [ ] Approval authority and downstream handoff are complete.

## 17. AI-Assisted Review

AI may assist with:

- Change summarisation.
- Suspicious-pattern and potential-defect discovery.
- Complexity, duplication, and dependency analysis.
- Test-gap and edge-case suggestions.
- Documentation and traceability checks.
- Review-comment drafting.

All AI-assisted review follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

Reviewers must:

- Use only authorised code and context.
- Treat generated findings as untrusted hypotheses.
- Verify every material claim against code and evidence.
- Avoid delegating complete review scope to AI.
- Detect false positives, omissions, outdated APIs, and fabricated execution.
- Keep the human decision independent and accountable.

AI cannot approve, reject, accept risk, or satisfy required human independence.

## 18. Review Governance

- Every review has a stable revision, named author, required reviewers, and recorded decision.
- Review depth is proportionate to impact, complexity, reversibility, and exposure.
- Required code-owner and specialist scopes cannot be bypassed by general approval.
- Reviewers disclose conflicts of interest or insufficient competence.
- Exceptions and emergency paths are authorised, documented, and followed by required retrospective review.
- Material post-approval changes invalidate affected approval.
- Repeated findings feed Standards, Playbooks, templates, tooling, and training.
- Review records follow retention, confidentiality, and audit requirements.

## 19. Risk Management

| Review Risk | Warning Signal | Treatment |
|---|---|---|
| Superficial review | Fast approval without evidence or findings | Scope checklist and risk-based depth |
| Confirmation bias | Reviewer co-designed or authored the change | Add independent reviewer |
| Context gap | Missing requirements, design, or risk | Return Not Ready |
| Review overload | Large mixed diff | Split change or divide explicit scopes |
| Security blind spot | No qualified reviewer for sensitive change | Specialist review |
| Architecture drift | Local approval changes system direction | Return upstream |
| Stale approval | Code changes after review | Re-review affected areas |
| Preference conflict | Comment lacks outcome or standard | Reclassify as suggestion or provide evidence |
| Rubber stamping | Approval rate is treated as productivity | Measure outcomes, not approvals |
| Review delay | Ownership or priority is unclear | Assign service expectation and escalate |

## 20. Security Review

Security review evaluates:

- Trust boundaries, assets, threats, and abuse cases.
- Input validation, output encoding, authentication, authorisation, and ownership.
- Secrets, cryptography, sessions, tokens, and least privilege.
- Personal, customer, confidential, regulated, and logged data.
- Injection, traversal, request forgery, replay, enumeration, unsafe deserialisation, and resource exhaustion.
- Dependencies, packages, licences, build scripts, and supply chain.
- Error handling, audit, monitoring, failure, and recovery.
- Configuration, infrastructure, network, and environment permissions.

Automated scanners support review but do not replace human threat reasoning. High-risk findings require a qualified security reviewer and authorised risk owner.

## 21. Reviewer Accountability

Reviewers are accountable for:

- Preparing enough to understand their assigned scope.
- Applying evidence and approved guidance rather than preference.
- Identifying material risk and admitting uncertainty.
- Giving respectful, specific, actionable feedback.
- Protecting confidential code and review data.
- Verifying agreed resolutions.
- Approving only the reviewed revision within their competence and authority.
- Escalating unresolved design, security, or organisational decisions.

Authors remain accountable for the implementation. Reviewers share responsibility for the quality of the review decision; approval does not transfer authorship.

## 22. Review Standards Integration

This playbook governs the software code-review process.

`STD-REVIEW` currently governs engineering documentation and explicitly excludes software code review. Its general principles of objectivity, independence, constructive feedback, consistency, traceability, risk-based depth, timeliness, accountability, and proportionality inform this playbook, but it is not the code-review process authority.

Approved Coding, Security, API, Logging, Testing, Documentation, Git, and other Standards define what reviewers must evaluate. Planned standards are non-authoritative until approved.

Review comments should cite an applicable requirement, decision, standard, or observed risk when a change is mandatory.

## 23. Review Findings Classification

Severity describes impact. Blocking status describes whether approval may proceed. They are related but not identical.

| Severity | Meaning | Default Disposition |
|---|---|---|
| Critical | Exploitable security issue, data loss, severe outage, legal breach, or fundamentally incorrect behaviour | Block; urgent resolution and escalation |
| High | Material correctness, security, compatibility, architecture, or operational failure | Block before approval |
| Medium | Real quality defect with bounded impact or likely maintenance/reliability cost | Usually block or require explicit authorised disposition |
| Low | Limited impact, local quality issue, or minor non-compliance | Fix or record proportionate follow-up |
| Suggestion | Optional improvement that does not represent a current requirement failure | Non-blocking |
| Question | Clarification needed before classification or understanding | Blocking only when answer affects readiness |

### Finding Categories

- Functional.
- Architecture or design.
- Security or privacy.
- Data or migration.
- Performance or reliability.
- Maintainability.
- Testing or evidence.
- Documentation or traceability.
- Dependency or supply chain.
- Operational or deployment.

Every finding records severity, category, blocking status, rationale, owner, and state. Teams must not use severity to express reviewer preference.

## 24. Common Mistakes

### Reviewing Only the Diff Syntax

Correct review needs requirements, design, callers, dependencies, tests, and runtime behaviour.

### Treating Automated Checks as Review

Automation finds selected patterns; humans evaluate intent, trade-offs, missing behaviour, and system fit.

### Leaving Vague Comments

“Fix this” does not explain impact, evidence, or required outcome.

### Enforcing Personal Style

Preference is not a blocker unless an approved Standard or material outcome supports it.

### Approving Around Unresolved Findings

Silence, age, or schedule pressure does not resolve risk.

### Re-reviewing Only the Commented Line

A fix may move risk or introduce new behaviour elsewhere.

### Expanding Scope

Review should not opportunistically redesign unrelated code.

### Reviewing Huge Changes as One Unit

Overload reduces defect detection and encourages superficial approval.

### Assuming Generated Code Is Safer

AI and generators require the same understanding, evidence, and ownership.

### Using Review as Performance Evaluation

This discourages questions and honest findings, damaging quality.

## 25. Best Practices

- Review intent and risk before individual lines.
- Use a stable revision and notify reviewers of material updates.
- Separate review scopes and require the right expertise.
- Prioritise correctness, security, data, contracts, and failure behaviour.
- Ask questions before assuming author intent.
- State impact and required outcome clearly.
- Use suggestions for optional improvements.
- Review tests as critically as production code.
- Verify the final revision, not only comment responses.
- Keep changes small enough for meaningful review.
- Escalate authority gaps early.
- Feed recurring issues into systemic improvement.

## 26. Templates

### Review Plan

```markdown
## Revision and Scope

## Requirements and Design

## Risks and Reviewer Focus

## Required Reviewers

## Evidence

## Exclusions

## Decision Authority
```

### Review Finding

```markdown
**Category:**
**Severity:**
**Blocking:** Yes / No
**Location:**
**Issue:**
**Impact:**
**Evidence or governing source:**
**Required outcome:**
**Owner:**
**State:** Open / Addressed / Verified / Escalated / Accepted Risk
```

### Review Decision

```markdown
**Revision:**
**Outcome:**
**Reviewers and scopes:**
**Automated gates:**
**Blocking findings:**
**Conditions or accepted risks:**
**Testing handoff:**
**Approver:**
**Date:**
```

### Testing Handoff

```markdown
## Reviewed Revision

## Requirements and Design Links

## Review Evidence

## Residual Risks and Conditions

## Areas Requiring Broader Verification

## Environment, Data, Migration, and Compatibility Notes
```

## 27. Examples

### Example: Functional Blocking Finding

An order endpoint treats a repeated idempotency key with a different payload as the original request. The contract requires rejection.

The reviewer records a High, blocking functional finding, links the contract, explains the duplicate-charge risk, and requires payload comparison. The author fixes the shared idempotency boundary, adds negative contract tests, and the reviewer verifies the current revision.

### Example: Non-Blocking Suggestion

A reviewer prefers a different local variable name, but the current name is clear and follows existing conventions.

The reviewer either omits the comment or marks it as a Suggestion. Approval does not depend on personal preference.

### Example: Architecture Escalation

A change introduces direct database access across a module boundary to avoid using an approved interface.

The reviewer does not approve the architecture change through code review. The finding is High and blocking, and the decision returns to the technical-design or architecture owner.

### Example: Security Specialist Review

A dependency update changes authentication token validation. The general reviewer checks integration and tests; a security reviewer verifies algorithm restrictions, key handling, claims, failure behaviour, advisories, and migration. Both scopes must approve the same revision.

## 28. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Architecture Principles](../01-principles/03-architecture-principles.md)
- [Coding Principles](../01-principles/04-coding-principles.md)
- [Testing Principles](../01-principles/05-testing-principles.md)
- [Security Principles](../01-principles/06-security-principles.md)
- [Observability Principles](../01-principles/07-observability-principles.md)
- [Performance Principles](../01-principles/08-performance-principles.md)

## 29. Related Standards

- [Playbook Authoring Standard](../03-standards/PB-AUTHORING.md)
- [Engineering Review Standard](../03-standards/STD-REVIEW.md) — General review principles; software code review is out of its declared scope.
- [Engineering Traceability Standard](../03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](../03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](../03-standards/STD-VERSIONING.md)
- [Engineering Terminology Standard](../03-standards/TERM-STANDARD.md)
- [Documentation Style Guide](../03-standards/DOC-STYLE.md)
- [Coding Standards](../03-standards/coding-standards.md) — Planned and non-authoritative.

## 30. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)

## 31. Related Playbooks

- [Coding Playbook](PB-CODING.md) supplies the review-ready change.
- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted review.
- [Technical Design Playbook](PB-TECH-DESIGN.md) supplies implementation intent.
- [Architecture Playbook](PB-ARCH.md) supplies system boundaries and decisions.
- [`PB-TESTING`](PB-TESTING.md) consumes the reviewed change and review conditions.
- [Security Playbook](09-security-playbook.md) governs broader security activity.
- [Debugging Playbook](08-debugging-playbook.md) governs defect diagnosis.
- [`PB-DEPLOYMENT`](PB-DEPLOYMENT.md) governs production release.

## 32. Metrics

Use metrics to improve review quality and flow, not evaluate individuals.

| Metric | What It Reveals | Guardrail |
|---|---|---|
| Time to first substantive review | Review responsiveness | Exclude Draft and waiting-for-author time |
| Review cycle time | Flow from ready request to decision | Segment author and reviewer waiting |
| Findings by category and severity | Risk detected before integration | More findings can indicate stronger review |
| First-review readiness | Author package quality | High values may also indicate superficial review |
| Rework caused by review | Cost of coding gaps | Classify root cause |
| Escaped reviewed defects | Defects missed by code review | Separate test, design, and requirement failures |
| Re-review rate | Material change or incomplete resolution | Interpret by change risk |
| Specialist coverage | Required expert scopes completed | Do not force specialists onto low-risk work |
| Finding recurrence | Systemic gaps in standards, tooling, or learning | Improve the system, not blame authors |
| Review distribution | Knowledge and workload concentration | Protect expertise without quota-driven reviews |

Do not use comment count, approval count, review speed alone, or findings per reviewer as performance targets.

## 33. Reference Implementation and Enterprise Appendices

`PB-CODE-REVIEW` is the reference implementation for independent engineering verification playbooks.

### 33.1 Review Readiness Checklist

- [ ] Stable revision, focused scope, complete package, and self-review.
- [ ] Requirements, design, risks, evidence, rollout, and rollback are linked.
- [ ] Required code owners and specialists are identifiable.
- [ ] Known incomplete work and failed checks are absent or explicitly authorised.

### 33.2 Reviewer Checklist

- [ ] Review scope, competence, independence, and authority are clear.
- [ ] Intent and risk were understood before line-level review.
- [ ] Correctness, design, security, operations, maintainability, tests, and docs were covered.
- [ ] Findings are evidence-based, classified, respectful, and actionable.
- [ ] The current revision and resolutions were verified before decision.

### 33.3 Author Checklist

- [ ] Review package is complete and honest.
- [ ] Questions and findings receive timely, evidence-based responses.
- [ ] Root causes are fixed and affected evidence is rerun.
- [ ] Material updates are announced and re-review requested.
- [ ] Design deviations return upstream.

### 33.4 Security Review Checklist

- [ ] Trust boundaries, input, identity, permission, and least privilege are correct.
- [ ] Secrets and protected data are handled safely.
- [ ] Dependencies, licences, packages, and build changes are verified.
- [ ] Errors, logs, audit, timeouts, retries, and resource limits are safe.
- [ ] Security tests and specialist review match risk.

### 33.5 Architecture Compliance Checklist

- [ ] Responsibilities, boundaries, ownership, and dependency directions match design.
- [ ] Interfaces, schemas, data flow, state, and sequences remain coherent.
- [ ] Existing approved capabilities are reused where suitable.
- [ ] Migration, coexistence, compatibility, and rollback are feasible.
- [ ] Material deviations have upstream approval.

### 33.6 Review Findings Severity Matrix

| Impact | Example | Severity | Default |
|---|---|---|---|
| Catastrophic or exploit-ready | Data loss, critical security, major outage | Critical | Block and escalate |
| Material product or system failure | Incorrect business rule, auth bypass, broken contract | High | Block |
| Bounded real quality failure | Maintainability, reliability, or evidence gap | Medium | Usually block |
| Limited local impact | Minor non-compliance or clarity defect | Low | Fix or follow up |
| Optional improvement | Alternative naming or simplification | Suggestion | Non-blocking |
| Missing understanding | Clarification needed | Question | Classify after answer |

### 33.7 Review Decision Matrix

| Readiness | Blocking Findings | Required Scopes | Decision |
|---|---|---|---|
| Incomplete | Any | Incomplete | Not Ready |
| Complete | Open | Complete or incomplete | Changes Requested |
| Complete | Resolved | Missing | Await required review |
| Complete | Resolved | Complete | Approve |
| Complete | Disputed beyond authority | Complete | Escalate |
| Fundamentally unsuitable approach | Material | Any | Reject or return upstream |

### 33.8 Review Maturity Model

| Level | Characteristics |
|---|---|
| 1. Ad Hoc | Review depends on individuals and often checks style only |
| 2. Repeatable | Basic readiness, peer review, and automated gates |
| 3. Defined | Risk-based scopes, eight phases, findings classification, and traceability |
| 4. Measured | Flow, recurrence, escaped defects, and coverage improve the system |
| 5. Adaptive | Review depth, automation, and ownership evolve from evidence |

### 33.9 AI-Assisted Review Guidance

- Use AI only through `PB-AI-ENGINEERING`.
- Limit context to authorised code and evidence.
- Treat findings as hypotheses.
- Verify line references, APIs, behaviour, severity, and remediation.
- Do not use AI as the required independent reviewer.
- Do not retain protected code or review content outside approved controls.
- Record material AI contribution when required.

### 33.10 Traceability Checklist

- [ ] Review baseline links to requirements, design, work item, and author.
- [ ] Findings link to affected code, evidence, owner, and resolution.
- [ ] Approval identifies exact revision, reviewers, scopes, and conditions.
- [ ] Testing handoff includes residual risks and focus areas.
- [ ] Material decisions and exceptions remain discoverable.

### 33.11 Deliverables Checklist

- [ ] Review scope and assignments.
- [ ] Findings and discussion record.
- [ ] Updated implementation and validation.
- [ ] Verified finding resolutions.
- [ ] Human review decision.
- [ ] Traceability and Testing handoff.

### 33.12 Review Exit Criteria

- [ ] Required scopes and reviewers are complete.
- [ ] Blocking findings are resolved.
- [ ] Automated and manual evidence passes on the current revision.
- [ ] Design deviations and residual risks have authorised disposition.
- [ ] Documentation and traceability are current.
- [ ] The change is ready for Testing or governed integration.

Failure of any exit criterion prevents approval.

## 34. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.2 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the governed `PB-DEPLOYMENT` release stage |
| 1.0.1 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the governed `PB-TESTING` verification handoff |
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Code Review Playbook with eight-phase verification workflow, findings classification, governance, risk, security, accountability, metrics, and twelve enterprise appendices |

## 35. Summary

`PB-CODE-REVIEW` governs independent engineering verification of implemented software.

It requires teams to:

- Review a stable, prepared change.
- Verify functionality, architecture, security, operations, and maintainability.
- Classify findings by impact and blocking status.
- Resolve disagreements through evidence and authority.
- Reverify the current revision.
- Record a human approval, rejection, revision, or escalation decision.
- Hand reviewed software and residual risk to Testing.

`PB-CODING` governs how software is implemented. Standards define acceptable implementation rules. `PB-CODE-REVIEW` governs how a qualified, independent reviewer evaluates whether the change is ready to become part of the product and proceed through broader verification.
