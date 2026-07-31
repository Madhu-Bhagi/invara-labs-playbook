---
title: Engineering Governance Framework
id: EGF-ENGINEERING-GOVERNANCE
version: 1.0.0
status: Draft
owner: Invara Labs Engineering Leadership
classification: Governance Framework
review_cycle: Annual
created: 2026-07-31
last_updated: 2026-07-31
approved_by: TBD
authors:
  - Invara Labs Engineering
tags:
  - governance
  - decision-rights
  - accountability
  - risk
  - engineering
related:
  - ILOS-GOVERNANCE
  - PB-ARCH
  - PB-AI-ENGINEERING
  - PB-CHANGE-MANAGEMENT
  - PB-MAINTENANCE
  - PB-PLATFORM-ENGINEERING
  - PB-SECURITY-ENGINEERING
  - PB-DATA-ENGINEERING
  - PB-API-MANAGEMENT
  - PB-DEVELOPER-EXPERIENCE
  - STD-REVIEW
  - STD-TRACEABILITY
  - STD-METADATA
  - STD-VERSIONING
  - REF-IDENTIFIERS
supersedes: null
superseded_by: null
---

# Engineering Governance Framework

> **The framework defining decision rights, ownership, accountability, review, exceptions, risk, compliance evidence, and continuous improvement across the Enterprise Engineering Operating System.**

## Table of Contents

1. Overview
2. Purpose
3. Governance Principles
4. Governance Model
5. Decision Rights
6. Organisational Roles
7. Engineering Councils
8. Architecture Governance
9. Standards Governance
10. Technology Governance
11. AI Governance
12. Security Governance
13. Data Governance
14. Platform Governance
15. API Governance
16. Technical Debt Governance
17. Exception Management
18. Risk Management
19. Compliance and Assurance
20. Metrics
21. Review Cadence
22. Continuous Improvement
23. Related Documents

## 1. Overview

Engineering Governance establishes how engineering decisions are proposed, reviewed, approved, communicated, implemented, measured, challenged, and retired.

This framework sits above engineering Principles, Playbooks, Standards, References, Templates, and Examples. It governs engineering activity and decision-making; [`ILOS-GOVERNANCE`](../../ilos/ILOS-GOVERNANCE.md) separately governs the documentation operating system itself.

Engineering Governance is not:

- A central committee approving every technical choice.
- A substitute for accountable engineering leadership.
- A collection of meetings without decisions.
- An Information Security or compliance policy.
- A reason to remove team autonomy.
- A guarantee that all risk can be eliminated.

Governance applies the lightest control that provides the required clarity, evidence, and accountability.

```text
Company Strategy and Risk Appetite
                │
                ▼
Engineering Governance Framework
                │
       ┌────────┼────────┐
       ▼        ▼        ▼
  Principles  Decision  Portfolio and
              Rights     Domain Governance
       │        │        │
       └────────┼────────┘
                ▼
      Playbooks and Standards
                │
                ▼
        Team and Project Work
                │
                ▼
       Evidence and Outcomes
                │
                └──────► Review and Improvement
```

## 2. Purpose

This framework ensures:

- Decisions are made at the appropriate level.
- Accountability remains explicit.
- Teams know which rules are mandatory and where judgement is permitted.
- Architecture, technology, AI, security, data, platform, API, and lifecycle decisions align.
- Risk and exceptions are visible, owned, and time-bound.
- Reviews are proportionate to impact.
- Evidence supports learning, assurance, and audit.
- Governance improves engineering outcomes rather than creating avoidable delay.

## 3. Governance Principles

1. **Decision authority follows accountability** — the person accepting consequences must have appropriate authority and evidence.
2. **Subsidiarity** — make decisions at the lowest competent level unless impact requires escalation.
3. **Risk-proportionate control** — higher consequence, uncertainty, exposure, or irreversibility requires stronger review.
4. **Guardrails over gates** — encode safe defaults and feedback before adding manual approval.
5. **Evidence over opinion** — proposals state context, options, trade-offs, risk, and expected outcomes.
6. **Transparency** — material decisions, exceptions, owners, and rationale are discoverable.
7. **Time-bounded exceptions** — deviations expire unless reviewed and renewed.
8. **Independent challenge** — material decisions receive review from someone not solely responsible for implementation.
9. **Reversibility matters** — reversible decisions move faster; one-way decisions receive greater scrutiny.
10. **No governance theatre** — meetings and artefacts exist only when they change decision quality, safety, or accountability.
11. **Learning closes the loop** — incidents, outcomes, audits, and operating evidence update governance.
12. **Human accountability** — tools and AI assist; authorised people decide and approve.

## 4. Governance Model

### Governance Levels

| Level | Scope | Typical Authority | Evidence |
|---|---|---|---|
| Enterprise | Company-wide engineering strategy, risk appetite, major investment | Founder, CTO, executive authority | Strategy, portfolio, risk decision |
| Engineering System | EEOS principles, cross-domain policy, shared standards | CTO or delegated engineering governance authority | Framework, standard, decision record |
| Domain | Architecture, security, platform, data, API, AI, operations | Accountable domain lead or council | Domain review and roadmap |
| Product or Platform | Product boundary, service, capability, lifecycle | Product and engineering owners | Requirements, design, risk, lifecycle evidence |
| Team | Reversible implementation within approved boundaries | Tech Lead or delegated engineer | Code, test, review, operational evidence |
| Incident or Emergency | Time-critical containment and restoration | Incident Commander and emergency authority | Incident and retrospective record |

### Control Modes

| Mode | Use When | Mechanism |
|---|---|---|
| Self-governed | Low-risk and within approved standards | Team review and automated evidence |
| Consulted | Specialist input improves a reversible decision | Time-boxed consultation |
| Reviewed | Material cross-system or risk impact exists | Independent domain review |
| Approved | Risk, cost, exposure, or irreversibility exceeds delegated authority | Explicit authorised decision |
| Emergency | Delay creates greater harm | Delegated action with retrospective review |

## 5. Decision Rights

### Decision Classification

Classify decisions using:

- Scope of affected teams, consumers, systems, data, or customers.
- Business, security, privacy, reliability, financial, and compliance impact.
- Reversibility and migration cost.
- Novelty, uncertainty, and evidence quality.
- Duration and lifecycle consequence.
- External obligation or public exposure.

### Decision Matrix

| Decision | Recommends | Reviews | Approves | Records |
|---|---|---|---|---|
| Engineering strategy | CTO and engineering leadership | Executive stakeholders | Founder or executive authority | Strategy or roadmap |
| Architecture principle | Architecture authority | Domain leads | CTO or delegated authority | Principle and ADR |
| Solution architecture | Architect and team | Required domain specialists | Delegated architecture authority | Architecture and ADRs |
| Engineering standard | Subject-matter owner | Affected domains and teams | Standard owner or governance authority | Versioned Standard |
| Technology adoption | Sponsor and owner | Architecture, security, platform, finance as applicable | Delegated technology authority | Technology decision |
| AI capability or use | Product or engineering owner | AI, security, privacy, legal as applicable | Delegated AI authority | AI assessment and approval |
| Security risk acceptance | Engineering and security owners | Security authority | Named risk owner | Risk acceptance |
| Data use or retention | Product and data owners | Steward, security, privacy | Delegated data authority | Data decision |
| Platform product | Platform Product Owner | Architecture, security, operations, DevEx | Platform authority | Product and lifecycle record |
| API publication or breaking change | API Product Owner | Capability, security, data, consumers | API authority | API review and change record |
| Production change | Change owner | Risk-proportionate reviewers | Change authority | Change Record |
| Emergency action | Incident Commander | Available specialists | Emergency authority | Incident Record |
| Exception | Requesting owner | Standard or domain owner | Named exception authority | Exception Record |

Authority may be delegated in writing, but accountability and escalation thresholds remain explicit.

## 6. Organisational Roles

| Role | Governance Responsibilities |
|---|---|
| Founder or Executive Authority | Sets company direction, risk appetite, investment, and ultimate escalation decisions |
| CTO or Engineering Executive | Owns engineering strategy, EEOS effectiveness, cross-domain alignment, and delegated authorities |
| Chief or Principal Architect | Owns architecture governance, principles, strategic coherence, and major design review |
| Domain Lead | Owns domain policy, roadmap, standards, risk, and lifecycle |
| Engineering Manager | Owns team capability, delivery system, staffing, escalation, and adoption |
| Staff or Principal Engineer | Provides cross-team technical leadership, review, and systemic improvement |
| Tech Lead | Owns solution decisions within delegated boundaries and ensures evidence |
| Product Owner | Owns value, priority, users, acceptance, and lifecycle outcomes |
| Security or Risk Owner | Owns security review, risk treatment, acceptance boundaries, and assurance |
| Data Owner or Steward | Owns meaning, quality, permitted use, access, retention, and lifecycle |
| Platform Product Owner | Owns platform users, outcomes, service, adoption, and lifecycle |
| Document or Standard Owner | Maintains accuracy, review, version, relationships, and retirement |
| Contributor | Follows governance, raises exceptions, preserves traceability, and reports evidence |
| AI Assistant | May analyse and draft; cannot own, approve, accept risk, or exercise delegated authority |

Named individuals and deputies should be maintained in an organisational authority register when the team grows beyond direct founder governance.

## 7. Engineering Councils

Councils are optional mechanisms, not permanent requirements. Establish one only when decision volume or cross-team impact exceeds direct-owner governance.

| Council | Scope | Typical Decisions |
|---|---|---|
| Engineering Leadership Council | Strategy, portfolio, investment, systemic performance | Priorities, funding, major risk |
| Architecture Review Group | Cross-system architecture and technology | Principles, major designs, technology lifecycle |
| Engineering Standards Group | Shared mandatory practices | Standard creation, revision, deprecation, exceptions |
| Platform Council | Shared platform products and adoption | Roadmap, service, golden paths, retirement |
| Security and Risk Council | Material security and privacy risk | Risk treatment, exceptions, systemic controls |
| AI Governance Group | AI capability, data, evaluation, and human control | Approved use, restrictions, evaluation, incident learning |
| Data Governance Group | Data products, meaning, quality, use, and lifecycle | Ownership, access, retention, shared definitions |
| API Governance Group | Shared or external API products | Publication, breaking change, deprecation |

Every council shall publish scope, authority, quorum, inputs, decisions, owners, dates, and escalation. Advisory councils do not silently become approval gates.

## 8. Architecture Governance

Architecture Governance shall:

- Maintain architecture principles and strategic boundaries.
- Define review thresholds by impact, novelty, and reversibility.
- Require traceability from requirements and quality attributes to architecture.
- Record material decisions through ADRs.
- Review cross-domain, shared-platform, public-interface, data, security, and resilience impact.
- Govern technology lifecycle and architectural exceptions.
- Validate that implementation and operation remain aligned with approved intent.
- Use [`PB-ARCH`](02-playbooks/PB-ARCH.md) and [`PB-TECH-DESIGN`](02-playbooks/PB-TECH-DESIGN.md) for delivery work.

Local, reversible design inside approved boundaries remains a team decision.

## 9. Standards Governance

### Standard Lifecycle

```text
Need → Draft → Review → Approve → Publish → Adopt → Measure → Revise or Retire
```

Every Standard shall define:

- Problem, scope, owner, audience, and authority.
- Normative requirements and rationale.
- Verification and evidence.
- Adoption and migration expectations.
- Exception authority and process.
- Version, compatibility, review, deprecation, and retirement.
- Relationships to Principles, Playbooks, References, Templates, and Examples.

Standards are not approved merely because a file exists. Draft Standards remain non-authoritative until reviewed and approved.

## 10. Technology Governance

Technology Governance covers languages, frameworks, runtimes, platforms, data stores, infrastructure, services, tools, vendors, and critical dependencies.

Assess:

- Validated need and existing alternatives.
- Strategic fit and owner.
- Security, privacy, compliance, and data handling.
- Reliability, performance, scalability, and operability.
- Skills, developer experience, support, and ecosystem health.
- Licensing, cost, concentration, portability, and exit.
- Upgrade, patch, lifecycle, deprecation, and retirement.

Technology states may include Assess, Trial, Adopt, Contain, and Retire. A future Technology Radar may publish these decisions but does not replace their evidence.

## 11. AI Governance

AI Governance shall define:

- Approved capabilities, users, use cases, and prohibited uses.
- Data classification, context, retention, provider, and privacy restrictions.
- Human authority, review, verification, and escalation.
- Evaluation for correctness, safety, security, bias, reliability, and fitness.
- Traceability for material AI-assisted work.
- Access, cost, vendor, model, version, incident, and lifecycle management.
- Monitoring for failure, drift, misuse, and changing risk.

All engineering AI use follows [`PB-AI-ENGINEERING`](02-playbooks/PB-AI-ENGINEERING.md). AI cannot approve its own output or accept residual risk.

## 12. Security Governance

Security Governance shall:

- Define security profiles and review thresholds.
- Maintain risk and exception authority.
- Integrate threat modelling, secure design, verification, vulnerability, incident, and maintenance work.
- Define unacceptable risk and release-blocking conditions.
- Govern identity, access, secrets, data protection, supply chain, monitoring, and disclosure.
- Track remediation, acceptance, expiry, and systemic improvement.
- Preserve independent review for material risk.

Security engineering work follows [`PB-SECURITY-ENGINEERING`](02-playbooks/PB-SECURITY-ENGINEERING.md).

## 13. Data Governance

Data Governance shall define:

- Data product, source, owner, steward, and authoritative meaning.
- Classification, purpose, permitted use, access, sharing, and residency.
- Contract, schema, quality, metadata, and lineage expectations.
- Retention, legal hold, deletion, and verified disposal.
- Consumer, supplier, model, AI, and analytical use.
- Change, compatibility, migration, incident, and lifecycle authority.

Data engineering work follows [`PB-DATA-ENGINEERING`](02-playbooks/PB-DATA-ENGINEERING.md).

## 14. Platform Governance

Platform Governance shall define:

- Platform product ownership, users, roadmap, and service expectations.
- Capability boundaries and consumer responsibilities.
- Golden paths, secure defaults, self-service, and exceptions.
- Reliability, support, capacity, cost, vendor, and continuity.
- Adoption, developer outcomes, change, compatibility, and lifecycle.
- Contribution and extension boundaries.

Platform work follows [`PB-PLATFORM-ENGINEERING`](02-playbooks/PB-PLATFORM-ENGINEERING.md); developer outcomes follow [`PB-DEVELOPER-EXPERIENCE`](02-playbooks/PB-DEVELOPER-EXPERIENCE.md).

## 15. API Governance

API Governance shall define:

- API product, capability, technical, security, and operational ownership.
- Consumer, exposure, contract, publication, and access requirements.
- Protocol-specific standards and design-review thresholds.
- Security, data, privacy, service, observability, and support.
- Versioning, compatibility, change communication, migration, deprecation, and retirement.
- Catalogue registration and consumer identification.

API lifecycle work follows [`PB-API-MANAGEMENT`](02-playbooks/PB-API-MANAGEMENT.md).

## 16. Technical Debt Governance

Technical debt is a current or deferred engineering condition that increases future cost, risk, or constraint.

Govern debt through:

- Clear description, affected asset, owner, evidence, and cause.
- Consequence across delivery, quality, reliability, security, data, cost, and DevEx.
- Intentional versus unintentional classification.
- Treatment options: tolerate, contain, reduce, replace, or retire.
- Priority based on interest and risk, not age alone.
- Capacity allocation and roadmap integration.
- Outcome verification and closure.

Debt shall not become a separate unprioritised backlog. It competes transparently with other product and engineering work.

## 17. Exception Management

An exception is a temporary, approved deviation from an authoritative requirement.

### Required Record

| Field | Requirement |
|---|---|
| Requirement | Standard or control being deviated from |
| Scope | Systems, versions, environments, users, and data |
| Reason | Why compliance is not currently feasible or proportionate |
| Risk | Consequence, likelihood, uncertainty, and affected parties |
| Compensating Controls | Temporary measures and monitoring |
| Owner | Person accountable for treatment |
| Approver | Authority accepting residual risk |
| Start and Expiry | Time-bounded validity |
| Remediation | Plan, milestones, and target state |
| Review and Closure | Evidence, decision, and final disposition |

Expired exceptions become non-compliance and require escalation. Repeated exceptions may indicate a defective Standard or platform capability and trigger systemic review.

## 18. Risk Management

Engineering risk management shall:

1. Identify affected objectives, assets, users, data, systems, and obligations.
2. Describe plausible events and consequences.
3. Assess likelihood, impact, exposure, uncertainty, and existing controls.
4. Select avoid, reduce, transfer, or accept.
5. Assign treatment, owner, deadline, validation, and monitoring.
6. Escalate beyond delegated risk appetite.
7. Review after material change, incident, control failure, or expiry.

Risk acceptance is a decision, not the absence of remediation. Critical or systemic risk must be visible to engineering leadership.

## 19. Compliance and Assurance

Engineering demonstrates conformance through normal delivery evidence where possible:

- Approved requirements, architecture, designs, and decisions.
- Reviewed code, configuration, infrastructure, and contracts.
- Test, security, quality, deployment, and operational evidence.
- Ownership, inventory, access, change, incident, vulnerability, and lifecycle records.
- Standard adoption, exceptions, risk acceptance, and remediation.
- Periodic control-effectiveness review.

Compliance mappings do not create duplicate engineering processes. External obligations are mapped to authoritative internal controls, owners, and evidence.

## 20. Metrics

Use a balanced governance scorecard:

| Dimension | Example Measures | Guardrail |
|---|---|---|
| Decision Flow | Review lead time, ageing, rework | Faster is not always better |
| Decision Quality | Reversal, incident, exception, outcome | Novel work carries uncertainty |
| Standards | Adoption, verification, exception, expiry | Count does not prove effectiveness |
| Risk | Exposure, overdue treatment, acceptance age | Avoid hiding risk through classification |
| Architecture | Decision coverage, drift, migration progress | More ADRs is not inherently better |
| Security | Material findings, remediation, control effectiveness | Reporting must remain safe |
| Platform and DevEx | Adoption, task outcomes, reliability, cognitive load | Do not rank individuals |
| Data and API | Ownership, quality, compatibility, lifecycle | Coverage must be current |
| Technical Debt | Interest, risk trend, treatment effectiveness | Debt volume alone is misleading |
| Lifecycle | Review currency, deprecation, retirement | Exceptions require expiry |

Metrics improve the governance system; they do not evaluate individual performance.

## 21. Review Cadence

| Cadence | Purpose | Participants | Outputs |
|---|---|---|---|
| Continuous | Automated conformance and team decisions | Teams and owners | Evidence, findings, remediation |
| Weekly or Event-Driven | Operational risk, incidents, urgent changes | Relevant operational owners | Decisions and actions |
| Monthly | Domain portfolio, exceptions, risk, and decision flow | Domain leads | Updated risks, roadmaps, escalations |
| Quarterly | Cross-domain architecture, technology, capability, and outcomes | Engineering leadership and domain authorities | Portfolio decisions and priorities |
| Semi-Annual | Standards effectiveness and lifecycle | Standard owners and affected teams | Revise, retain, or retire decisions |
| Annual | EEOS, governance, maturity, metrics, and authority review | Founder, CTO, engineering leadership | Approved improvement plan |

Cadence scales with organisational need. Event-driven review overrides calendar delay for material risk.

## 22. Continuous Improvement

Governance improves through:

- Decision outcome reviews.
- Incident, postmortem, vulnerability, and audit learning.
- Developer and stakeholder feedback.
- Exception and bypass patterns.
- Standard adoption and control-effectiveness evidence.
- Architecture, technology, platform, data, API, and lifecycle metrics.
- Periodic simplification of meetings, approvals, and artefacts.

Every improvement has an owner, expected outcome, evidence, target date, and review. Remove governance that no longer provides value or control.

## 23. Related Documents

### Control Layer

- [ILOS Architecture](../../ilos/ILOS-ARCHITECTURE.md)
- [ILOS Governance](../../ilos/ILOS-GOVERNANCE.md)
- [ILOS Lifecycle](../../ilos/ILOS-LIFECYCLE.md)
- [ILOS Roadmap](../../ilos/ILOS-ROADMAP.md)

### Engineering Knowledge

- [Engineering Principles](01-principles/README.md)
- [Engineering Playbooks](02-playbooks/README.md)
- [Engineering Standards](03-standards/README.md)
- [Engineering References](04-reference/README.md)
- [Engineering Examples](05-examples/README.md)

### Governing Standards and References

- [Engineering Review Standard](03-standards/STD-REVIEW.md)
- [Engineering Traceability Standard](03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](03-standards/STD-VERSIONING.md)
- [Engineering Identifier Reference](04-reference/REF-IDENTIFIERS.md)

### Planned Supporting Frameworks

- Engineering Maturity Model.
- Engineering Metrics Framework.
- Technology Radar.
- Cross-reference Matrix.

## Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.0 | 2026-07-31 | Invara Labs Engineering | Draft | Initial Engineering Governance Framework covering decision rights, roles, councils, domain governance, technical debt, exceptions, risk, assurance, metrics, cadence, and improvement |

## Status

🟡 Draft

Formal approval, delegated authority assignments, and supporting governance templates remain required before this framework is authoritative.
