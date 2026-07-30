---
title: Security Engineering Playbook
id: PB-SECURITY-ENGINEERING
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
  - security
  - secure-sdlc
  - devsecops
  - engineering
  - playbook
related:
  - PB-REQ
  - PB-ARCH
  - PB-TECH-DESIGN
  - PB-AI-ENGINEERING
  - PB-CODING
  - PB-CODE-REVIEW
  - PB-TESTING
  - PB-DEPLOYMENT
  - PB-OBSERVABILITY
  - PB-INCIDENT-MANAGEMENT
  - PB-CHANGE-MANAGEMENT
  - PB-MAINTENANCE
  - PB-PLATFORM-ENGINEERING
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

# Security Engineering Playbook

> **The standard operating procedure for integrating security into every stage of the engineering lifecycle through proactive risk identification, secure design, implementation, verification, deployment, operations, and continuous improvement.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. Security Engineering Principles
6. Secure SDLC Integration
7. When to Use This Playbook
8. Roles and Responsibilities
9. Inputs
10. Entry Criteria
11. Security Engineering Workflow
12. Security Lifecycle
13. Detailed Phase Activities
14. Threat Modelling
15. Security Design Review
16. Secure Development
17. Security Verification
18. Supply Chain Security
19. Secrets and Identity Management
20. Security Monitoring
21. Vulnerability Management
22. Security Incident Integration
23. AI-Assisted Security Engineering
24. Security Governance
25. Risk Management
26. Deliverables
27. Quality Gates
28. Common Mistakes
29. Best Practices
30. Templates
31. Examples
32. Related Principles
33. Related Standards
34. Related References
35. Related Playbooks
36. Metrics
37. Reference Implementation and Enterprise Appendices
38. Revision History
39. Summary

## 1. Overview

Security Engineering makes security part of normal engineering work.

It protects software, infrastructure, data, users, and business operations by identifying risk early, designing appropriate controls, verifying their effectiveness, monitoring real behaviour, and improving protection throughout the system lifecycle.

Security Engineering is not:

- An Information Security policy.
- A compliance framework or audit checklist.
- A catalogue of vulnerabilities.
- A secure-coding standard.
- A penetration-test procedure.
- A final approval performed after engineering is complete.

Those artefacts may inform this process, but this playbook governs how engineers perform security work.

```text
Business and User Context
          │
          ▼
Assets, Data, and Trust Boundaries
          │
          ▼
Threats and Risk
          │
          ▼
Requirements and Secure Design
          │
          ▼
Implementation and Verification
          │
          ▼
Secure Release and Operation
          │
          ▼
Vulnerability, Incident, and Lifecycle Learning
```

Security is continuous and risk-based. It is not equally heavy for every change, but it is never absent.

## 2. Purpose

This playbook defines how Invara Labs:

- Identifies security-relevant assets, data, actors, and boundaries.
- Converts risk into traceable security requirements.
- Threat-models systems and material changes.
- Designs controls using least privilege and defence in depth.
- Implements and independently verifies security behaviour.
- Protects dependencies, build systems, artifacts, identities, and secrets.
- Releases and operates software with security evidence.
- Finds, prioritises, remediates, and closes vulnerabilities.
- Coordinates security incidents with the incident-response lifecycle.
- Learns from evidence and evolves controls.

## 3. Objectives

Applying this playbook should produce:

- Explicit security ownership and risk decisions.
- Traceable security requirements.
- Current threat models for material systems and changes.
- Reviewed security architecture and technical design.
- Secure implementation and verification evidence.
- Governed software-supply-chain controls.
- Protected identities, credentials, keys, and secrets.
- Actionable security monitoring and response paths.
- Time-bound vulnerability treatment.
- Lifecycle evidence supporting assurance and audit.

## 4. Scope

### In Scope

- Software, APIs, infrastructure, cloud, mobile, data, and AI-enabled systems.
- Authentication, authorisation, session, identity, secrets, and cryptographic use.
- Data protection, privacy engineering, trust boundaries, and abuse cases.
- Threat modelling and security design review.
- Secure development and security verification.
- Dependencies, build systems, provenance, artifacts, and deployment security.
- Configuration, runtime, monitoring, vulnerability, incident, and maintenance security.
- Third-party integrations and platform capabilities.

### Out of Scope

- Corporate physical security.
- Human-resources security processes.
- Legal interpretation or enterprise compliance ownership.
- Technology-specific control values that belong in approved Standards.
- Replacing Privacy, Risk, Incident Management, Change Management, or business-continuity authorities.

Out-of-scope functions may still provide requirements or approval.

## 5. Security Engineering Principles

1. **Risk-based** — effort and control strength reflect plausible impact and exposure.
2. **Secure by design** — security shapes requirements and architecture.
3. **Secure by default** — the normal path applies safe configuration.
4. **Least privilege** — every identity and component receives only necessary access.
5. **Defence in depth** — independent controls limit single-control failure.
6. **Minimise attack surface** — remove unnecessary exposure, privilege, data, and functionality.
7. **Verify continuously** — controls require evidence throughout delivery and operation.
8. **Assume failure** — detect, contain, recover, revoke, and learn.
9. **Automate repeatable control** — make policy timely, consistent, and actionable.
10. **Preserve human accountability** — tools and AI assist; authorised people decide.
11. **Protect usable systems** — unusable controls are bypassed and create hidden risk.
12. **Make risk visible** — accepted risk has an owner, reason, expiry, and evidence.

## 6. Secure SDLC Integration

| Lifecycle Activity | Security Engineering Contribution |
|---|---|
| Requirements | Assets, abuse cases, data classification, security and privacy requirements |
| Architecture | Trust boundaries, threat model, control strategy, resilience, material decisions |
| Technical Design | Identity, authorisation, data, secrets, validation, logging, recovery detail |
| AI Engineering | Data restrictions, adversarial risk, evaluation, human authority |
| Coding | Secure implementation, dependency, secret, configuration, and error handling |
| Code Review | Independent review of security-sensitive behaviour and evidence |
| Testing | Misuse, negative, control, penetration, and regression verification |
| Deployment | Artifact integrity, environment hardening, access, policy, and recovery |
| Observability | Security signals, audit evidence, detection, and response context |
| Incident Management | Coordinated containment, investigation, recovery, and communication |
| Change Management | Risk-proportionate approval and production control |
| Maintenance | Patch, vulnerability, dependency, credential, and lifecycle treatment |
| Platform Engineering | Secure defaults, policy, identity, secrets, evidence, and self-service guardrails |

Security does not create a separate delivery lifecycle. It participates in the governed lifecycle.

## 7. When to Use This Playbook

Apply this playbook to:

- New systems and material features.
- New or changed trust boundaries.
- Authentication, authorisation, identity, payment, or administrative functions.
- Sensitive, regulated, personal, confidential, or high-value data.
- Internet-exposed systems and APIs.
- Infrastructure, platform, pipeline, or deployment changes.
- New dependencies, suppliers, integrations, AI capabilities, or data flows.
- Security defects, advisories, vulnerabilities, and incidents.
- Significant architecture, migration, deprecation, and retirement work.

Use a risk-proportionate profile for low-risk routine changes, but preserve entry, verification, and traceability requirements.

## 8. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| Engineering Owner | Owns system security outcomes, requirements, implementation, and residual risk escalation |
| Security Engineer | Facilitates threat modelling, advises controls, reviews evidence, and supports vulnerability and incident work |
| Architect | Defines security boundaries, patterns, quality attributes, and material decisions |
| Technical Lead | Integrates security into technical design, implementation planning, and delivery |
| Developer | Implements secure behaviour, protects secrets, validates inputs, tests changes, and reports risk |
| Reviewer | Independently verifies security-sensitive changes, assumptions, and evidence |
| Test or Quality Engineer | Designs and executes risk-based security verification |
| Platform Engineer | Provides secure defaults, identity, policy, pipelines, provenance, telemetry, and self-service controls |
| Operations or Reliability Engineer | Operates detection, response, hardening, continuity, and recovery capabilities |
| Product Owner | Defines business impact, acceptable user experience, priority, and value trade-offs |
| Data or Privacy Representative | Defines data classification, purpose, minimisation, retention, and privacy requirements |
| Risk Owner | Accepts, treats, transfers, or avoids residual risk within delegated authority |
| Incident Commander | Coordinates material security incidents under Incident Management |
| Approver | Authorises progression when required evidence and residual risk are acceptable |

The implementer cannot self-approve material residual risk outside delegated authority.

## 9. Inputs

Security Engineering may consume:

- Business, user, regulatory, contractual, and assurance requirements.
- Requirements, architecture, technical design, and decision records.
- Asset, service, data, identity, dependency, and supplier inventories.
- Data classification, flow, retention, and privacy information.
- Threat intelligence, abuse cases, adversary capability, and exposure.
- Source, infrastructure, configuration, pipeline, and deployment definitions.
- Test results, scan findings, penetration results, and review evidence.
- Logs, metrics, traces, audit events, incidents, and support evidence.
- Vulnerability advisories, dependency lifecycle, patch, and exception records.

Input provenance and currency must be known.

## 10. Entry Criteria

Before security work begins:

- System, change, or vulnerability scope is defined.
- Business and technical owners are named.
- Assets, users, data, environments, and trust boundaries are identified.
- Data classification and criticality are known or escalated.
- Applicable security, privacy, contractual, and compliance requirements are available.
- Architecture and intended data flows are sufficiently understood.
- Risk-assessment and approval authorities are known.
- Required evidence and security profile are defined.
- Traceability to initiating requirements, change, incident, or advisory exists.

Unknown critical information blocks high-risk work or becomes an explicit, owned risk.

## 11. Security Engineering Workflow

```text
Identify Assets and Context
          │
          ▼
Classify Data and Criticality
          │
          ▼
Assess Risk and Threat Model
          │
          ▼
Define Requirements and Controls
          │
          ▼
Review Secure Design
          │
          ▼
Implement Securely
          │
          ▼
Verify Controls and Residual Risk
          │
          ▼
Release Through Governance
          │
          ▼
Monitor, Respond, and Remediate
          │
          ▼
Improve and Maintain
```

Discovery, design, verification, and operation exchange evidence continuously.

## 12. Security Lifecycle

| State | Meaning | Required Evidence |
|---|---|---|
| Identified | Asset, owner, purpose, data, and exposure are known | Asset and context record |
| Assessed | Threats, impact, likelihood, and obligations are evaluated | Risk assessment and threat model |
| Designed | Requirements and controls address material risk | Reviewed security design |
| Implemented | Controls exist in code, configuration, infrastructure, and process | Reviewed implementation |
| Verified | Controls and failure paths meet acceptance criteria | Security verification evidence |
| Operated | Signals, response, access, vulnerability, and recovery are active | Operational security evidence |
| Maintained | Threats, controls, dependencies, credentials, and risk stay current | Lifecycle review and maintenance records |
| Retired | Access, data, secrets, integrations, and assets are safely removed | Retirement and destruction evidence |

## 13. Detailed Phase Activities

### Phase 1: Identify Assets and Context

**Goal:** understand what must be protected and why.

Activities:

- Identify users, services, infrastructure, data, identities, interfaces, and suppliers.
- Define business purpose, criticality, exposure, and availability needs.
- Map data flow, storage, processing, transfer, and retention.
- Mark trust boundaries and privileged operations.
- Identify misuse, abuse, fraud, privacy harm, and safety concerns.
- Assign owners and authoritative inventories.

Outputs:

- Asset and Context Record.
- Data Flow and Classification.
- Initial Abuse Cases.

### Phase 2: Assess Risk

**Goal:** prioritise plausible threats by business consequence.

Activities:

- Identify threat actors, capability, intent, and opportunity.
- Evaluate confidentiality, integrity, availability, privacy, financial, legal, and safety impact.
- Assess exposure, exploitability, existing controls, and uncertainty.
- Separate inherent risk from residual risk.
- Define treatment priority and escalation threshold.
- Record assumptions and evidence.

Outputs:

- Security Risk Assessment.
- Prioritised Risk Register.
- Security Profile.

### Phase 3: Threat Model

**Goal:** identify how the system could be abused or compromised.

Activities:

- Decompose the system and mark trust boundaries.
- Enumerate threats against assets, flows, identities, and control planes.
- Analyse spoofing, tampering, repudiation, disclosure, denial, privilege escalation, and domain abuse.
- Model attacker paths and high-impact combinations.
- Identify mitigations, detection, recovery, and residual risk.
- Review with architecture, engineering, security, operations, and product perspectives.

Outputs:

- Threat Model.
- Threat-to-Control Traceability.
- Open Risk and Decision List.

### Phase 4: Define Requirements and Secure Design

**Goal:** translate risk into verifiable design.

Activities:

- Define authentication, authorisation, session, identity, and administrative controls.
- Define data minimisation, encryption, key, retention, deletion, and privacy behaviour.
- Define validation, output encoding, rate, quota, isolation, and abuse controls.
- Define secrets, configuration, dependency, artifact, and deployment controls.
- Define logging, audit, alerting, containment, revocation, recovery, and continuity.
- Record material decisions, trade-offs, exceptions, and acceptance criteria.

Outputs:

- Security Requirements.
- Security Architecture and Technical Design.
- Verification Strategy.

### Phase 5: Implement Securely

**Goal:** build the approved controls without introducing avoidable weakness.

Activities:

- Use approved frameworks, libraries, platform capabilities, and secure defaults.
- Validate untrusted input and encode output at trust boundaries.
- Enforce authorisation server-side for every protected action.
- Protect credentials, keys, tokens, and sensitive configuration.
- Avoid sensitive data in logs, errors, telemetry, fixtures, and source control.
- Pin, review, scan, and update dependencies and build inputs.
- Add negative, misuse, control, and regression tests.

Outputs:

- Secure Implementation.
- Review-Ready Evidence.
- Updated Dependency and Configuration Records.

### Phase 6: Verify Security

**Goal:** prove controls work and residual risk is understood.

Activities:

- Review security-sensitive code, configuration, infrastructure, and permissions.
- Execute static, dynamic, dependency, secret, container, and infrastructure checks where applicable.
- Test authentication, authorisation, validation, isolation, abuse, rate, logging, and recovery.
- Verify threat mitigations and security requirements.
- Use independent penetration or specialist testing when risk warrants.
- Triage findings by exploitability, reachability, impact, and exposure.

Outputs:

- Security Verification Report.
- Finding and Treatment Register.
- Residual Risk Recommendation.

### Phase 7: Release Securely

**Goal:** preserve verified security through production promotion.

Activities:

- Verify artifact identity, provenance, integrity, and approved source.
- Validate environment configuration, identities, secrets, network, storage, and policy.
- Confirm monitoring, alerting, audit, revocation, backup, and recovery readiness.
- Restrict production authority and preserve attributable evidence.
- Stage high-risk rollout and define security stop and rollback conditions.
- Obtain risk-proportionate change and release approval.

Outputs:

- Security Release Evidence.
- Operational Security Handover.
- Approval and Residual Risk Record.

### Phase 8: Monitor, Respond, and Remediate

**Goal:** detect harmful behaviour and reduce exposure quickly.

Activities:

- Monitor security-relevant events, control failures, anomalous access, and configuration drift.
- Maintain actionable detection, ownership, routing, context, and response runbooks.
- Receive, validate, assess, prioritise, and assign vulnerabilities.
- Coordinate material impact through Incident Management.
- Contain, revoke, patch, mitigate, recover, and verify.
- Communicate according to legal, privacy, customer, and contractual authority.

Outputs:

- Detection and Response Evidence.
- Vulnerability Treatment Records.
- Incident and Recovery Records where applicable.

### Phase 9: Improve and Maintain

**Goal:** keep protection effective as systems and threats evolve.

Activities:

- Review incidents, vulnerabilities, exceptions, bypasses, and near misses.
- Update threat models, requirements, tests, controls, and monitoring.
- Patch dependencies, platforms, configurations, and credentials.
- Remove unused access, secrets, data, interfaces, and attack surface.
- Track systemic improvements through Change Management and Maintenance.
- Reassess risk at lifecycle reviews and before deprecation or retirement.

Outputs:

- Security Improvement Plan.
- Updated Risk and Threat Records.
- Maintenance and Lifecycle Evidence.

## 14. Threat Modelling

Threat modelling is structured reasoning about how a system may be misused, attacked, or fail under hostile conditions.

A threat model shall identify:

- Scope, purpose, owners, users, environments, and assumptions.
- Assets, sensitive data, identities, and privileged actions.
- Components, dependencies, data flows, entry points, and trust boundaries.
- Threat actors, abuse cases, attacker paths, and failure modes.
- Existing and proposed preventive, detective, and recovery controls.
- Risk, treatment, residual risk, owner, and validation.
- Review triggers and lifecycle state.

Threat models must be updated when trust boundaries, data, exposure, identity, dependencies, or material behaviour change.

## 15. Security Design Review

Security design review evaluates whether proposed controls address risk before implementation cost becomes entrenched.

Review areas include:

- Trust boundaries and attack surface.
- Authentication, session, authorisation, and administrative access.
- Data classification, minimisation, encryption, retention, and deletion.
- Input, output, file, command, query, and deserialisation boundaries.
- Tenant, process, network, storage, and environment isolation.
- Secrets, keys, certificates, tokens, and rotation.
- Dependencies, suppliers, build, provenance, and artifact integrity.
- Audit, detection, incident, revocation, recovery, and continuity.
- Privacy, abuse, fraud, and AI-specific risks.

Findings must be accepted, treated, transferred, or avoided by authorised owners.

## 16. Secure Development

Secure implementation shall:

- Use memory-safe and type-safe capabilities where practical.
- Prefer supported libraries and platform services over custom security mechanisms.
- Validate input by expected structure, type, length, range, and context.
- Apply contextual output encoding.
- Use parameterised data access and safe command execution.
- Enforce access at the authoritative service boundary.
- Fail closed for protected operations without causing unsafe availability failure.
- Avoid revealing secrets, internals, personal data, or control detail in errors.
- Use secure randomness and approved cryptographic primitives.
- Separate environments and production authority.
- Keep tests and examples free of live credentials and sensitive data.

Technology-specific rules belong in Standards.

## 17. Security Verification

Select verification from risk and technology:

| Method | Finds | Limitation |
|---|---|---|
| Code and design review | Logic, boundary, control, and assumption defects | Depends on reviewer expertise and context |
| Static analysis | Recognisable source patterns and flows | False positives and incomplete runtime context |
| Software composition analysis | Known component risk and licence metadata | Does not prove reachability or safe use |
| Secret scanning | Credential-like content | Cannot prove revocation or absence elsewhere |
| Infrastructure scanning | Configuration and policy defects | Deployed state may drift |
| Dynamic testing | Runtime behaviour in exercised paths | Limited by reachable coverage |
| Fuzzing | Parser, boundary, state, and crash defects | Requires useful harnesses and oracles |
| Penetration testing | Composed attacker paths and practical exploitability | Point-in-time and scope-limited |
| Adversarial or abuse testing | Domain misuse and control bypass | Requires realistic threat knowledge |

No single tool provides security assurance.

## 18. Supply Chain Security

Engineering shall govern:

- Source repositories, branch protection, review, and signing where justified.
- Build identities, runners, permissions, isolation, and ephemeral execution.
- Dependency origin, version, integrity, support, vulnerability, and licence.
- Build reproducibility and protection from untrusted contribution paths.
- Artifact identity, immutability, provenance, storage, promotion, and verification.
- Software Bills of Materials (SBOMs) for scoped systems.
- Supplier access, assurance, notification, lifecycle, and exit.
- Secure update, patch, rollback, and revocation.

Dependency count alone is not risk. Exposure, privilege, reachability, maintenance, and consequence matter.

## 19. Secrets and Identity Management

### Secrets

- Store secrets in approved secret-management systems.
- Never place live secrets in source, images, logs, tickets, prompts, or documentation.
- Use short-lived credentials and workload identity where practical.
- Restrict access by purpose, identity, environment, and least privilege.
- Rotate on schedule, exposure, role change, and control failure.
- Revoke and verify after suspected compromise.
- Inventory ownership, consumers, purpose, and lifecycle.

### Identity

- Use unique, attributable human and workload identities.
- Require strong authentication proportionate to access.
- Centralise lifecycle and promptly remove stale access.
- Separate routine, privileged, emergency, and machine access.
- Review high-risk roles and service identities.
- Log privileged and sensitive actions with protected audit evidence.

Shared credentials require explicit exception and migration.

## 20. Security Monitoring

Security monitoring should answer:

- Who performed which sensitive action, where, and when?
- Did authentication, authorisation, policy, integrity, or isolation fail?
- Are access, privilege, data movement, or configuration patterns abnormal?
- Are protections disabled, bypassed, degraded, or drifting?
- Can responders identify affected assets, users, data, versions, and owners?

Signals require:

- Defined purpose and threat.
- Source integrity and time reliability.
- Data minimisation and access protection.
- Actionable threshold, context, owner, routing, and runbook.
- Test evidence and periodic effectiveness review.
- Retention aligned with investigation, privacy, and compliance needs.

## 21. Vulnerability Management

```text
Discover or Receive
        │
        ▼
Validate and De-duplicate
        │
        ▼
Assess Reachability, Exposure, and Impact
        │
        ▼
Prioritise and Assign
        │
        ▼
Mitigate or Remediate
        │
        ▼
Verify and Monitor
        │
        ▼
Close, Accept, or Reopen
```

Every vulnerability record includes:

- Affected asset, owner, version, environment, and exposure.
- Source and confidence.
- Technical severity and business context.
- Exploitability, reachability, privilege, data, and compensating controls.
- Treatment, deadline, owner, verification, and residual risk.
- Exception authority and expiry where applicable.

Severity labels do not replace contextual risk assessment.

## 22. Security Incident Integration

Suspected or confirmed security harm invokes [`PB-INCIDENT-MANAGEMENT`](PB-INCIDENT-MANAGEMENT.md) when coordinated response is required.

Security specialists support:

- Evidence preservation and investigation.
- Containment, credential revocation, and threat eradication.
- Impact assessment for systems, identities, users, and data.
- Legal, privacy, customer, supplier, and authority coordination.
- Secure recovery and monitoring for recurrence.
- Root cause, control gap, and systemic improvement analysis.

Incident response has priority over routine vulnerability workflow when active harm is present.

## 23. AI-Assisted Security Engineering

AI may assist with:

- Threat and abuse-case exploration.
- Design and code review prompts.
- Finding correlation, de-duplication, and initial triage.
- Test generation and log analysis.
- Documentation, evidence mapping, and control consistency review.
- Draft remediation options.

All AI-assisted work follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

Humans must:

- Validate claims against source and environment.
- Review generated code, commands, rules, and configurations.
- Prevent secrets and prohibited data from entering AI systems.
- Confirm exploitability, impact, treatment, and closure.
- Retain authority for production access, testing, disclosure, and risk acceptance.

AI must not autonomously exploit production, rotate credentials, change access, suppress findings, or accept risk.

## 24. Security Governance

Security governance defines:

- Security profiles and risk-proportionate activity.
- Ownership and approval authority.
- Review and verification independence.
- Finding classification and treatment timelines.
- Exception, risk acceptance, expiry, and escalation.
- Evidence, traceability, retention, and access.
- Supplier, dependency, and disclosure processes.
- Security incident and vulnerability coordination.
- Lifecycle review triggers.

Controls must provide actionable remediation. Governance that only blocks work pushes risk into unmanaged paths.

## 25. Risk Management

| Treatment | Meaning | Required Record |
|---|---|---|
| Avoid | Remove the risky activity or exposure | Decision and resulting scope |
| Reduce | Add controls to lower likelihood or impact | Treatment, validation, residual risk |
| Transfer | Allocate consequence through contract or service | Scope, dependency, remaining responsibility |
| Accept | Authorised owner retains residual risk | Reason, evidence, expiry, monitoring |

Risk assessment considers:

- Business and user impact.
- Data sensitivity and volume.
- Exposure and trust boundary.
- Exploitability and attacker capability.
- Privilege and lateral movement.
- Detection, containment, recovery, and uncertainty.
- Existing controls and their verified effectiveness.

No risk is “closed” merely because a scanner finding is suppressed.

## 26. Deliverables

| Deliverable | Purpose |
|---|---|
| Asset and Security Context | Establishes scope, ownership, data, exposure, and criticality |
| Security Requirements | Defines verifiable protective behaviour |
| Threat Model | Connects threats, controls, validation, and residual risk |
| Security Design Review | Records review findings and design decisions |
| Security Verification Report | Provides evidence of control effectiveness |
| Risk and Finding Register | Tracks treatment, owners, dates, and acceptance |
| SBOM or Dependency Record | Supports supply-chain visibility |
| Security Monitoring Plan | Defines detection, routing, response, and evidence |
| Vulnerability Treatment Record | Governs remediation and closure |
| Security Incident Evidence | Supports coordinated response and learning |
| Security Improvement Plan | Tracks systemic control improvements |

Deliverables may be combined when ownership, traceability, and approval remain clear.

## 27. Quality Gates

### Gate 1: Security Context Ready

- Assets, owners, users, data, criticality, exposure, and boundaries are known.
- Applicable requirements and security profile are identified.
- Risk and approval authorities are named.
- Required security work is planned.

### Gate 2: Secure Design Ready

- Threat model covers material assets, flows, boundaries, abuse, and dependencies.
- Security requirements and controls are traceable.
- Identity, data, secrets, validation, supply chain, monitoring, and recovery are designed.
- Material residual risk and decisions are reviewed.

### Gate 3: Implementation Ready for Independent Verification

- Security controls are implemented and self-verified.
- Security-sensitive changes and dependencies are identifiable.
- Automated checks and negative tests pass at the required profile.
- Known findings have treatment and ownership.

### Gate 4: Security Release Ready

- Independent verification covers applicable threats and requirements.
- Critical and unacceptable risks are mitigated or block release.
- Artifact, environment, identity, secrets, monitoring, response, and recovery are ready.
- Residual risk and release authority are recorded.

### Gate 5: Operational Security and Lifecycle Review

- Security signals, vulnerabilities, access, dependencies, incidents, and exceptions are reviewed.
- Controls remain effective against current exposure and threat.
- Required remediation and maintenance have owners and dates.
- Risk, threat model, evidence, and next review are updated.

Failed gates block progression unless an authorised, documented, time-bound exception exists.

## 28. Common Mistakes

- Treating security as a release-end scan.
- Copying controls without understanding threat or user impact.
- Using compliance completion as evidence of security effectiveness.
- Relying on one scanner or penetration test.
- Recording vulnerabilities without ownership and treatment dates.
- Prioritising scores without reachability, exposure, or business context.
- Building custom authentication, cryptography, or secret storage unnecessarily.
- Granting broad access to reduce delivery friction.
- Logging sensitive data in the name of auditability.
- Hiding findings through exclusions instead of treating root cause.
- Shipping detection without routing, runbooks, or response authority.
- Accepting risk indefinitely.
- Ignoring supplier, build, pipeline, and artifact compromise.
- Sharing sensitive code, data, credentials, or findings with unapproved AI tools.

## 29. Best Practices

- Start with assets, data, trust, and plausible harm.
- Add security acceptance criteria to normal engineering requirements.
- Threat-model before implementation and update on material change.
- Prefer platform-provided secure defaults and maintained libraries.
- Make access narrow, temporary, attributable, and reviewable.
- Test negative and abuse paths, not only expected use.
- Verify authorisation at the authoritative boundary.
- Keep secrets out of code and use short-lived identity.
- Protect the build and verify artifact provenance.
- Prioritise vulnerabilities using real system context.
- Design detection, containment, revocation, and recovery with prevention.
- Exercise security response and recovery.
- Learn from bypasses, exceptions, incidents, and near misses.
- Remove unused privilege, data, interfaces, dependencies, and controls.

## 30. Templates

### Security Engineering Record

```text
System or change:
Purpose and owner:
Assets and criticality:
Users, identities, and privileged actions:
Data classification, flow, retention, and deletion:
Components, dependencies, interfaces, and trust boundaries:
Threats and abuse cases:
Security requirements:
Controls and decisions:
Verification:
Monitoring and response:
Findings and residual risk:
Approval:
Lifecycle triggers and next review:
```

### Vulnerability Record

```text
ID and source:
Affected asset, owner, version, and environment:
Description and evidence:
Exposure, reachability, exploitability, and privilege:
Business, user, data, and operational impact:
Existing and compensating controls:
Priority and deadline:
Treatment and validation:
Risk owner and exception expiry:
Status and closure evidence:
```

### Security Exception

```text
Requirement or finding:
Scope:
Reason:
Risk and affected parties:
Compensating controls:
Monitoring:
Owner and approver:
Start and expiry:
Remediation or migration:
Review and closure:
```

## 31. Examples

### Example: New Administrative API

**Context:** a service adds an endpoint that changes customer access.

Security work:

1. Classify the operation as privileged and high impact.
2. Model identity spoofing, privilege escalation, cross-tenant access, replay, abuse, and audit repudiation.
3. Require strong administrator identity, server-side scoped authorisation, step-up control where appropriate, idempotency, rate limits, protected audit, and alerting.
4. Add negative tests for missing, stale, forged, cross-tenant, and insufficient privilege.
5. Verify production identity, secrets, policy, audit routing, rollback, and incident response.

Release blocks if cross-tenant authorisation or attributable audit cannot be demonstrated.

### Example: Critical Dependency Advisory

**Context:** an advisory affects a library present in several services.

Security work:

1. Identify deployed versions and owning services.
2. Validate component identity, reachability, exposure, exploitability, and available mitigations.
3. Prioritise internet-exposed reachable services over unused transitive instances.
4. Apply containment where needed, upgrade through governed change, and verify.
5. Update SBOM, dependency, exception, and lifecycle records.

A critical label does not justify closing unaffected records without evidence.

### Example: Secret Found in Source History

**Response:**

1. Treat the secret as exposed.
2. Revoke or rotate it immediately through authorised response.
3. Identify access, use, affected systems, and possible impact.
4. Remove current exposure without assuming history rewrite removes compromise.
5. investigate through Incident Management if material risk exists.
6. Add prevention, scanning, least privilege, and lifecycle improvements.

## 32. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Architecture Principles](../01-principles/03-architecture-principles.md)
- [Coding Principles](../01-principles/04-coding-principles.md)
- [Testing Principles](../01-principles/05-testing-principles.md)
- [Security Principles](../01-principles/06-security-principles.md)
- [Observability Principles](../01-principles/07-observability-principles.md)

## 33. Related Standards

- [Playbook Authoring Standard](../03-standards/PB-AUTHORING.md)
- [Documentation Style Guide](../03-standards/DOC-STYLE.md)
- [Engineering Terminology Standard](../03-standards/TERM-STANDARD.md)
- [Engineering Review Standard](../03-standards/STD-REVIEW.md)
- [Engineering Traceability Standard](../03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](../03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](../03-standards/STD-VERSIONING.md)

Security, secure-coding, identity, secrets, dependency, vulnerability, and supply-chain implementation standards are planned and non-authoritative.

## 34. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)

Threat-modelling, security-testing, vulnerability, security-pattern, and OWASP references are planned and non-authoritative.

## 35. Related Playbooks

- [Requirements Playbook](PB-REQ.md) governs security requirements.
- [Architecture Playbook](PB-ARCH.md) and [Technical Design Playbook](PB-TECH-DESIGN.md) govern secure design.
- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted security work.
- [Coding Playbook](PB-CODING.md), [Code Review Playbook](PB-CODE-REVIEW.md), and [Testing Playbook](PB-TESTING.md) govern implementation and verification.
- [Deployment Playbook](PB-DEPLOYMENT.md) governs secure production promotion.
- [Observability Playbook](PB-OBSERVABILITY.md) governs security-relevant operational evidence.
- [Incident Management Playbook](PB-INCIDENT-MANAGEMENT.md) governs coordinated security incident response.
- [Change Management Playbook](PB-CHANGE-MANAGEMENT.md) governs security changes.
- [Maintenance Playbook](PB-MAINTENANCE.md) governs patch, vulnerability, credential, dependency, and lifecycle work.
- [Platform Engineering Playbook](PB-PLATFORM-ENGINEERING.md) supplies secure defaults and platform controls.

## 36. Metrics

Use metrics to improve security outcomes, not reward suppressed findings or compare individual engineers.

| Dimension | Example Metrics | Guardrail |
|---|---|---|
| Context | Asset, data-classification, ownership, and threat-model coverage | Coverage does not prove quality |
| Prevention | Secure-default and platform-control adoption | Exceptions may be justified |
| Verification | Applicable security-test and control coverage | Tool count is not assurance |
| Findings | Open risk by exposure, age, and treatment state | More findings may mean better detection |
| Remediation | Time to contain and remediate by contextual priority | Separate waiting, change, and verification |
| Supply Chain | Dependency visibility, provenance, SBOM, supported-version coverage | Inventory freshness matters |
| Identity | Privileged access, stale access, credential age, break-glass review | Avoid incentivising weak classification |
| Monitoring | Detection coverage, alert actionability, time to triage | Measure actual response |
| Incidents | Security incident rate, impact, recurrence, learning completion | Reporting must remain safe |
| Exceptions | Count, age, expiry, compensating-control effectiveness | Expired exceptions are failures |

Metrics require segmentation by system criticality and exposure.

## 37. Reference Implementation and Enterprise Appendices

### 37.1 Secure SDLC Checklist

- [ ] Security context and profile are defined.
- [ ] Assets, data, identities, boundaries, and abuse cases are known.
- [ ] Requirements trace to threats and controls.
- [ ] Design addresses identity, data, secrets, validation, supply chain, monitoring, and recovery.
- [ ] Implementation and independent verification evidence exist.
- [ ] Release preserves artifact, environment, access, and monitoring controls.
- [ ] Vulnerability, incident, maintenance, and lifecycle paths are active.

### 37.2 Threat Modelling Template

| Area | Required Content |
|---|---|
| Context | Purpose, owners, users, environments, criticality |
| Assets | Data, identities, functions, infrastructure, business value |
| Model | Components, flows, interfaces, dependencies, trust boundaries |
| Threats | Actors, abuse cases, attacker paths, failure modes |
| Controls | Preventive, detective, containment, recovery |
| Risk | Likelihood, impact, uncertainty, residual risk |
| Validation | Tests, evidence, owner, status |
| Lifecycle | Triggers, review, version, approval |

### 37.3 Security Review Checklist

- [ ] Scope, assumptions, data flow, and boundaries are accurate.
- [ ] Authentication, authorisation, session, and privileged actions are reviewed.
- [ ] Data minimisation, protection, retention, and deletion are reviewed.
- [ ] Validation, encoding, isolation, abuse, and availability controls are reviewed.
- [ ] Secrets, dependencies, build, artifact, and deployment controls are reviewed.
- [ ] Audit, detection, incident, revocation, and recovery are reviewed.
- [ ] Findings, decisions, owners, deadlines, and residual risk are recorded.

### 37.4 Vulnerability Triage Matrix

| Factor | Low | Medium | High |
|---|---|---|---|
| Exposure | Isolated or inactive | Restricted | Internet or broad internal |
| Reachability | Not reachable | Conditional | Directly reachable |
| Exploitability | Impractical | Requires conditions | Reliable or known exploitation |
| Privilege | None gained | Scoped | Administrative or lateral |
| Data and Impact | Minimal | Material | Critical, sensitive, systemic |
| Control | Strong verified containment | Partial | None or ineffective |

Use the matrix to support judgement, not compute risk mechanically.

### 37.5 Security Risk Matrix

| Risk | Asset | Threat | Existing Controls | Likelihood | Impact | Treatment | Residual Risk | Owner | Due | Status |
|---|---|---|---|---|---|---|---|---|---|---|

### 37.6 Secure Deployment Checklist

- [ ] Release artifact, source, integrity, provenance, and SBOM are verified.
- [ ] Production identity, privilege, secrets, certificates, and policy are correct.
- [ ] Environment, network, storage, runtime, and administrative interfaces are hardened.
- [ ] Security configuration is versioned and drift-detectable.
- [ ] Audit, detection, routing, runbooks, containment, revocation, and recovery work.
- [ ] Findings, residual risk, stop, rollback, and approval are recorded.

### 37.7 Security Maturity Model

| Level | Characteristics |
|---|---|
| 1 — Reactive | Security occurs after defects or incidents |
| 2 — Repeatable | Basic reviews, scans, ownership, and remediation exist |
| 3 — Integrated | Threats, requirements, design, verification, and operations connect |
| 4 — Managed | Risk profiles, secure defaults, evidence, metrics, and lifecycle are governed |
| 5 — Adaptive | Controls evolve from threat, incident, vulnerability, and effectiveness evidence |

Maturity is assessed per product or capability.

### 37.8 SBOM Checklist

- [ ] Product, version, artifact, and environment are identifiable.
- [ ] Direct and transitive components include name, version, origin, and integrity.
- [ ] SBOM format and generation method are documented.
- [ ] Build and artifact relationship is traceable.
- [ ] Access, storage, update, retention, and consumer needs are defined.
- [ ] Vulnerability and lifecycle processes consume current SBOM data.

### 37.9 Security Metrics Dashboard

| Dimension | Indicator | Target | Current | Trend | Evidence | Owner | Action |
|---|---|---:|---:|---|---|---|---|
| Risk | | | | | | | |
| Threats | | | | | | | |
| Verification | | | | | | | |
| Vulnerabilities | | | | | | | |
| Supply chain | | | | | | | |
| Identity | | | | | | | |
| Monitoring | | | | | | | |
| Incidents | | | | | | | |
| Exceptions | | | | | | | |

### 37.10 Deliverables Checklist

- [ ] Asset and Security Context.
- [ ] Security Requirements and acceptance criteria.
- [ ] Threat Model and risk register.
- [ ] Security Architecture and Technical Design Review.
- [ ] Implementation and verification evidence.
- [ ] Dependency, SBOM, artifact, and deployment evidence.
- [ ] Monitoring, vulnerability, incident, and maintenance plan.
- [ ] Residual risk, approval, lifecycle, and next review.

### 37.11 Security Architecture Review Template

```text
System, version, owner, and purpose:
Users, identities, assets, and criticality:
Data classification, flow, retention, and deletion:
Components, interfaces, dependencies, and trust boundaries:
Threats and abuse cases:
Authentication, authorisation, session, and administration:
Validation, isolation, availability, and abuse control:
Secrets, cryptography, keys, and certificates:
Supply chain, build, artifact, and deployment:
Audit, monitoring, incident, revocation, and recovery:
Findings, decisions, treatment, and residual risk:
Reviewers, approval, date, and next trigger:
```

### 37.12 Security Verification Checklist

- [ ] Verification maps to threats, requirements, and changed attack surface.
- [ ] Authentication, authorisation, validation, isolation, and abuse are tested.
- [ ] Data, secrets, errors, logs, and privacy behaviour are tested.
- [ ] Dependencies, source, build, infrastructure, configuration, and artifact are checked.
- [ ] Monitoring, alerting, audit, revocation, rollback, and recovery are tested.
- [ ] Findings are validated, contextualised, assigned, and tracked.
- [ ] Closure evidence and residual risk approval exist.

## 38. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Security Engineering Playbook with nine-phase secure-lifecycle workflow, threat modelling, design review, secure development, verification, supply chain, identity, vulnerability, incident integration, five quality gates, metrics, and twelve enterprise appendices |

## 39. Summary

`PB-SECURITY-ENGINEERING` governs how security is engineered into software and platform systems.

It requires teams to:

- Understand assets, data, trust, threats, and business impact.
- Translate risk into traceable requirements and verified controls.
- Secure implementation, supply chains, identities, secrets, release, and operation.
- Detect and treat vulnerabilities and incidents through governed workflows.
- Keep controls effective through maintenance and lifecycle change.
- Preserve authorised human accountability for risk.

This Draft establishes Security Engineering as the second Enterprise Engineering Capability. Formal review and approval remain required before it is Stable.
