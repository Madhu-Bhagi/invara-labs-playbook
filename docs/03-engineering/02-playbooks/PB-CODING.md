---
title: Coding Playbook
id: PB-CODING
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
  - coding
  - implementation
  - software-engineering
  - development
  - engineering
  - execution
  - playbook
related:
  - CP-001
  - CP-002
  - CP-003
  - CP-004
  - CP-005
  - CP-006
  - CP-007
  - PB-TECH-DESIGN
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

# Coding Playbook

> **The standard operating procedure for implementing approved technical designs into production-ready software that is correct, maintainable, secure, testable, and traceable.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. Coding Workflow
10. Coding Lifecycle
11. Detailed Phase Activities
12. Implementation Concepts
13. Coding Decision Framework
14. Deliverables
15. Quality Gates
16. Coding Checklist
17. AI-Assisted Coding
18. Coding Governance
19. Risk Management
20. Secure Coding
21. Human Accountability
22. Coding Standards Integration
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

Coding is the controlled translation of an approved technical design into executable, reviewable software.

This playbook begins when a technical design or proportionate implementation brief is ready. It ends when the implementation:

- Satisfies the intended requirements and design.
- Preserves approved architecture, boundaries, contracts, and quality thresholds.
- Includes required source code, configuration, migrations, infrastructure, tests, and documentation.
- Passes self-review and automated validation.
- Is traceable to its governing artefacts.
- Is organised into understandable commits.
- Is packaged with enough evidence for effective code review.

Coding is not a private activity between an engineer and an editor. It is one governed stage in a delivery system:

```text
Approved Technical Design
        │
        ▼
PB-CODING
        │
        ▼
Review-Ready Change
        │
        ▼
PB-CODE-REVIEW
        │
        ▼
PB-TESTING
        │
        ▼
PB-DEPLOYMENT
```

This playbook is technology-neutral. Language syntax, formatting rules, framework conventions, and design-pattern catalogues belong in Standards and References.

## 2. Purpose

This playbook helps engineers:

- Understand the approved design before changing code.
- Prepare a reproducible and safe development environment.
- Plan work as small, coherent, testable implementation slices.
- Implement the simplest solution that satisfies the current requirement.
- Preserve architectural and component boundaries.
- Validate continuously rather than deferring quality until review.
- Handle configuration, data, infrastructure, documentation, and tests as part of the change.
- Maintain traceability from design to implementation and evidence.
- Produce clear commit history and a review-ready change package.
- Respond to review findings without losing design intent.

## 3. Objectives

Following this playbook should produce:

- Shared understanding of the implementation scope.
- A verified development environment.
- A sequenced implementation plan.
- Correct and maintainable source code.
- Safe configuration, migrations, and infrastructure definitions where needed.
- Unit and focused integration tests.
- Updated technical and operational documentation.
- Static-analysis, build, and local-test evidence.
- Traceable and coherent commits.
- A complete review package.
- Timely resolution of code-review findings.

The objective is not to maximise code written. It is to deliver the smallest complete change that produces the approved outcome safely.

## 4. Scope

### In Scope

Apply this playbook to:

- New product features and system capabilities.
- Changes to services, modules, components, libraries, APIs, jobs, and integrations.
- Defect fixes and root-cause corrections.
- Refactoring tied to a defined outcome.
- Database schemas, migration scripts, queries, and data transformations.
- Configuration, build, CI/CD, and infrastructure definitions.
- Security, reliability, performance, and observability improvements.
- Documentation and test updates required by implementation.

### Proportionate Application

| Change Profile | Expected Application |
|---|---|
| Small, local, reversible | Focused design reference, local validation, self-review, coherent commit, review package |
| Material feature or integration | Full nine-phase workflow, implementation plan, tests, traceability, and multidisciplinary evidence |
| High-risk, regulated, data-changing, or production-critical | Formal design baseline, specialist controls, migration rehearsal, independent evidence, staged review |

### Out of Scope

This playbook does not:

- Define requirements or approve architecture and technical design.
- Replace coding standards, language conventions, or framework references.
- Replace code review, system testing, security testing, or deployment approval.
- Justify speculative features or unrelated cleanup.
- Permit implementation to silently change an approved contract or architecture.
- Define product-specific branching or release policy.
- Treat local success as proof of production readiness.

## 5. When to Use This Playbook

Use this playbook whenever an engineer changes a governed software artefact intended to enter a shared codebase or delivery pipeline.

Start when:

- The implementation objective and acceptance criteria are understood.
- The technical design or proportionate implementation brief is available.
- Required decisions, risks, interfaces, and quality thresholds are known.
- The implementing engineer and reviewers are identified.

Re-enter this playbook when:

- Review findings require implementation changes.
- Testing exposes a coding defect or incomplete implementation.
- A dependency, contract, design, or migration assumption changes.
- Production evidence requires a corrective code change.

Return upstream when:

- Business behaviour or acceptance criteria are unclear: return to `PB-REQ`.
- System boundaries or material architecture change: return to `PB-ARCH`.
- Component, contract, data, security, or operational design changes materially: return to `PB-TECH-DESIGN`.

## 6. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| Implementing Engineer | Owns understanding, implementation, self-review, evidence, commits, and review support |
| Technical Design Owner | Clarifies design intent and evaluates technical-design deviations |
| Engineering Lead | Confirms scope, sequencing, standards, capability, risk, and escalation |
| Code Owner | Protects owned boundaries, conventions, compatibility, and maintainability |
| Quality Engineer | Advises on test strategy, independence, coverage, and evidence |
| Security Reviewer | Reviews sensitive code, trust boundaries, dependencies, secrets, and controls |
| Data Owner | Reviews schemas, migrations, integrity, retention, access, and recovery |
| Platform or Operations Engineer | Reviews build, configuration, infrastructure, deployment, and operability impacts |
| Code Reviewer | Independently evaluates correctness, design fit, risk, tests, and readiness |
| Product Owner | Clarifies user-visible behaviour and acceptance when needed |

### Responsibility Rules

- The implementing engineer owns all submitted code, including generated or copied code.
- A design owner clarifies intent; they do not waive required evidence.
- Reviewers remain independent enough to challenge assumptions.
- High-risk work requires qualified specialist review.
- AI may assist under `PB-AI-ENGINEERING`; it cannot own code or approve submission.

## 7. Inputs

| Input | Required Information |
|---|---|
| Approved technical design | Components, interfaces, data, security, operations, constraints, decisions, and implementation plan |
| Requirements and acceptance criteria | Intended behaviour, boundaries, quality thresholds, and traceable identifiers |
| Architecture and ADRs | Approved system boundaries, patterns, dependencies, and material decisions |
| Current codebase | Existing implementation, tests, conventions, utilities, dependencies, and technical debt |
| Applicable standards | Coding, security, API, logging, documentation, metadata, versioning, and review rules |
| Development environment definition | Toolchain, runtime, dependencies, services, configuration, and setup |
| Risk and migration records | Known technical, data, security, delivery, compatibility, and rollback concerns |
| Work item | Scope, owner, priority, dependencies, and links to authoritative artefacts |
| Verification plan | Required static checks, builds, tests, benchmarks, security checks, and evidence |

Read the current implementation before writing code. Existing patterns may already solve the problem, reveal constraints, or expose a better root-cause location.

## 8. Entry Criteria

Before implementation begins, confirm:

- The change has a named owner.
- Scope, intended behaviour, and acceptance criteria are clear.
- The technical design or proportionate brief is available.
- Architecture, contract, data, security, and operational constraints are understood.
- The current code and relevant tests have been inspected.
- Required standards and owners are known.
- Dependencies, environments, and access are available.
- A verification and rollback approach exists.
- Material unknowns have owners.

Do not start coding to discover what the requirement should have been. Use a small prototype only when the design explicitly identifies evidence that implementation must obtain.

## 9. Coding Workflow

| Phase | Objective | Exit Decision |
|---|---|---|
| 1. Understand the Technical Design | Establish scope, intent, constraints, risks, and traceability | Is the approved implementation direction understood? |
| 2. Prepare the Development Environment | Create a reproducible, isolated, and validated workspace | Can the change be built and tested safely? |
| 3. Plan the Implementation | Divide work into coherent, dependency-aware, testable slices | Is the sequence small enough to implement and review? |
| 4. Implement the Solution | Produce the simplest complete change aligned with design and standards | Does the code express the approved behaviour? |
| 5. Perform Self Verification | Inspect intent, correctness, scope, security, maintainability, and diff quality | Would the engineer confidently review this work from another contributor? |
| 6. Execute Automated Validation | Run applicable formatting, static, build, test, security, and migration checks | Is the implementation supported by repeatable evidence? |
| 7. Update Documentation | Bring technical, API, configuration, migration, and operational documentation in line with implementation | Can users, engineers, and operators understand the changed system? |
| 8. Prepare the Review Package | Organise commits, description, evidence, risks, and reviewer guidance | Can a reviewer understand and evaluate the change efficiently? |
| 9. Submit and Support Code Review | Request reviewers, protect the baseline, resolve findings, and revalidate | Is the change ready to complete formal review? |

```text
Approved Technical Design
        │
        ▼
Understand Design
        │
        ▼
Prepare Environment
        │
        ▼
Plan Implementation
        │
        ▼
Implement Incrementally
        │
        ▼
Self Verification
        │
        ▼
Automated Validation
        │
        ▼
Update Documentation
        │
        ▼
Prepare Review Package
        │
        ▼
Submit for Code Review
        │
        ▼
Resolve Findings
```

## 10. Coding Lifecycle

Code evolves through controlled states:

```text
Planned Change
      │
      ▼
Local Implementation
      │
      ▼
Self-Verified Change
      │
      ▼
Review-Ready Change
      │
      ▼
Reviewed and Tested Change
      │
      ▼
Released Software
      │
      ▼
Maintained or Retired Software
```

The source repository is authoritative. Local notes, AI conversations, generated patches, and uncommitted work are transient. Accepted code, tests, decisions, and documentation must enter the governed repository and normal lifecycle.

Implementation evidence remains valid only for the tested code and environment. Material changes after validation require the affected checks to run again.

## 11. Detailed Phase Activities

### Phase 1: Understand the Technical Design

**Objective:** Translate the approved design into a precise implementation boundary.

**Activities:**

1. Read the TDD, requirements, ADRs, interface contracts, risks, and acceptance criteria.
2. Trace the work item to the design elements and expected evidence.
3. Inspect affected code, tests, schemas, configuration, infrastructure, and ownership.
4. Identify fixed decisions, reversible implementation choices, and escalation triggers.
5. List assumptions, unknowns, compatibility needs, and operational impacts.
6. Confirm what is explicitly out of scope.

**Outputs:**

- Implementation understanding record.
- Affected-artefact and dependency map.
- Open-question and escalation list.

**Exit criteria:**

- The engineer can explain what must change and why.
- Scope and boundaries are explicit.
- Material design gaps have returned upstream.

### Phase 2: Prepare the Development Environment

**Objective:** Establish a reproducible workspace that can build and verify the current baseline before change.

**Activities:**

1. Use the approved runtime, toolchain, dependency, and environment definitions.
2. Obtain least-privileged access and safe test data.
3. Configure secrets through approved mechanisms; never commit them.
4. Build and run relevant baseline checks.
5. Confirm local dependencies and services match supported versions.
6. Isolate work through the repository's approved branch or worktree practice.
7. Record environment limitations that affect evidence.

**Outputs:**

- Working development environment.
- Baseline build and test evidence.
- Environment issue record where needed.

**Exit criteria:**

- The unchanged baseline builds and relevant tests pass, or existing failures are documented.
- No production data or unsafe credentials are used.
- The engineer can reproduce the validation path.

### Phase 3: Plan the Implementation

**Objective:** Sequence the change into small, coherent, testable, and reviewable slices.

**Activities:**

1. Map design deliverables to code, test, configuration, migration, infrastructure, and documentation changes.
2. Order compatibility and migration work safely.
3. Identify reuse opportunities in the existing codebase.
4. Define completion and evidence for each slice.
5. Separate necessary change from unrelated cleanup.
6. Identify feature flags, staged rollout, or backward-compatibility needs.
7. Confirm commit and review boundaries.

**Outputs:**

- Implementation plan.
- Slice, dependency, and evidence map.
- Risk-reduction order.

**Exit criteria:**

- Each slice is independently understandable and testable where practical.
- Dependencies and migration order are safe.
- Scope remains aligned with the approved design.

### Phase 4: Implement the Solution

**Objective:** Produce the smallest complete implementation that satisfies the approved behaviour.

**Activities:**

1. Begin at the root cause or authoritative shared boundary.
2. Reuse suitable existing helpers, components, types, patterns, and platform capabilities.
3. Implement one coherent slice at a time.
4. Preserve contracts, invariants, ownership, and dependency direction.
5. Validate inputs and protect trust boundaries.
6. Handle errors, state, concurrency, retries, idempotency, and recovery as designed.
7. Add tests with the behaviour rather than after all coding.
8. Update configuration, migrations, infrastructure, and documentation in the same change.
9. Avoid speculative abstractions, unrelated refactors, and unnecessary dependencies.

**Outputs:**

- Source code.
- Tests and fixtures.
- Configuration, migration, build, and infrastructure changes.
- Documentation updates.

**Exit criteria:**

- The slice implements intended behaviour and failure handling.
- Code remains understandable and aligned with design.
- Required supporting artefacts are present.

### Phase 5: Perform Self Verification

**Objective:** Review the change critically before asking another engineer to spend review time.

**Activities:**

1. Read the complete diff, not only edited files.
2. Compare behaviour with requirements and design.
3. Remove debugging output, dead code, duplication, accidental files, and speculative complexity.
4. Check names, responsibilities, control flow, error handling, and comments.
5. Review security, privacy, data integrity, compatibility, performance, and operational effects.
6. Confirm tests fail for the intended defect or missing behaviour where practical.
7. Verify no secrets, personal data, credentials, or unsafe test data are present.
8. Check that documentation and traceability remain accurate.

**Outputs:**

- Self-review checklist.
- Corrected implementation.
- Known limitations and residual risks.

**Exit criteria:**

- The engineer understands every changed line.
- The diff contains only intentional work.
- Material issues are corrected or escalated.

### Phase 6: Execute Automated Validation

**Objective:** Produce repeatable evidence that the change meets applicable technical controls.

**Activities:**

1. Run repository formatting and lint checks.
2. Run type checking, compilation, and build steps.
3. Run focused unit, integration, contract, and regression tests.
4. Run static security, dependency, licence, and secret checks where applicable.
5. Validate schemas, migrations, rollback, and data reconciliation.
6. Run performance, concurrency, compatibility, or accessibility checks when risk requires.
7. Record commands, environment, results, and justified exclusions.

**Outputs:**

- Automated-validation evidence.
- Test and analysis results.
- Corrected implementation or exception record.

**Exit criteria:**

- Required checks pass.
- Failures are resolved rather than hidden or disabled.
- Any unavailable check has an authorised alternative and owner.

### Phase 7: Update Documentation

**Objective:** Keep governed documentation consistent with the implemented behaviour.

**Activities:**

1. Update API and interface documentation.
2. Update configuration, environment, build, and dependency guidance.
3. Update migration, rollback, operational, and support documentation.
4. Record implementation notes only when they provide maintained value.
5. Update diagrams, examples, and traceability affected by the change.
6. Remove or mark obsolete instructions.
7. Validate documentation links, terminology, commands, and examples.

**Outputs:**

- Updated technical and operational documentation.
- Accurate API, configuration, and migration guidance.
- Updated traceability.

**Exit criteria:**

- Documentation agrees with the implemented revision.
- Affected audiences can use and operate the change.
- No known stale guidance remains.

### Phase 8: Prepare the Review Package

**Objective:** Make the change efficient to understand, reproduce, and review.

**Activities:**

1. Organise commits into coherent units with meaningful messages.
2. Rebase or update safely according to repository policy.
3. Write the change summary, reason, approach, scope, and exclusions.
4. Link requirements, TDD sections, ADRs, work items, and evidence.
5. Describe user-visible behaviour, compatibility, migration, deployment, and rollback.
6. Highlight high-risk files, deliberate trade-offs, and questions for reviewers.
7. Confirm the final diff and validation after commit preparation.

**Outputs:**

- Coherent commit history.
- Review description.
- Evidence and traceability links.
- Reviewer guidance.

**Exit criteria:**

- A reviewer can understand why, what, and how.
- Evidence corresponds to the submitted revision.
- Risks and open questions are visible.

### Phase 9: Submit and Support Code Review

**Objective:** Transfer the review-ready change into the governed process and resolve findings without losing intent.

**Activities:**

1. Select required code owners and specialist reviewers.
2. Submit through the repository's approved review mechanism.
3. Confirm automated checks started against the correct revision.
4. Mark Draft when known work remains; request review only when ready.
5. Avoid changing the review baseline without notifying reviewers.
6. Respond promptly to questions that block understanding.
7. Classify findings as accepted, clarified, disputed with evidence, or escalated.
8. Fix root causes, update affected artefacts, and re-run validation.
9. Explain significant changes and request re-review.
10. Return upstream when a finding exposes a requirement, architecture, or design change.

**Outputs:**

- Resolved findings.
- Updated code and evidence.
- Submitted review package, reviewer assignments, and decision inputs.

**Exit criteria:**

- Blocking findings are resolved.
- Required checks pass on the current revision.
- The change is ready for formal review completion and downstream testing.

## 12. Implementation Concepts

### Implementation Slice

An implementation slice is a coherent unit that delivers or enables observable behaviour and can be reasoned about, tested, and reviewed. Prefer vertical slices over large layers of unfinished infrastructure.

### Root-Cause Implementation

Place a fix at the shared source of incorrect behaviour. A local guard may hide one symptom while sibling callers remain unsafe.

### Smallest Complete Change

Small does not mean incomplete. A complete change includes required tests, error handling, configuration, migration, documentation, security, and operational effects.

### Reuse Before Addition

Inspect the codebase, standard library, platform, and installed dependencies before creating a new abstraction or dependency. Reuse only when the existing solution remains fit and understandable.

### Reversibility

Prefer choices that are easy to change until evidence justifies commitment. Data loss, public contracts, security boundaries, and irreversible migrations require stronger design and review.

### Defensive Boundaries

Validate at trust boundaries. Inside a well-controlled boundary, use types, invariants, and focused interfaces to make invalid states difficult.

### Tests as Implementation Evidence

Tests demonstrate selected behaviour under defined conditions. They do not prove absence of defects. Derive tests from requirements, risks, contracts, and failure modes rather than mirroring implementation structure.

### Review-Ready

A change is review-ready when its purpose, scope, implementation, evidence, risks, and traceability are complete enough for independent evaluation.

## 13. Coding Decision Framework

Before making an implementation choice:

1. Trace the decision to a requirement, technical design element, standard, or risk.
2. Check whether the existing codebase already establishes a suitable pattern.
3. Prefer the simplest solution that satisfies current needs.
4. Evaluate correctness, security, testability, maintainability, operability, performance, and reversibility.
5. Determine whether the choice is local or changes an approved design.
6. Gather evidence for uncertain or high-cost assumptions.
7. Record the decision at the proportionate level.

| Choice | Authority and Record |
|---|---|
| Local, reversible implementation detail | Implementing engineer; code and review rationale |
| Shared component, contract, or data behaviour | Design owner and affected code/data owner |
| Material technical-design deviation | Return to `PB-TECH-DESIGN` |
| Architecture boundary or long-lived cross-team decision | Return to `PB-ARCH` and ADR governance |
| Security, privacy, legal, or irreversible risk | Specialist and authorised risk owner |

## 14. Deliverables

| Deliverable | Minimum Content |
|---|---|
| Source Code | Complete implementation aligned with design and standards |
| Configuration Files | Safe defaults, validation, environment separation, ownership |
| Database Migration Scripts | Forward change, compatibility, verification, rollback or recovery |
| Infrastructure Definitions | Least privilege, reproducibility, policy compliance, rollback |
| Unit Tests | Focused behaviour and boundary evidence |
| Integration and Contract Tests | Collaboration and compatibility evidence |
| Documentation Updates | User, developer, API, operational, and decision information affected |
| Build Configuration | Reproducible dependencies, tooling, generation, and packaging |
| Commit History | Coherent, traceable implementation units |
| Validation Evidence | Static, build, test, security, migration, and risk-specific results |
| Review Package | Summary, links, risks, rollout, rollback, and reviewer guidance |

## 15. Quality Gates

### Gate A: Implementation Ready

- Design, acceptance criteria, scope, owner, standards, and risks are understood.
- The baseline environment builds and relevant existing tests are known.

### Gate B: Slice Ready

- The implementation plan is coherent, proportionate, dependency-aware, and testable.
- Compatibility, migration, security, and rollback needs are explicit.

### Gate C: Code Complete

- Intended behaviour, failure handling, tests, configuration, documentation, and traceability are implemented.
- No silent design deviation or unrelated scope is present.

### Gate D: Validation Complete

- Self-review and required automated checks pass.
- Evidence matches the current revision.
- Residual risks and unavailable checks are authorised and visible.

### Gate E: Review Ready

- Commits and review description are coherent.
- Required reviewers, evidence, migration, rollout, rollback, and questions are identified.
- The implementing engineer can explain every change.

## 16. Coding Checklist

### Understanding and Scope

- [ ] Requirements, design, decisions, standards, and risks are linked.
- [ ] The current implementation and tests were inspected.
- [ ] In-scope and out-of-scope work are explicit.
- [ ] Material gaps returned upstream.

### Implementation

- [ ] The change is the smallest complete solution.
- [ ] Existing suitable capabilities were reused.
- [ ] Responsibilities and dependencies remain focused.
- [ ] Inputs, errors, state, concurrency, and recovery are handled.
- [ ] Configuration, migrations, infrastructure, tests, and docs are included.

### Verification

- [ ] The complete diff was self-reviewed.
- [ ] Required formatting, static, build, test, security, and migration checks pass.
- [ ] Tests cover requirements, boundaries, failures, and regression.
- [ ] Secrets, protected data, debug artefacts, and accidental files are absent.

### Review Readiness

- [ ] Commits are coherent and messages explain intent.
- [ ] The review package links design and evidence.
- [ ] Risks, compatibility, rollout, and rollback are explained.
- [ ] Required owners and specialists are requested.

## 17. AI-Assisted Coding

AI may assist with:

- Code and test drafting.
- Refactoring proposals.
- Existing-code explanation.
- Boilerplate and repetitive transformation.
- Documentation.
- Static-analysis interpretation.
- Edge-case and defect hypothesis generation.

All AI-assisted coding follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

The implementing engineer must:

- Provide only authorised context.
- Inspect the actual codebase before accepting generated patterns.
- Understand every accepted line.
- Remove unnecessary abstraction and dependencies.
- Verify APIs, versions, licences, security, and behaviour.
- Use independent tests and normal peer review.
- Record material AI contribution when required.

AI governance is not duplicated here. `PB-AI-ENGINEERING` remains authoritative.

## 18. Coding Governance

Coding governance ensures implementation remains within approved intent and organisational authority.

### Governance Requirements

- Every change has a named implementing engineer and accountable owner.
- Requirements, architecture, technical design, work items, code, tests, and review evidence remain traceable.
- Material design deviations return upstream before becoming accidental architecture.
- Required code owners and specialists review affected boundaries.
- Exceptions to standards or validation are explicit, time-bounded, and authorised.
- Source control, review, testing, release, and separation-of-duties controls remain intact.
- Generated, vendored, copied, and third-party code receives the same ownership and evidence.
- Review findings and production evidence feed continuous improvement.

### Decision Rights

| Decision | Authority |
|---|---|
| Local reversible implementation detail | Implementing engineer |
| Shared component, contract, or data behaviour | Design and affected owner |
| Standards exception | Standard owner or engineering governance |
| Security or privacy exception | Authorised specialist and risk owner |
| Architecture deviation | Architecture governance |
| Review approval | Required independent reviewers |
| Deployment approval | Release authority, not the implementing engineer alone |

## 19. Risk Management

Implementation risk is managed from planning through review support.

| Risk | Warning Signal | Required Treatment |
|---|---|---|
| Architecture drift | Boundaries, dependencies, or contracts change silently | Stop and return upstream |
| Incorrect behaviour | Implementation does not trace to acceptance criteria | Requirement-derived tests and review |
| Security vulnerability | New trust boundary, input, privilege, secret, or dependency | Threat-aware implementation and specialist evidence |
| Data loss or corruption | Destructive migration, weak transaction, missing reconciliation | Staged migration, rehearsal, integrity checks, recovery |
| Performance regression | New hot path, unbounded work, excessive I/O, or allocation | Representative measurement and thresholds |
| Compatibility failure | Public contract or data format changes | Compatibility plan and contract tests |
| Duplicate logic | Existing capability is reimplemented | Search and reuse or justify replacement |
| Technical debt | Shortcut lacks owner, limit, or repayment condition | Remove before review or record authorised debt |
| Review overload | Large mixed change and unclear history | Split into coherent reviewable slices |
| Incomplete validation | Checks are absent, flaky, skipped, or suppressed | Restore evidence or obtain authorised alternative |
| Dependency risk | New package has unclear maintenance, licence, or security | Necessity, provenance, version, licence, and vulnerability review |

Each material risk records impact, evidence, treatment, owner, and review trigger. Schedule pressure does not convert unknown risk into accepted risk.

## 20. Secure Coding

Security is part of implementation, not a final scanner.

Engineers must:

- Validate and normalise untrusted input at trust boundaries.
- Enforce authentication, authorisation, ownership, and least privilege.
- Use approved cryptographic, identity, secret, and session capabilities.
- Keep credentials and protected data out of source, logs, tests, errors, and generated artefacts.
- Use parameterised data access and safe output encoding.
- Protect against injection, traversal, request forgery, replay, enumeration, unsafe deserialisation, and resource exhaustion.
- Bound timeouts, retries, concurrency, memory, payloads, and external calls.
- Handle errors without leaking secrets or internal implementation details.
- Review dependencies, packages, build scripts, licences, and supply-chain provenance.
- Produce useful audit and security signals without exposing sensitive content.
- Fail safely and preserve integrity when controls or dependencies fail.

Security-sensitive changes require threat context, negative tests, automated checks, and qualified review proportionate to risk. Planned coding or security standards become authoritative only after approval; until then, approved architecture, technical design, security principles, and reviewer direction govern.

## 21. Human Accountability

The implementing engineer remains accountable for:

- Understanding the requirement, design, and code.
- Correctness and completeness of every submitted change.
- Security, privacy, data integrity, and dependency choices.
- Maintainability, performance, reliability, and operability.
- Test quality and validation evidence.
- Documentation and traceability.
- Commit and review-package quality.
- Honest disclosure of uncertainty, skipped checks, and residual risk.

AI, generators, frameworks, copied examples, and third-party libraries do not own the result. An engineer who cannot explain, validate, or maintain an implementation must not submit it as review-ready.

Human accountability does not mean one person works alone. It means named people make decisions, specialist authority is respected, independent review occurs, and responsibility cannot be delegated to a tool.

## 22. Coding Standards Integration

This playbook governs **how implementation work proceeds**.

Standards govern mandatory implementation rules, including:

- Language and framework conventions.
- Naming, formatting, and source organisation.
- API, error, logging, and documentation requirements.
- Dependency, security, testing, and quality thresholds.
- Git, commit, versioning, and automation requirements.

References provide reusable design patterns, secure-coding knowledge, technology guidance, and examples.

When an applicable Standard is Approved:

1. Identify it during implementation planning.
2. Apply its mandatory controls.
3. Run its required automation.
4. Record justified exceptions through its governance.
5. Link relevant evidence in the review package.

The Planned [Coding Standards](../03-standards/coding-standards.md) are not authoritative until reviewed and approved. This playbook must not be used to invent missing language-specific rules.

## 23. Common Mistakes

### Coding Before Understanding

Early activity can create rework when requirements or design are unresolved.

### Patching the Symptom

A local fix leaves shared root behaviour and sibling callers defective.

### Reimplementing Existing Capability

Duplicate helpers and patterns fragment the codebase and create inconsistent behaviour.

### Expanding Scope During Implementation

Unrelated cleanup makes review harder and risk less visible.

### Overengineering

Speculative abstraction, configuration, and dependencies increase maintenance cost without current value.

### Testing Only the Happy Path

Invalid input, failures, retries, state, concurrency, and recovery define production reliability.

### Hiding Failed Checks

Disabling tests, suppressing warnings, or omitting results transfers risk to reviewers and customers.

### Mixing Migration and Cutover Unsafely

Incompatible schema and code changes can make rollback impossible.

### Treating Commits as a Backup Dump

Large, incoherent commits hide intent and slow review.

### Relying on Review to Find Basic Problems

Reviewers should challenge engineering judgement, not perform the author's missing self-review.

## 24. Best Practices

- Read before writing.
- Follow the approved design and escalate deviations early.
- Implement and verify one coherent slice at a time.
- Prefer boring, explicit, maintainable code.
- Keep responsibilities and dependency directions clear.
- Make safe behaviour the easiest behaviour.
- Add evidence with the change.
- Use realistic but non-sensitive test data.
- Keep commits and review packages focused.
- Re-run affected checks after every material change.
- Leave the codebase clearer than before without expanding unrelated scope.

## 25. Templates

### Implementation Plan

| Slice | Design Link | Code and Artefacts | Dependencies | Evidence | Owner |
|---|---|---|---|---|---|
| 1 | TDD section | Files or components | Required predecessors | Tests and checks | Engineer |

### Implementation Understanding Record

```markdown
## Objective

## Requirements and Design

## Affected Components and Owners

## Constraints and Decisions

## Risks and Unknowns

## In Scope

## Out of Scope

## Verification Plan

## Escalation Triggers
```

### Self-Review Record

```markdown
## Behaviour Checked

## Diff and Scope Checked

## Security and Data Checked

## Failure and Recovery Checked

## Tests and Documentation Checked

## Known Limitations
```

### Review Package

```markdown
## Why
Problem and approved outcome.

## What
Behaviour and artefacts changed.

## How
Implementation approach and key decisions.

## Evidence
Build, tests, analysis, security, migration, and manual checks.

## Risk
Compatibility, data, security, performance, and operational concerns.

## Rollout and Rollback
Deployment order, flags, migration, observation, and recovery.

## Traceability
Requirements, TDD, ADRs, work items, and documentation.

## Reviewer Focus
High-risk areas and explicit questions.
```

## 26. Examples

### Example: Adding an Order Status Endpoint

The approved TDD defines the contract, permissions, data source, errors, and observability.

The engineer:

1. Finds an existing request-validation and authorisation path.
2. Plans separate contract, query, handler, test, documentation, and observability slices.
3. Reuses the shared order identifier and error mapping.
4. Adds unit tests for valid, missing, unauthorised, and invalid requests.
5. Adds a contract test for response compatibility.
6. Runs static checks, build, focused tests, and secret scanning.
7. Submits a review package linking the TDD and evidence.

The engineer does not introduce a new response abstraction because the established contract pattern is suitable.

### Example: Fixing Duplicate Payment Processing

A reported duplicate charge appears in one API path. Investigation shows retry callers share a non-idempotent payment function.

The engineer fixes the shared function, adds idempotency at the designed boundary, tests multiple callers and concurrent duplicates, updates operational metrics, and explains the migration and rollback.

Fixing only the reported endpoint would leave sibling callers unsafe.

### Example: Database Migration

The engineer separates the change into expand, backfill, switch, and contract stages. Old and new application versions remain compatible during rollout. Reconciliation validates the backfill, and the destructive cleanup occurs only after consumers and rollback conditions are confirmed.

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
- [Engineering Review Standard](../03-standards/STD-REVIEW.md)
- [Engineering Traceability Standard](../03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](../03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](../03-standards/STD-VERSIONING.md)
- [Engineering Terminology Standard](../03-standards/TERM-STANDARD.md)
- [Documentation Style Guide](../03-standards/DOC-STYLE.md)
- [Coding Standards](../03-standards/coding-standards.md) — Planned and non-authoritative until approved.

## 29. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)

## 30. Related Playbooks

- [Requirements Playbook](PB-REQ.md) supplies intended behaviour and acceptance criteria.
- [Architecture Playbook](PB-ARCH.md) supplies system boundaries and material decisions.
- [Technical Design Playbook](PB-TECH-DESIGN.md) supplies the implementation-ready design.
- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted coding.
- [Code Review Playbook](06-code-review-playbook.md) consumes the review-ready package.
- [Testing Playbook](07-testing-playbook.md) expands verification beyond implementation checks.
- [Debugging Playbook](08-debugging-playbook.md) governs systematic diagnosis.
- [Security Playbook](09-security-playbook.md) governs security activities.
- [Deployment Playbook](12-deployment-playbook.md) governs release.
- [Observability Playbook](10-observability-playbook.md) governs operational evidence.

## 31. Metrics

Use metrics to improve coding outcomes, not reward code volume.

| Metric | What It Reveals | Guardrail |
|---|---|---|
| Implementation cycle time | Time from coding-ready input to review-ready change | Separate waiting from active work |
| First-review readiness | Changes without basic blocking omissions | High values may indicate weak review |
| Review rework | Effort caused by implementation gaps | Classify root cause |
| Validation failure rate | Defects caught before review | Early findings indicate controls working |
| Escaped coding defects | Implementation defects found after review or release | Do not attribute design or requirement defects incorrectly |
| Change size | Review and integration risk | Do not optimise for arbitrary line limits |
| Revert or rollback rate | Changes requiring recovery | Interpret with deployment and incident evidence |
| Traceability completeness | Links from design through code and tests | Check meaning, not link presence |
| Build and test reliability | Whether evidence is repeatable | Separate flaky infrastructure from code defects |
| Maintainability signals | Complexity, duplication, ownership, and change concentration trends | Use as investigation prompts, not individual scores |

Do not use lines of code, commits, hours online, or AI-generated volume as productivity targets.

## 32. Reference Implementation and Enterprise Appendices

`PB-CODING` is the reference implementation for execution playbooks that convert an approved upstream baseline into reviewable engineering artefacts.

### 32.1 Implementation Readiness Checklist

- [ ] Scope, owner, design, acceptance, and standards are clear.
- [ ] Current code and tests were inspected.
- [ ] Environment and baseline validation work.
- [ ] Dependencies, access, migration, and rollback are understood.
- [ ] Unknowns and escalation triggers are owned.

### 32.2 Self-Verification Checklist

- [ ] Complete diff matches intended behaviour and scope.
- [ ] Existing suitable patterns were reused.
- [ ] Code is readable, focused, and free of speculative complexity.
- [ ] Inputs, errors, failures, state, and recovery are handled.
- [ ] Security, data, compatibility, performance, and operations were considered.
- [ ] Tests and documentation are complete.
- [ ] Secrets, debug output, dead code, and accidental files are absent.

### 32.3 Coding Risk Matrix

| Risk | Warning Signal | Treatment |
|---|---|---|
| Scope creep | Unrelated files or behaviours change | Split or defer unrelated work |
| Design drift | Code changes approved boundaries or contracts | Return upstream |
| Data loss | Destructive or incompatible migration | Expand/migrate/switch/contract with rehearsal |
| Security regression | New trust, privilege, input, secret, or dependency | Specialist review and security evidence |
| Hidden failure | Errors swallowed or unobservable | Explicit failure, recovery, and signals |
| Review overload | Large mixed diff and unclear commits | Smaller coherent slices and stacked review if supported |
| Irreversible rollout | No compatibility or rollback | Redesign before review |

### 32.4 Secure Coding Checklist

- [ ] Trust boundaries and protected assets are identified.
- [ ] Inputs are validated and outputs are encoded appropriately.
- [ ] Authentication, authorisation, ownership, and least privilege are enforced.
- [ ] Secrets and protected data are absent from source, logs, tests, and errors.
- [ ] Data access is parameterised and integrity is preserved.
- [ ] Dependencies, licences, packages, and build scripts are verified.
- [ ] Timeouts, retries, concurrency, payloads, and resource use are bounded.
- [ ] Negative security tests and required automated scans pass.
- [ ] Security-relevant events are observable without leaking sensitive information.

### 32.5 Pull Request Preparation Checklist

- [ ] Why, what, how, scope, and exclusions are clear.
- [ ] Requirements, design, ADRs, and work items are linked.
- [ ] Evidence corresponds to the submitted revision.
- [ ] Risks, compatibility, migration, rollout, and rollback are explicit.
- [ ] High-risk areas and reviewer questions are highlighted.
- [ ] Required code owners and specialists are requested.

### 32.6 Commit Message Guidelines

- Give each commit one coherent purpose.
- Use the repository's approved message format.
- Explain intent and reason, not only changed filenames.
- Reference the work item or decision when required.
- Keep generated, migration, dependency, and lockfile changes intentional.
- Do not include secrets, customer data, misleading evidence, or temporary messages.
- Preserve a history that a reviewer can understand without hidden local context.

### 32.7 Traceability Matrix

| Source | Implementation Link | Evidence | Downstream Link |
|---|---|---|---|
| Requirement or acceptance criterion | Work item, component, file, or commit | Unit, integration, contract, or manual verification | Review and release |
| Technical design element | Implementation slice | Build, static, migration, or benchmark evidence | Review finding or approval |
| ADR or constraint | Code boundary or configuration | Architecture/design conformance check | Operational evidence |
| Risk or control | Mitigation code and test | Security, failure, recovery, or monitoring evidence | Risk acceptance or closure |

### 32.8 Coding Maturity Model

| Level | Characteristics |
|---|---|
| 1. Ad Hoc | Large changes, inconsistent tests, and review-dependent quality |
| 2. Repeatable | Basic plans, self-review, automated checks, and review packages |
| 3. Defined | Nine phases, gates, traceability, and proportionate evidence are standard |
| 4. Measured | Rework, escaped defects, validation, and maintainability improve the workflow |
| 5. Adaptive | Implementation depth and automation respond to risk and operational evidence |

### 32.9 Review Readiness Assessment

| Assessment Area | Ready When |
|---|---|
| Intent | Purpose, scope, design, and acceptance are clear |
| Change | Diff is focused, understandable, and complete |
| Evidence | Required checks pass on the submitted revision |
| Risk | Security, data, compatibility, performance, and operations are addressed |
| History | Commits are coherent and traceable |
| Documentation | Affected guidance and interfaces are current |
| Review | Owners, specialists, questions, rollout, and rollback are identified |

Any blocking gap means the change remains Draft.

### 32.10 Implementation Decision Matrix

| Decision | Default | Escalation Trigger |
|---|---|---|
| Reuse or create | Reuse a suitable existing capability | Existing capability violates current need or ownership |
| Simple or abstract | Use the simplest complete implementation | Proven repetition or stable variation requires abstraction |
| Local or shared | Keep responsibility at the owning boundary | Several consumers require consistent shared behaviour |
| Dependency or internal code | Prefer existing platform or approved dependency | New dependency provides clear value and passes review |
| Immediate or staged change | Prefer reversible, compatible delivery | Irreversible data, contract, or operational impact |
| Fix or redesign | Fix the shared root cause | Root cause changes approved design or architecture |

### 32.11 Deliverables Checklist

- [ ] Source code.
- [ ] Configuration and build changes.
- [ ] Migrations and infrastructure where applicable.
- [ ] Unit, integration, contract, and risk-specific tests.
- [ ] Documentation updates.
- [ ] Validation evidence.
- [ ] Coherent commit history.
- [ ] Review package and traceability.

### 32.12 Production Readiness Checklist

Coding does not approve production deployment, but implementation must not block downstream readiness.

- [ ] Required behaviour and quality thresholds are implemented.
- [ ] Compatibility, migration, rollback, and recovery are feasible.
- [ ] Configuration has safe defaults and environment separation.
- [ ] Logs, metrics, traces, health checks, and audit signals are implemented as designed.
- [ ] Security, privacy, dependency, and data controls have evidence.
- [ ] Build and tests are reproducible in the delivery pipeline.
- [ ] Operational documentation and support ownership are current.
- [ ] Known limitations, feature flags, conditions, and residual risks are visible.
- [ ] The review package provides what Testing and Deployment need next.

## 33. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.1.0 | 2026-07-30 | Invara Labs Engineering | Draft | Added coding governance, risk management, secure coding, human accountability, Standards integration, explicit documentation phase, and twelve implementation-readiness appendices |
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Coding Playbook with nine-phase implementation workflow, quality gates, executable deliverables, AI boundary, templates, examples, metrics, and enterprise appendices |

## 34. Summary

`PB-CODING` turns an approved technical design into review-ready software.

It requires engineers to:

- Understand before changing.
- Prepare a reproducible environment.
- Plan coherent implementation slices.
- Implement the smallest complete solution.
- Verify their own work.
- Produce automated evidence.
- Maintain traceability and commit quality.
- Submit a clear review package.
- Resolve findings without losing design intent.

Coding Principles explain what good code should embody. Standards define mandatory conventions. `PB-CODING` defines how engineers execute implementation work from approved design to independent code review.
