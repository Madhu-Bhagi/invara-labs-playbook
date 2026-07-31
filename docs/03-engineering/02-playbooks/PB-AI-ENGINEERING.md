---
title: AI Engineering Playbook
id: PB-AI-ENGINEERING
version: 1.3.13
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
  - ai
  - artificial-intelligence
  - ai-engineering
  - engineering
  - software-engineering
  - productivity
  - security
  - verification
  - playbook
related:
  - AP-001
  - AP-002
  - AP-003
  - AP-004
  - AP-005
  - AP-006
  - EP-001
  - PB-REQ
  - PB-ARCH
  - PB-TECH-DESIGN
  - PB-CODING
  - PB-CODE-REVIEW
  - PB-TESTING
  - PB-DEPLOYMENT
  - PB-OBSERVABILITY
  - PB-INCIDENT-MANAGEMENT
  - PB-CHANGE-MANAGEMENT
  - PB-MAINTENANCE
  - PB-PLATFORM-ENGINEERING
  - PB-SECURITY-ENGINEERING
  - PB-DATA-ENGINEERING
  - PB-API-MANAGEMENT
  - PB-DEVELOPER-EXPERIENCE
  - PB-AUTHORING
  - STD-REVIEW
  - STD-TRACEABILITY
  - STD-METADATA
  - STD-VERSIONING
  - TERM-STANDARD
  - REF-IDENTIFIERS
  - REF-TERMINOLOGY
  - REF-ACRONYMS
  - REF-AI-TOOLS
  - REF-PROMPT-PATTERNS
supersedes: null
superseded_by: null
---

# AI Engineering Playbook

> **The standard operating procedure for using Artificial Intelligence responsibly, securely, and effectively throughout the software engineering lifecycle while maintaining human accountability for every engineering decision and deliverable.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. When to Use This Playbook
6. Roles and Responsibilities
7. Inputs
8. Entry Criteria
9. AI Engineering Workflow
10. AI Engineering Lifecycle
11. Detailed Phase Activities
12. AI Engineering Concepts
13. AI Decision Framework
14. Deliverables
15. Quality Gates
16. AI Engineering Checklist
17. AI-Assisted Engineering Across the SDLC
18. AI Governance
19. AI Risk Management
20. Security, Privacy, and Intellectual Property
21. Human Accountability
22. Approved AI Capabilities
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

Artificial intelligence is a cross-cutting engineering capability. It may assist requirements analysis, architecture, technical design, coding, review, testing, documentation, deployment preparation, debugging, incident investigation, and continuous improvement.

AI does not create a separate delivery lifecycle. It participates inside the governed lifecycle:

```text
                 PB-AI-ENGINEERING
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
Requirements → Architecture → Technical Design → Coding
                                                │
                                                ▼
                                            Code Review
                                                │
                                                ▼
                                             Testing
                                                │
                                                ▼
                                            Deployment
                                                │
                                                ▼
                                           Observability
```

Every AI-generated output is a proposal until a named human verifies and accepts it. The confidence of the language, the reputation of the model, and the speed of generation are not evidence of correctness.

This playbook governs the full path from deciding whether AI is appropriate through preparing safe context, selecting an approved tool, generating output, verifying it, conducting security and engineering validation, accepting or rejecting it, and recording traceability where required.

## 2. Purpose

This playbook helps teams:

- Use AI where it improves engineering outcomes rather than merely increasing output.
- Select only tools approved for the task and information involved.
- Prepare accurate, minimal, and safely disclosed context.
- Write task briefs and prompts with explicit objectives, constraints, and acceptance criteria.
- Treat hallucinations, omissions, insecure suggestions, and outdated information as expected risks.
- Verify AI-assisted decisions, code, tests, documentation, queries, and operational guidance.
- Apply security, privacy, intellectual-property, and customer obligations.
- Review AI-generated code to the same or higher standard as human-authored code.
- Preserve human understanding and accountability.
- Record material AI contributions when risk, policy, or governance requires it.
- Improve AI-assisted engineering through measured outcomes and review evidence.

## 3. Objectives

Following this playbook should produce:

- A defined AI task with a named human owner.
- A risk and information-classification decision.
- An approved tool and permitted usage mode.
- A minimal, accurate context package.
- A prompt or task brief with success criteria.
- AI output clearly treated as untrusted until verified.
- Verification evidence proportionate to the output and risk.
- Security and engineering review where required.
- An explicit accept, revise, reject, or escalate decision.
- Traceability for material AI contributions.
- Reusable learning that improves future work without exposing protected information.

The outcome is not “AI was used.” The outcome is engineering work that is understood, safe, maintainable, and supported by evidence.

## 4. Scope

### In Scope

This playbook governs AI assistance for:

- Requirements discovery, refinement, and consistency analysis.
- Architecture exploration, trade-off analysis, ADR drafting, and diagram preparation.
- Technical design, interface design, API design, data modelling, and edge-case analysis.
- Coding, refactoring, code explanation, dependency analysis, and migration assistance.
- Code review preparation and defect discovery.
- Unit, integration, contract, performance, and security test generation.
- Documentation authoring, summarisation, terminology checking, and traceability.
- SQL, infrastructure, configuration, build, and CI/CD assistance.
- Debugging, incident investigation, log analysis, and root-cause hypothesis generation.
- Operational query, dashboard, alert, and runbook drafting.
- Engineering research and learning.

### Out of Scope

This playbook does not:

- Approve a specific vendor or product.
- Replace the authoritative organisation tool register.
- Permit confidential or customer data to be disclosed.
- Delegate decisions, risk acceptance, approval, or production authority to AI.
- Replace domain playbooks, standards, security review, peer review, or testing.
- Permit autonomous production changes unless separately authorised and controlled.
- Treat generated tests as proof that generated implementation is correct.
- Govern AI features delivered to customers; those require product, legal, security, data, and model-specific governance.

### Proportionate Application

| Usage Profile | Example | Expected Control |
|---|---|---|
| Low risk | Rephrasing public documentation | Approved tool, human review |
| Moderate risk | Drafting internal code or tests from non-sensitive context | Task brief, source review, tests, peer review |
| High risk | Authentication, data migration, security, financial logic, production incident analysis | Formal risk classification, restricted tool, specialist review, independent evidence, traceability |
| Prohibited | Sending secrets, personal data, customer-confidential material, or unapproved source code to an unauthorised tool | Stop, protect information, and escalate |

## 5. When to Use This Playbook

Apply this playbook whenever AI influences an engineering artefact, decision, implementation, verification activity, or operational action.

Use AI when:

- The task has a clear human owner and verifiable outcome.
- AI can reduce repetitive effort, broaden options, improve consistency, or accelerate learning.
- Required context can be shared lawfully and safely.
- An approved tool supports the information classification and task.
- The team has time and capability to verify the output.

Do not use AI when:

- The required context cannot be safely disclosed.
- No approved tool supports the task.
- The output cannot be independently verified.
- The engineer cannot understand or maintain the result.
- Automation would bypass a required approval, separation of duties, or audit control.
- The cost of plausible error exceeds the available validation.

AI use is optional unless an approved process explicitly requires it. Engineers may choose a non-AI method when it is safer, clearer, faster, or easier to verify.

## 6. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| AI Task Owner | Defines the task, classifies risk, prepares context, verifies output, and owns acceptance |
| Engineering Lead | Confirms proportionate controls, capability, review, and escalation |
| Domain Owner | Validates domain correctness, constraints, trade-offs, and maintainability |
| Security or Privacy Reviewer | Evaluates information disclosure, tool suitability, threats, privacy, secrets, and residual risk |
| Data Owner | Authorises permitted data use, minimisation, anonymisation, retention, and lineage |
| Tool Owner | Maintains approval status, permitted uses, configuration, access, retention, and known limitations |
| Reviewer | Reviews accepted output and evidence without lowering normal engineering standards |
| Quality Engineer | Confirms verification strategy, test independence, coverage, and evidence |
| Legal, Compliance, or Customer Authority | Decides contractual, licensing, regulatory, or customer-specific constraints |
| Governance Owner | Defines organisation-wide AI policy, exceptions, audit needs, and lifecycle controls |

### Responsibility Rules

- A named human owns every AI-assisted artefact.
- Tool approval and output approval are separate decisions.
- The person generating an output must not be the only source of evidence for high-risk work.
- AI cannot approve its own output, accept risk, merge code, or authorise deployment.
- Reviewers assess the work, not whether it was produced quickly.
- Unclear authority, data rights, or tool status requires escalation before use.

## 7. Inputs

| Input | Required Information |
|---|---|
| Engineering task | Problem, intended outcome, owner, deadline, and downstream use |
| Acceptance criteria | Observable conditions that determine whether output is usable |
| Risk classification | Impact of incorrect, insecure, biased, leaked, or unavailable output |
| Information classification | Public, internal, confidential, restricted, personal, regulated, or customer-controlled status |
| Approved tool register | Allowed tools, models, modes, data classes, retention, regions, and restrictions |
| Authoritative sources | Requirements, code, architecture, standards, contracts, tests, runbooks, and current documentation |
| Constraints | Security, privacy, legal, licensing, customer, technical, cost, and time limits |
| Verification plan | Tests, review, source checks, benchmarks, security checks, or experiments |
| Traceability rule | Whether prompts, outputs, decisions, model/tool details, or contribution records must be retained |

Do not begin from AI output when an authoritative source is available. Begin from the source and use AI to assist analysis or transformation.

## 8. Entry Criteria

Before using AI, confirm:

- A human task owner is named.
- The problem and expected output are clear.
- The business and technical sources are available.
- The impact of error is understood.
- The information has been classified.
- The proposed tool and usage mode are approved.
- Context can be minimised and safely shared.
- Verification can be performed independently.
- Required reviewers and traceability are known.
- A non-AI fallback exists for tool failure or unacceptable output.

If any criterion is unknown, pause the AI interaction and resolve it. Convenience does not authorise disclosure or weaken verification.

## 9. AI Engineering Workflow

| Phase | Goal | Exit Decision |
|---|---|---|
| 1. Understand the Engineering Task | Establish the problem, owner, sources, constraints, desired output, and success criteria | Is the task understood well enough to evaluate AI use? |
| 2. Determine AI Suitability | Classify value, risk, information, verification, and authority | Is AI appropriate and controllable for this task? |
| 3. Prepare Context | Gather authoritative, minimal, accurate, and permitted context | Is the context sufficient and safe to disclose? |
| 4. Select AI Tools | Choose an approved tool, model, mode, and configuration | Is this capability authorised and fit for the task? |
| 5. Generate AI Output | Prompt deliberately and preserve assumptions and alternatives | Is the candidate complete enough to evaluate? |
| 6. Validate and Verify | Check claims, logic, sources, behaviour, edge cases, and engineering fit | Is correctness supported by independent evidence? |
| 7. Security and Compliance Review | Check disclosure, controls, threats, dependencies, privacy, licensing, and obligations | Is the interaction and output safe and compliant? |
| 8. Human Approval | Accept, revise, reject, or escalate through a qualified human decision | May the output enter the governed engineering workflow? |
| 9. Capture Knowledge and Continuous Improvement | Retain required traceability and improve future practice | Can the contribution, evidence, and lessons be understood later? |

```text
Understand Engineering Task
       │
       ▼
Determine AI Suitability
       │
       ▼
Prepare Context
       │
       ▼
Select Approved Tool
       │
       ▼
Generate AI Output
       │
       ▼
Validate and Verify
       │
       ▼
Security and Compliance Review
       │
       ▼
Human Approval
       │
       ▼
Capture Knowledge and Improve
```

An output may return to any earlier phase. Repeated failure should change the task decomposition, context, tool, or non-AI approach rather than produce endless prompt iteration.

## 10. AI Engineering Lifecycle

AI-assisted work follows the same controlled lifecycle as other engineering work:

```text
Proposed Use
      │
      ▼
Classified and Authorised
      │
      ▼
Generated
      │
      ▼
Verified and Reviewed
      │
      ▼
Accepted into Governed Artefact
      │
      ▼
Maintained with the System
      │
      ▼
Superseded or Retired
```

The accepted artefact, not the transient AI conversation, becomes the source of truth. Retain prompts and outputs only when policy, risk, auditability, or reproducibility requires them. Do not create a shadow documentation system inside an AI tool.

Changes in models, providers, terms, retention, integrations, or security posture may invalidate prior approval. Tool owners must review approved usage at a defined cadence and after material change.

## 11. Detailed Phase Activities

### Phase 1: Understand the Engineering Task

**Objective:** Establish the engineering problem and intended outcome without assuming AI is the solution.

**Activities:**

1. State the engineering problem without assuming AI is the solution.
2. Name the human owner and downstream consumer.
3. Define the desired output format and acceptance criteria.
4. Identify authoritative sources, constraints, dependencies, and required expertise.
5. Separate facts, assumptions, unknowns, and decisions already made.
6. Identify downstream engineering and customer impact.
7. Define what evidence will demonstrate success.

**Outputs:**

- AI task brief.
- Acceptance and verification criteria.
- Authoritative source and constraint list.

**Exit criteria:**

- The task is bounded and verifiable.
- A human owns the result.
- Sources, constraints, and downstream use are understood.

### Phase 2: Determine AI Suitability

**Objective:** Decide whether AI adds value and whether its risks can be controlled.

**Activities:**

1. Compare AI assistance with a direct engineering approach.
2. Classify the impact of incorrect, incomplete, insecure, biased, or leaked output.
3. Classify the information and authority the task requires.
4. Confirm the result can be independently verified.
5. Identify qualified reviewers and approval authority.
6. Define a non-AI fallback.
7. Choose Proceed, Use Non-AI Method, Narrow Scope, or Escalate.

**Outputs:**

- Suitability and risk decision.
- Required control level.
- Verification and fallback plan.

**Exit criteria:**

- AI has a clear engineering benefit.
- Information, verification, and authority are controllable.
- The owner can stop or fall back safely.

### Phase 3: Prepare Context

**Objective:** Provide enough correct context for useful assistance while disclosing the least information necessary.

**Activities:**

1. Identify authoritative requirements, code, decisions, standards, and examples.
2. Classify every context source.
3. Remove secrets, tokens, personal data, customer identifiers, and unrelated proprietary information.
4. Anonymise or synthesise data where permitted and effective.
5. Reduce the context to the minimum needed for the task.
6. Mark assumptions, unknowns, conflicting sources, and version boundaries.
7. Define retention and confirm that the prepared context may be processed.

**Outputs:**

- Approved context package.
- Source and assumption list.
- Disclosure and retention decision.

**Exit criteria:**

- Context is authoritative, relevant, current, minimal, and permitted.
- Protected information is excluded or handled under explicit approval.
- Missing context is visible rather than invented.

### Phase 4: Select AI Tools

**Objective:** Select an approved capability whose controls match the task and information.

**Activities:**

1. Consult the authoritative tool register.
2. Confirm permitted uses, information classes, users, regions, retention, training use, and integrations.
3. Evaluate capability, limitations, context size, reproducibility, cost, and availability.
4. Select enterprise or restricted modes when required.
5. Disable unnecessary connectors, browsing, execution, or retention.
6. Confirm access control, logging, incident response, and revocation.
7. Request an exception or use a non-AI method when no approved tool is suitable.

**Outputs:**

- Tool and mode selection.
- Configuration and restriction record where required.
- Approval or exception reference.

**Exit criteria:**

- Tool approval is current and task-specific.
- Intended context and actions are permitted.
- Known limitations fit the verification plan.

### Phase 5: Generate AI Output

**Objective:** Produce a candidate through clear, bounded, and iterative interaction.

**Activities:**

1. Provide the objective, context, constraints, acceptance criteria, and output format.
2. Separate facts from assumptions and ask the tool to do the same.
3. Request alternatives and trade-offs for consequential choices.
4. Require grounding in supplied or approved sources where possible.
5. Break complex work into reviewable stages.
6. Inspect intermediate output before granting more context or action.
7. Stop when iteration no longer improves verifiable quality.

**Outputs:**

- Candidate AI-generated artefact.
- Declared assumptions and limitations.
- Alternatives or unresolved questions where relevant.

**Exit criteria:**

- The candidate is concrete enough to verify.
- Its provenance and assumptions are distinguishable.
- It remains unaccepted pending validation.

### Phase 6: Validate and Verify

**Objective:** Establish correctness and engineering fitness through evidence independent of the generated claim.

**Activities:**

1. Compare output with authoritative requirements, code, contracts, and documentation.
2. Verify APIs, behaviour, commands, citations, versions, and configuration against primary sources.
3. Execute tests, static analysis, type checks, builds, queries, benchmarks, or prototypes.
4. Test normal, boundary, invalid, failure, concurrency, and recovery behaviour.
5. Check omissions, contradictions, invented facts, and stale assumptions.
6. Apply domain standards and confirm architecture, maintainability, performance, reliability, and operability.
7. Record evidence, corrections, and unresolved uncertainty.

**Outputs:**

- Verification and engineering review record.
- Corrected candidate.
- Evidence and remaining limitations.

**Exit criteria:**

- Material claims and behaviours have independent evidence.
- Applicable engineering quality gates pass.
- Unverified content is rejected or isolated.

### Phase 7: Security and Compliance Review

**Objective:** Ensure the interaction and candidate do not compromise trust or obligations.

**Activities:**

1. Confirm no prohibited information was disclosed.
2. Review code and configuration for vulnerabilities, unsafe defaults, secrets, and excessive privilege.
3. Review dependencies, licences, packages, URLs, commands, and infrastructure changes.
4. Check privacy, retention, residency, consent, intellectual property, customer, and regulatory obligations.
5. Evaluate prompt injection and untrusted retrieved content.
6. Confirm privileged or destructive actions remain under human control.
7. Report suspected disclosure or unsafe execution through the incident process.

**Outputs:**

- Security and compliance review record.
- Findings and remediation.
- Incident or exception record where required.

**Exit criteria:**

- Disclosure and output risks are acceptable within authority.
- Blocking findings are resolved.
- Suspected compromise is contained and escalated.

### Phase 8: Human Approval

**Objective:** Make an explicit human decision about the candidate.

**Possible outcomes:**

- **Accept** — evidence is sufficient and the output enters the normal workflow.
- **Revise** — bounded issues can be corrected and reverified.
- **Reject** — the output is incorrect, unsafe, unnecessary, or uneconomical to repair.
- **Escalate** — authority, risk, policy, customer obligation, or architectural impact exceeds the owner.

**Activities:**

1. Review evidence, findings, residual uncertainty, and downstream impact.
2. Confirm the owner understands and can explain the result.
3. Obtain required domain, peer, security, quality, or governance approval.
4. Record the responsible human decision-maker.
5. Remove generated content that adds no maintained value.
6. Integrate accepted work through normal version control and review.
7. Prevent rejected or escalated output from entering delivery.

**Outputs:**

- Disposition decision.
- Accepted governed artefact or rejected candidate.
- Conditions and escalation references.

**Exit criteria:**

- A named human owns the decision.
- Accepted output meets the same standard as other work.
- Rejected or escalated output cannot enter delivery accidentally.

### Phase 9: Capture Knowledge and Continuous Improvement

**Objective:** Preserve required accountability and improve practice without retaining unnecessary sensitive data.

**Activities:**

1. Link accepted work to its requirements, design, implementation, tests, and review evidence.
2. Record AI contribution details when required by risk or policy.
3. Capture the tool, model or service class, date, owner, purpose, and verification method at the required level.
4. Retain prompts or raw outputs only when authorised and necessary.
5. Record useful prompt patterns, verification gaps, or tool limitations without protected content.
6. Update the tool owner when material defects or unsafe behaviour are discovered.
7. Measure outcomes and improve the workflow.

**Outputs:**

- Traceability record.
- AI contribution record where required.
- Approved reusable learning.
- Tool or process feedback.

**Exit criteria:**

- Future reviewers can understand ownership and evidence.
- Retention follows policy and least-data principles.
- Learning improves practice without creating a new information risk.

## 12. AI Engineering Concepts

### AI Output Is Untrusted Input

Treat AI output like input from an unknown external source. Validate it before it affects decisions, repositories, systems, customers, or production.

### Human Accountability

The accepting engineer owns:

- Problem selection.
- Context disclosure.
- Tool choice.
- Verification depth.
- Engineering decision.
- Integrated output.
- Downstream consequences.

“The AI produced it” is never an ownership statement.

### Approved Tool

An approved tool is authorised for a defined combination of:

- User group.
- Use case.
- Information classification.
- Model or capability.
- Data retention and training settings.
- Region and legal terms.
- Connectors and execution permissions.
- Review period.

Approval for public brainstorming does not imply approval for proprietary source code or customer data.

### Context Management

Good context is authoritative, relevant, minimal, current, structured, and permitted. More context may increase disclosure, confusion, prompt-injection exposure, and cost without improving the result.

### Prompt Engineering

A prompt is a task specification. It should communicate:

- Objective.
- Authoritative context.
- Constraints.
- Assumptions and unknowns.
- Desired output.
- Acceptance criteria.
- Required evidence or source boundaries.

Prompt quality does not remove the need for verification.

### Hallucination

A hallucination is generated content presented without reliable grounding. Common forms include:

- Invented APIs, packages, flags, citations, or files.
- Incorrect claims about current code.
- Fabricated test results or command execution.
- Confident but invalid reasoning.
- Details inferred beyond the supplied evidence.

The control is independent verification, not asking the same model whether it is correct.

### Automation Boundary

Capability and authority are different. A tool may be capable of editing files, executing commands, opening pull requests, or changing infrastructure. It may do so only within explicitly granted scope and existing approval controls.

### Verification Independence

Verification is stronger when its source differs from generation:

- Generated code checked by human reasoning, compiler, static analysis, and tests.
- Generated test cases checked against independent requirements and additional human-selected cases.
- Generated citations checked against primary sources.
- Generated queries tested against controlled data and expected results.

### Traceability Threshold

Record AI involvement when it materially affects:

- An architecture or technical decision.
- Security, privacy, compliance, financial, or safety-sensitive work.
- Substantial code, migrations, infrastructure, or production operations.
- Customer-facing representations.
- An artefact whose provenance is contractually or legally relevant.

Routine spelling assistance may need no separate record unless policy requires it.

## 13. AI Decision Framework

Use five questions before AI assistance:

1. **Value:** Will AI improve quality, learning, coverage, or cycle time?
2. **Permission:** May this information and task be processed by this tool?
3. **Capability:** Is the tool fit for the domain and output?
4. **Verification:** Can the result be independently tested or reviewed?
5. **Accountability:** Is a qualified human prepared to own the result?

| Permission | Verification | Decision |
|---|---|---|
| Permitted | Strong | Proceed with proportionate controls |
| Permitted | Weak | Narrow the task, add evidence, or use a non-AI approach |
| Unclear | Any | Stop and obtain approval |
| Prohibited | Any | Do not use AI |

### Risk Factors

Increase control when work involves:

- Secrets, personal data, customer information, or proprietary code.
- Authentication, authorisation, cryptography, payments, safety, or legal rules.
- Data migration, deletion, irreversible change, or production execution.
- Public APIs, shared contracts, or cross-team architecture.
- New dependencies, external content, agents, connectors, or command execution.
- Weak tests, poor observability, missing domain expertise, or unclear ownership.

### Escalate When

- Tool approval or information rights are unclear.
- Required disclosure exceeds the tool’s permitted classification.
- The engineer cannot verify or explain the result.
- Output proposes an architectural deviation.
- Security or legal obligations are uncertain.
- AI behaviour suggests data leakage, prompt injection, unsafe execution, or compromised credentials.
- Autonomous action would exceed existing engineering authority.

## 14. Deliverables

| Deliverable | Minimum Content | Required When |
|---|---|---|
| AI Task Brief | Owner, task, benefit, output, criteria, risk, verification | Every material AI task |
| Context and Disclosure Record | Sources, classification, minimisation, permission | Internal or protected context is involved |
| Tool Selection Record | Approved tool, mode, restrictions, register reference | Moderate or high-risk usage |
| Prompt or Instruction Set | Objective, context, constraints, format, evidence needs | Reuse, review, or audit matters |
| Candidate Output | Clearly unaccepted output and declared assumptions | Every AI interaction |
| Verification Record | Sources, tests, checks, findings, limitations | Before acceptance |
| Security and Privacy Review | Disclosure and output risk assessment | Sensitive or high-risk work |
| Engineering Review Record | Domain and standards validation | Material engineering output |
| Disposition Record | Accept, revise, reject, or escalate with owner | Every material output |
| AI Contribution Record | Tool class, purpose, owner, evidence, linked artefact | Policy or traceability threshold applies |
| Learning Record | Safe reusable pattern or limitation | A durable lesson is found |

These records may be combined with existing design, code-review, test, or decision artefacts. Do not duplicate authoritative evidence.

## 15. Quality Gates

### Gate A: Task and Authority Ready

- The task, owner, value, output, and acceptance criteria are clear.
- Risk and information classifications are complete.
- AI is appropriate and a fallback exists.

### Gate B: Context and Tool Ready

- Context is authoritative, minimal, current, and permitted.
- The tool, model, mode, connectors, and retention are approved.
- Constraints and limitations are explicit.

### Gate C: Verification Ready

- Candidate output is separated from accepted work.
- Material claims and behaviours have independent evidence.
- Hallucinations, omissions, edge cases, and outdated assumptions were checked.

### Gate D: Security and Engineering Ready

- Disclosure, dependency, execution, security, privacy, licensing, and operational concerns pass review.
- The owner understands the output.
- Domain standards and normal quality gates pass.

### Gate E: Acceptance and Traceability Ready

- A human disposition and residual-risk owner are recorded.
- Accepted work enters normal version control, review, testing, and approval.
- Required AI contribution traceability is complete.
- Unnecessary prompts and outputs are not retained.

## 16. AI Engineering Checklist

### Before Use

- [ ] I can state why AI is useful for this task.
- [ ] A qualified human owns the result.
- [ ] Error impact and information sensitivity are classified.
- [ ] The selected tool and mode are approved.
- [ ] I can verify the result independently.

### Context and Prompt

- [ ] Context comes from authoritative sources.
- [ ] Secrets, personal data, and unrelated confidential content are excluded.
- [ ] The prompt defines objective, constraints, assumptions, output, and success.
- [ ] The task is small enough to review.
- [ ] Tool access and connectors are limited to what is needed.

### Verification

- [ ] I understand and can explain the output.
- [ ] Claims, APIs, citations, commands, and versions were checked.
- [ ] Code builds and passes meaningful independent tests.
- [ ] Normal, edge, failure, security, and recovery cases were considered.
- [ ] Generated tests do not simply confirm generated implementation.

### Acceptance

- [ ] Security, privacy, licensing, and dependency concerns are resolved.
- [ ] Normal peer and domain review is complete.
- [ ] The disposition is human-owned.
- [ ] Required traceability is recorded.
- [ ] Rejected or unnecessary generated content is excluded.

## 17. AI-Assisted Engineering Across the SDLC

AI is a supporting capability across the software development lifecycle (SDLC), not a substitute lifecycle or an approval authority. Each domain playbook remains authoritative for its activity.

| Lifecycle Activity | AI May Assist | Human Must |
|---|---|---|
| Requirements | Summarise, identify ambiguity, generate questions, check consistency | Validate user need, priority, acceptance, and stakeholder intent |
| Architecture | Generate options, draft views and ADRs, identify risks | Select trade-offs, validate evidence, approve architecture |
| Technical Design | Draft components, contracts, models, sequences, and edge cases | Confirm fit with architecture, codebase, security, and operations |
| Coding | Generate scaffolding, implementations, refactors, explanations | Understand, simplify, test, review, and own every change |
| Code Review | Find suspicious patterns, omissions, and standards gaps | Judge correctness, intent, risk, and merge readiness |
| Testing | Generate cases, data, mocks, and assertions | Derive independent coverage from requirements and risk |
| Security | Suggest threats, checks, and remediation options | Protect context, validate controls, and accept residual risk |
| Documentation | Draft, restructure, summarise, and check terminology | Verify truth, audience fit, sources, and lifecycle |
| CI/CD | Draft pipelines, policies, scripts, and diagnostics | Validate permissions, supply chain, environments, and rollback |
| Debugging | Summarise evidence and propose hypotheses | Reproduce, isolate root cause, test the fix, prevent recurrence |
| Incident Response | Correlate authorised evidence and draft timelines | Control disclosure, lead response, verify facts, authorise actions |
| Operations | Draft queries, dashboards, alerts, and runbooks | Validate signals, thresholds, access, and operational action |

Domain-specific playbooks remain authoritative for their activities. This playbook supplies the common AI control layer.

## 18. AI Governance

AI governance establishes who may use AI, for which purposes, with what information, under which controls, and with what evidence. It applies to chat interfaces, editors, command-line tools, platform integrations, agents, APIs, and embedded capabilities.

### Governance Requirements

- Every material AI-assisted artefact has a named human owner.
- Capabilities are approved for specific users, purposes, information classes, and actions.
- Access follows least privilege and can be revoked promptly.
- High-risk use separates generation, specialist review, and approval.
- Exceptions are time-bounded, recorded, and approved by the correct authority.
- Provider, model, term, retention, connector, or execution changes trigger review.
- AI incidents follow security and engineering incident processes.
- Accepted outputs enter the normal artefact lifecycle; AI conversations do not become a shadow source of truth.

### Governance Decision Rights

| Decision | Accountable Authority |
|---|---|
| Whether AI adds value | AI Task Owner |
| Whether information may be disclosed | Data, Security, Privacy, Legal, or Customer Authority |
| Whether a capability is approved | Capability Owner and Governance Authority |
| Whether output is technically correct | Domain Owner and qualified reviewers |
| Whether residual risk is accepted | Authorised human risk owner |
| Whether work may merge or deploy | Existing engineering and release authority |
| Whether an exception is allowed | Governance authority defined by policy |

## 19. AI Risk Management

AI risk management begins during suitability assessment and continues through verification, approval, operation, and learning.

| Risk | Typical Failure | Required Treatment |
|---|---|---|
| Hallucination | Invented facts, APIs, files, citations, or execution results | Primary-source checks and independent evidence |
| Prompt injection | Untrusted content redirects the tool or exposes context | Treat retrieved content as hostile; isolate instructions and restrict access |
| Data leakage | Protected context enters an unauthorised service, log, or output | Classification, minimisation, approved capability, incident response |
| Security weakness | Insecure code, configuration, permissions, or dependencies | Security review, scanning, testing, and least privilege |
| Privacy violation | Personal data is used beyond purpose, consent, or retention | Privacy authority, minimisation, lawful purpose, deletion controls |
| Copyright or IP risk | Protected material is reproduced or ownership is unclear | Source and licence review; legal escalation where uncertain |
| Licensing risk | Generated code introduces incompatible terms or packages | Dependency and licence validation |
| Bias | Output disadvantages users or encodes unsupported assumptions | Representative review, domain evidence, impact assessment |
| Outdated knowledge | Advice conflicts with current versions or policy | Version boundaries and current authoritative sources |
| Model drift | Behaviour changes after model or provider updates | Approval triggers, regression evaluation, and controlled rollout |
| Context loss | Important constraints disappear across long interactions | Bounded tasks, source references, checkpoints, and revalidation |
| Overreliance | Engineers accept output without understanding | Human explanation, independent review, and skills development |

### Risk Treatment

1. Identify the risk and affected assets.
2. Estimate impact, likelihood, detectability, and reversibility.
3. Avoid prohibited use; reduce exposure through scope, context, and capability controls.
4. Define verification and specialist review.
5. Name the residual-risk owner.
6. Monitor accepted work and feed failures into capability and process review.

## 20. Security, Privacy, and Intellectual Property

AI interactions create two separate security surfaces:

1. **Input risk** — information disclosed through prompts, files, retrieval, connectors, logs, or tool access.
2. **Output and action risk** — insecure code, malicious retrieved content, unsafe commands, new dependencies, excessive access, or autonomous changes.

### Mandatory Controls

- Classify information before disclosure.
- Never submit secrets, credentials, personal data, customer-confidential information, production records, or restricted source code unless the exact tool and mode are authorised for it.
- Minimise, redact, anonymise, or synthesise context where permitted.
- Treat retrieved web pages, repository content, tickets, emails, and documents as potentially hostile prompt-injection sources.
- Restrict tool access, connectors, execution, network access, repositories, and environments to the task.
- Review generated dependencies, licences, URLs, scripts, commands, infrastructure, and security controls.
- Require human confirmation for privileged, destructive, irreversible, customer-visible, or production actions.
- Report suspected disclosure, unsafe execution, or compromised access immediately.

### Privacy and Customer Trust

Engineers must respect purpose limitation, consent, retention, deletion, residency, contractual obligations, and customer instructions. Tool convenience never overrides these obligations. When rights or policy are unclear, stop and obtain authoritative guidance.

### Intellectual Property

- Do not disclose trade secrets, NDA material, customer source code, export-controlled data, or third-party confidential content without explicit authority.
- Verify ownership, provenance, licence compatibility, attribution, and redistribution obligations.
- Treat generated code as requiring the same dependency, licence, security, and originality review as other external input.
- Do not request or accept reproduction of protected material when rights are absent.
- Escalate uncertain training-data, output-ownership, patent, copyright, or customer-contract questions.

## 21. Human Accountability

Human accountability is the boundary between generated content and accepted engineering work.

Humans remain responsible for:

- Requirements and acceptance criteria.
- Architecture and technical design.
- Source code, dependencies, data, and configuration.
- Security, privacy, intellectual property, and compliance.
- Test strategy, coverage, and evidence.
- Deployment approval and change control.
- Production operations, incident decisions, and risk acceptance.

### Verification Principles

- The accepting engineer must understand and be able to explain the output.
- Verification must trace to requirements, architecture, standards, and real system behaviour.
- Evidence should be independent of the generation path.
- Verification depth follows risk, reversibility, and information sensitivity.
- High-risk work requires qualified specialist and peer review.
- Unverifiable output must be rejected, narrowed, or escalated.

### Verification Methods

| Output | Human Verification |
|---|---|
| Factual statement | Check authoritative primary source and applicable version |
| Requirement summary | Compare with source and obtain stakeholder confirmation |
| Architecture or design | Validate drivers, constraints, alternatives, evidence, and domain review |
| Code | Understand logic; compile; run static, security, and independent behavioural tests |
| Test | Derive expected behaviour from requirements; add human-selected negative cases |
| SQL or migration | Inspect plan, locking, transactions, data integrity, reconciliation, and rollback |
| Dependency | Confirm existence, ownership, version, licence, security, maintenance, and necessity |
| Command or infrastructure | Use controlled environment, least privilege, dry run, policy checks, and rollback |
| Incident hypothesis | Verify against timeline, telemetry, reproduction, and alternative hypotheses |
| Documentation | Check sources, terminology, links, audience fit, and lifecycle metadata |

AI self-critique may generate useful questions. It is not independent approval.

> **AI assists. Engineers decide, approve, operate, and remain accountable.**

## 22. Approved AI Capabilities

An approved capability is the intersection of an authorised engineering purpose, permitted information, an approved service mode, bounded actions, and proportionate human verification.

Typical capabilities may include:

- Requirements refinement and consistency analysis.
- Architecture brainstorming and option drafting.
- Technical-design, API, and data-model drafting.
- Code generation, explanation, and refactoring.
- Code-review preparation and defect discovery.
- Test generation and coverage analysis.
- Documentation and knowledge synthesis.
- Debugging, root-cause hypotheses, and authorised log summarisation.
- SQL, CI/CD, and infrastructure generation.
- Threat-modelling and security-analysis assistance.

This list is not blanket permission. Every use passes the nine-phase workflow. The changeable catalogue of approved services, models, modes, data rules, connectors, and restrictions belongs in [`REF-AI-TOOLS`](../04-reference/REF-AI-TOOLS.md). Reusable prompt patterns belong in [`REF-PROMPT-PATTERNS`](../04-reference/REF-PROMPT-PATTERNS.md).

## 23. Common Mistakes

### Trusting Fluency

Clear writing and confident code can still be wrong. Require evidence.

### Sharing Too Much Context

Large context dumps increase disclosure and confusion. Share the least authorised information needed.

### Using an Approved Tool for an Unapproved Purpose

Approval is scoped. Public research approval does not permit customer data, proprietary code, or production access.

### Accepting Code That Cannot Be Explained

Generated code becomes team-owned code. If the engineer cannot explain it, it is not ready.

### Letting AI Generate Both the Answer and All Evidence

Tests derived only from the same generated assumptions may miss the same defect. Add independent requirements and human-selected cases.

### Prompting Around a Poorly Defined Problem

More iterations do not fix missing objectives or authority. Return to the task definition.

### Treating AI as a Reviewer of Itself

Self-critique may help exploration but is not independent review.

### Adding Unnecessary Complexity

AI often produces abstractions, dependencies, and speculative handling. Remove anything not required by the real problem.

### Fabricated Sources and Execution

Never assume a cited page exists or a claimed command ran. Check directly.

### Bypassing Normal Workflow

AI speed does not bypass architecture, design, review, testing, security, deployment, or change controls.

### Retaining Every Conversation

Unnecessary retention creates cost, noise, and information risk. Preserve governed artefacts and required evidence.

### Measuring Lines Generated

Output volume rewards complexity. Measure quality, rework, defects, learning, and customer outcomes.

## 24. Best Practices

- Define the problem and verification plan before opening the tool.
- Use the existing codebase and authoritative documents as the starting point.
- Give AI one bounded, reviewable task at a time.
- Ask for assumptions, alternatives, failure modes, and uncertainties.
- Prefer primary sources for technical and legal claims.
- Keep generated output visibly unaccepted until evidence is complete.
- Use compilers, tests, scanners, benchmarks, and real systems as evidence.
- Apply stronger controls to irreversible, sensitive, or high-impact work.
- Remove generated complexity and comments that do not aid maintenance.
- Use AI to improve understanding, not avoid it.
- Share safe reusable patterns through governed templates.
- Preserve a non-AI path for critical work and tool outages.

## 25. Templates

### AI Task Brief

```markdown
# AI Task Brief

Owner:
Engineering activity:
Problem:
Why AI is useful:
Desired output:
Authoritative sources:
Constraints:
Acceptance criteria:
Risk classification:
Information classification:
Approved tool and mode:
Verification plan:
Required reviewers:
Traceability requirement:
Fallback:
```

### Context Preparation Record

| Field | Content |
|---|---|
| Sources | Authoritative files, records, links, or datasets |
| Classification | Highest information classification |
| Removed | Secrets, identifiers, personal data, unrelated content |
| Transformation | Redaction, anonymisation, synthesis, minimisation |
| Permission | Policy, customer, data-owner, or exception reference |
| Assumptions | Missing or uncertain context |
| Retention | Whether context or conversation may be retained |

### Prompt Structure

```text
Role or perspective:
Objective:
Authoritative context:
Known facts:
Assumptions and unknowns:
Constraints:
Tasks:
Required output format:
Acceptance criteria:
Sources or evidence to use:
Actions not permitted:
```

### Verification Record

```markdown
## Verification

Output reviewed:
Human owner:
Claims checked:
Authoritative sources:
Commands and tests executed:
Edge and failure cases:
Security and privacy checks:
Independent reviewer:
Findings and corrections:
Known limitations:
Evidence links:
Disposition recommendation:
```

### AI Contribution Record

| Field | Content |
|---|---|
| Artefact | Governed output receiving the contribution |
| Owner | Human accountable for acceptance |
| Purpose | Task AI assisted |
| Tool class | Approved service or capability; exact model when required |
| Date | Date of material use |
| Contribution | Summary, not raw sensitive content |
| Verification | Evidence and reviewers |
| Disposition | Accepted, revised, rejected, or escalated |
| Retention | Location and period for required records |

## 26. Examples

### Example: AI-Assisted API Implementation

An engineer needs to implement an approved order-status endpoint.

1. The engineer creates a task brief from the approved TDD and API contract.
2. The context contains the relevant module, interface, validation rules, coding standards, and tests. Customer data and unrelated source code are excluded.
3. An approved enterprise coding assistant is selected.
4. AI drafts the handler and unit tests.
5. The engineer identifies an invented helper and replaces it with the existing repository function.
6. Independent contract tests cover valid, missing, unauthorised, stale, and dependency-failure cases.
7. Static analysis and peer review find an excessive data field in logs; it is removed.
8. The engineer accepts the corrected implementation and links it to the TDD and tests.

AI reduced drafting time. Existing code discovery, verification, security review, and human ownership made the result acceptable.

### Example: Rejected Production Debugging Use

An engineer considers pasting a production database export into a public AI service to diagnose a customer issue.

The data contains personal and customer-confidential information. The tool is not approved for that classification. The engineer rejects the AI approach, follows incident controls, creates a sanitised reproduction, and uses an approved restricted tool only after authorisation.

The decision protects trust even though it may take longer.

### Example: Architecture Exploration

AI generates three architecture options and a comparison table. The architecture owner verifies every constraint, removes an option based on a nonexistent managed service, adds the current-state option, runs a prototype for the highest-risk integration, and records the human decision in an ADR.

The AI output remains analysis input. `PB-ARCH` governs the decision and approval.

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

## 29. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)
- [AI Tools Reference](../04-reference/REF-AI-TOOLS.md)
- [Engineering Prompt Patterns Reference](../04-reference/REF-PROMPT-PATTERNS.md)

## 30. Related Playbooks

- [Requirements Playbook](PB-REQ.md) governs requirements refined with AI.
- [Architecture Playbook](PB-ARCH.md) governs AI-assisted architecture decisions.
- [Technical Design Playbook](PB-TECH-DESIGN.md) governs AI-assisted implementation design.
- [`PB-CODING`](PB-CODING.md) governs accepted AI-assisted code.
- [`PB-CODE-REVIEW`](PB-CODE-REVIEW.md) governs independent review and integration readiness for AI-assisted code.
- [`PB-TESTING`](PB-TESTING.md) governs AI-assisted test design, execution, and verification evidence.
- [Debugging Playbook](08-debugging-playbook.md) will govern AI-assisted diagnosis.
- [`PB-SECURITY-ENGINEERING`](PB-SECURITY-ENGINEERING.md) governs AI-assisted security work and human security authority.
- [`PB-DEPLOYMENT`](PB-DEPLOYMENT.md) governs AI-assisted release work and human release authority.
- [`PB-OBSERVABILITY`](PB-OBSERVABILITY.md) governs AI-assisted operational analysis and human operational authority.
- [`PB-INCIDENT-MANAGEMENT`](PB-INCIDENT-MANAGEMENT.md) governs AI-assisted incident work and human incident authority.
- [`PB-CHANGE-MANAGEMENT`](PB-CHANGE-MANAGEMENT.md) governs AI-assisted change assessment and human approval authority.
- [`PB-MAINTENANCE`](PB-MAINTENANCE.md) governs AI-assisted sustainment and human lifecycle authority.
- [`PB-PLATFORM-ENGINEERING`](PB-PLATFORM-ENGINEERING.md) governs AI-assisted platform-product work and human platform authority.
- [`PB-DATA-ENGINEERING`](PB-DATA-ENGINEERING.md) governs AI-assisted data-product work and human data authority.
- [`PB-API-MANAGEMENT`](PB-API-MANAGEMENT.md) governs AI-assisted API-product work and human API authority.
- [`PB-DEVELOPER-EXPERIENCE`](PB-DEVELOPER-EXPERIENCE.md) governs AI-assisted developer journeys and human DevEx authority.
- [Documentation Playbook](14-documentation-playbook.md) will govern accepted documentation.

## 31. Metrics

Use metrics to determine whether AI improves engineering outcomes safely.

| Metric | What It Reveals | Guardrail |
|---|---|---|
| AI-assisted cycle time | Time change for comparable work | Do not trade quality for speed |
| Acceptance after revision | How often candidates need material correction | High acceptance may indicate weak review |
| Verification finding rate | Incorrect, unsafe, stale, or invented content found | Findings show controls working |
| AI-related escaped defect rate | Defects in accepted AI-assisted work | Classify root cause and control failure |
| Rework rate | Effort spent correcting accepted output | Compare with non-AI baseline where possible |
| Security or disclosure events | Actual or near-miss information compromise | Report immediately; never optimise for a low reported number |
| Tool exception rate | Work outside approved capability | Review approval gaps and unsafe demand |
| Traceability completeness | Required contribution records linked to evidence | Check meaning, not field presence |
| Engineer understanding | Ability to explain accepted work during review | Use sampling, not surveillance |
| Outcome improvement | Quality, coverage, reliability, learning, or customer value | Output volume is not an outcome |

Do not use prompts submitted, tokens consumed, lines generated, or raw usage time as performance targets for individuals.

## 32. Reference Implementation and Enterprise Appendices

`PB-AI-ENGINEERING` is the common AI control layer for every engineering playbook. Domain playbooks explain where AI may help; this playbook defines the shared conditions under which that help becomes acceptable engineering work.

### 32.1 AI Suitability Matrix

| Task Characteristic | AI Suitability | Required Response |
|---|---|---|
| Clear, bounded, reversible, and independently verifiable | High | Proceed with approved capability and normal controls |
| Complex but decomposable with authoritative sources | Conditional | Split into reviewable tasks and strengthen verification |
| Sensitive information requiring restricted handling | Conditional | Use only an explicitly approved restricted capability |
| Irreversible, privileged, or production-changing action | Low | Keep execution under existing human approval and change controls |
| Output cannot be understood or independently verified | Unsuitable | Use a non-AI method or obtain qualified expertise |
| Required disclosure is prohibited | Prohibited | Stop and do not use AI |

### 32.2 AI Risk Matrix

| Impact if Wrong | Information Sensitivity | Minimum Treatment |
|---|---|---|
| Low | Public | Human review |
| Low or moderate | Internal | Approved tool, minimised context, verification |
| Moderate or high | Confidential | Explicit tool permission, restricted mode, independent review, traceability |
| High | Personal, regulated, security-sensitive, or customer-controlled | Specialist approval, strict minimisation, controlled environment, formal evidence |
| Any | Prohibited for selected tool | Do not use; choose authorised path |

### 32.3 AI Review Checklist

- [ ] The task, owner, desired outcome, and acceptance criteria are clear.
- [ ] AI suitability, information classification, and capability approval are recorded.
- [ ] Context is authoritative, minimal, current, and permitted.
- [ ] Output assumptions, omissions, sources, and limitations are visible.
- [ ] Independent engineering evidence supports material claims.
- [ ] Security, privacy, IP, licensing, bias, and compliance risks are resolved.
- [ ] The accepting engineer understands and can explain the result.
- [ ] Normal domain review and delivery gates pass.

### 32.4 Prompt Review Checklist

- [ ] Objective and expected output are explicit.
- [ ] Facts, assumptions, and unknowns are separated.
- [ ] Context is authoritative, current, minimal, and permitted.
- [ ] Secrets, personal data, customer identifiers, and unrelated content are absent.
- [ ] Constraints and actions not permitted are clear.
- [ ] Acceptance and evidence criteria are included.
- [ ] The tool cannot access unnecessary repositories, connectors, or execution.

### 32.5 AI Output Validation Checklist

- [ ] Facts, APIs, versions, citations, commands, and dependencies were checked against primary sources.
- [ ] Requirements and architecture constraints are satisfied.
- [ ] Normal, boundary, invalid, failure, concurrency, and recovery behaviour was tested.
- [ ] Generated tests have independent expected results and human-selected negative cases.
- [ ] Security, performance, reliability, maintainability, and operability were evaluated.
- [ ] Known uncertainty is isolated, owned, and prevented from becoming an accidental commitment.

### 32.6 Human Approval Checklist

- [ ] The approver is qualified and has the required authority.
- [ ] The owner can explain the output and its trade-offs.
- [ ] Verification and specialist findings are complete.
- [ ] Residual risks and conditions have authorised owners.
- [ ] Accepted work enters normal version control, review, testing, and release controls.
- [ ] Rejected or escalated output cannot enter delivery.
- [ ] AI did not approve itself or bypass separation of duties.

### 32.7 AI Traceability Model

```text
Engineering Task
      │
      ▼
Suitability + Context + Approved Capability
      │
      ▼
AI Candidate Output
      │
      ▼
Validation + Security + Human Review
      │
      ▼
Accepted Engineering Artefact
      │
      ├───────────────┐
      ▼               ▼
Implementation    Verification Evidence
      │               │
      └───────┬───────┘
              ▼
      Release and Operational Evidence
```

### 32.8 AI Engineering Maturity Model

| Level | Characteristics |
|---|---|
| 1. Ad Hoc | Individual use with inconsistent disclosure and review |
| 2. Controlled | Approved capabilities and basic human review exist |
| 3. Defined | Suitability, nine phases, risk controls, verification, and traceability are standard |
| 4. Measured | Defects, rework, incidents, exceptions, and outcome changes improve controls |
| 5. Adaptive | Capability approval and verification evolve from evidence without weakening accountability |

Maturity is demonstrated by safe engineering outcomes and learning, not adoption percentage.

### 32.9 AI Tool Evaluation Matrix

| Criterion | Evaluation Question |
|---|---|
| Capability | Does it reliably support the approved engineering purpose? |
| Information handling | What is stored, retained, trained on, transferred, and deleted? |
| Access | How are identity, least privilege, connectors, repositories, and execution controlled? |
| Security and privacy | What evidence, incidents, subprocessors, regions, and residual risks exist? |
| Intellectual property | What terms govern inputs, outputs, licences, attribution, and indemnity? |
| Verification | What limitations, drift, reproducibility, and evaluation evidence apply? |
| Operations | How are availability, audit, monitoring, revocation, and incident response handled? |
| Commercial | What cost, lock-in, exit, and contractual constraints apply? |

The approved catalogue belongs in [`REF-AI-TOOLS`](../04-reference/REF-AI-TOOLS.md).

### 32.10 AI Governance Workflow

```text
Proposed AI Use
      │
      ▼
Risk + Information Classification
      │
      ├── Prohibited ──► Stop
      ▼
Approved Tool and Context
      │
      ▼
Candidate Output
      │
      ▼
Verification + Security + Engineering Review
      │
      ├── Fails ──► Revise / Reject / Escalate
      ▼
Human Acceptance
      │
      ▼
Normal Delivery Workflow + Required Traceability
```

### 32.11 AI Deliverables Checklist

- [ ] AI Task Record and suitability decision.
- [ ] Context Package and disclosure decision.
- [ ] Approved capability reference.
- [ ] Prompt or instruction record where required.
- [ ] Candidate AI-generated artefacts.
- [ ] Validation and security evidence.
- [ ] Human review and approval record.
- [ ] Accepted engineering deliverable.
- [ ] Required traceability and lessons learned.

### 32.12 Gold-Standard Review Gate

Before approval, reviewers must confirm this playbook enables an engineer to:

- Decide whether AI should be used.
- Protect customer, personal, confidential, and proprietary information.
- Select an approved tool without confusing general approval with task-specific permission.
- Prepare a purposeful prompt and minimal context.
- Detect hallucinations and verify every output type with independent evidence.
- Review AI-generated code, tests, documents, queries, and operational guidance.
- Preserve architecture, security, review, testing, and deployment authority.
- Accept or reject output through a named human decision.
- Record material contributions without retaining unnecessary sensitive content.
- Respond to suspected disclosure or unsafe AI action.
- Apply the workflow across the full engineering lifecycle.

Failure of any item keeps the playbook in Draft.

## 33. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.3.13 | 2026-07-30 | Invara Labs Engineering | Draft | Linked AI-assisted developer journeys to governed `PB-DEVELOPER-EXPERIENCE` human authority |
| 1.3.12 | 2026-07-30 | Invara Labs Engineering | Draft | Linked AI-assisted API work to governed `PB-API-MANAGEMENT` human authority |
| 1.3.11 | 2026-07-30 | Invara Labs Engineering | Draft | Linked AI-assisted data work to governed `PB-DATA-ENGINEERING` human authority |
| 1.3.10 | 2026-07-30 | Invara Labs Engineering | Draft | Linked AI-assisted security work to governed `PB-SECURITY-ENGINEERING` human authority |
| 1.3.9 | 2026-07-30 | Invara Labs Engineering | Draft | Linked AI-assisted platform work to governed `PB-PLATFORM-ENGINEERING` human authority |
| 1.3.8 | 2026-07-30 | Invara Labs Engineering | Draft | Linked AI-assisted sustainment to governed `PB-MAINTENANCE` human authority |
| 1.3.7 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the governed `PB-CHANGE-MANAGEMENT` operations-governance stage |
| 1.3.6 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the governed `PB-INCIDENT-MANAGEMENT` response stage |
| 1.3.5 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the governed `PB-OBSERVABILITY` operations stage |
| 1.3.4 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the governed `PB-DEPLOYMENT` release stage |
| 1.3.3 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the governed `PB-TESTING` verification stage |
| 1.3.2 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the governed `PB-CODE-REVIEW` verification stage |
| 1.3.1 | 2026-07-30 | Invara Labs Engineering | Draft | Linked the new `PB-CODING` execution playbook |
| 1.3.0 | 2026-07-30 | Invara Labs Engineering | Draft | Elevated the document to an enterprise AI operating procedure with SDLC-wide guidance, dedicated risk management, IP controls, human accountability, capability governance, and twelve flagship appendices |
| 1.2.0 | 2026-07-30 | Invara Labs Engineering | Draft | Refocused the playbook on SOP and governance, moved volatile tool and prompt detail to supporting References, aligned the 32-section structure, and corrected appendix numbering |
| 1.1.0 | 2026-07-30 | Invara Labs Engineering | Draft | Renamed the artefact to `PB-AI-ENGINEERING` and added dedicated governance, security and privacy, approved-tools, prompt-engineering, and human-verification sections |
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial cross-lifecycle AI-assisted development playbook with nine-phase workflow, tool and context controls, independent verification, security review, traceability, and enterprise appendices |

## 34. Summary

`PB-AI-ENGINEERING` makes AI a first-class engineering capability without making it an authority.

The workflow requires engineers to:

- Define an appropriate task.
- Protect and minimise context.
- Use an approved tool.
- Treat output as untrusted.
- Verify claims and behaviour independently.
- Complete security and engineering validation.
- Make an explicit human decision.
- Record material contributions and improve practice.

AI Engineering Principles explain what Invara Labs believes: AI assists, engineers decide; understanding precedes acceptance; prompts have purpose; verification earns confidence; trust must be protected; and AI should multiply human potential.

This playbook turns those beliefs into daily engineering practice across requirements, architecture, technical design, coding, review, testing, deployment, operations, and incident response.
