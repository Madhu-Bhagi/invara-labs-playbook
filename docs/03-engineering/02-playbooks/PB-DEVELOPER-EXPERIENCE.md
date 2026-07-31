---
title: Developer Experience Playbook
id: PB-DEVELOPER-EXPERIENCE
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
  - developer-experience
  - devex
  - platform
  - productivity
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
  - PB-SECURITY-ENGINEERING
  - PB-DATA-ENGINEERING
  - PB-API-MANAGEMENT
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

# Developer Experience Playbook

> **The standard operating procedure for designing, operating, measuring, and continuously improving the end-to-end engineering experience so developers can deliver software efficiently, consistently, securely, and with manageable cognitive load.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. Developer Experience Principles
6. Developer Journey
7. When to Use This Playbook
8. Roles and Responsibilities
9. Inputs
10. Entry Criteria
11. Developer Experience Workflow
12. DevEx Lifecycle
13. Detailed Phase Activities
14. Developer Enablement
15. Engineering Productivity
16. Tooling Strategy
17. Documentation Experience
18. Developer Self-Service
19. Feedback and Measurement
20. AI-Assisted Developer Experience
21. Platform Integration
22. Governance
23. Risk Management
24. Deliverables
25. Quality Gates
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

Developer Experience (DevEx) is the quality of an engineer’s interaction with the systems, tools, knowledge, environments, workflows, and organisational interfaces needed to deliver and operate software.

DevEx work identifies avoidable friction, validates its impact, improves the complete journey, and measures whether engineers can achieve valuable outcomes more safely and predictably.

Developer Experience is not:

- A one-time onboarding guide.
- IDE, Git, or local-setup documentation.
- A collection of productivity tools.
- A platform portal or internal wiki.
- Coding standards.
- A programme for measuring individual developer output.

Those may contribute to the experience, but this playbook governs how the organisation improves it.

```text
Developer Goal
      │
      ▼
Discover → Understand → Access → Configure
      │
      ▼
Build → Verify → Review → Release → Operate
      │
      ▼
Diagnose → Recover → Learn → Improve
```

## 2. Purpose

This playbook defines how Invara Labs:

- Understands developer users and end-to-end journeys.
- Identifies friction, delay, cognitive load, risk, and repetitive work.
- Prioritises improvements by developer and organisational outcomes.
- Designs usable, secure, accessible, and supportable workflows.
- Integrates platform, tooling, documentation, automation, and enablement.
- Pilots improvements before broad rollout.
- Measures adoption, task success, flow, satisfaction, and quality.
- Operates and maintains DevEx capabilities as products.
- Learns continuously without surveilling or ranking individuals.

## 3. Objectives

Applying this playbook should produce:

- Faster time to first meaningful contribution.
- Reproducible development environments.
- Shorter, more reliable feedback loops.
- Discoverable and trustworthy engineering knowledge.
- Safe self-service for common tasks.
- Lower avoidable cognitive load and manual toil.
- Better cross-team collaboration and contribution.
- Higher developer confidence and satisfaction.
- Measurable delivery improvement without sacrificing quality or security.
- Governed tooling and workflow lifecycle.

## 4. Scope

### In Scope

- Joining, onboarding, team transfer, and role transitions.
- Local, remote, containerised, and cloud development environments.
- Source, build, test, review, release, deployment, and operational workflows.
- Engineering portals, catalogues, templates, command-line tools, and automation.
- Documentation, search, examples, support, and knowledge discovery.
- Access, secrets, environments, infrastructure, and self-service journeys.
- AI-assisted engineering experience.
- Inner-source contribution and cross-team collaboration.
- Developer research, metrics, feedback, experimentation, and improvement.

### Out of Scope

- Individual performance evaluation.
- Employee engagement or HR policy.
- Product-customer experience.
- Technology-specific setup and tooling standards.
- Product requirements and business-process ownership.
- Removing required security, risk, privacy, accessibility, or operational controls.

## 5. Developer Experience Principles

1. **Outcome-first** — optimise the developer’s complete goal, not one tool step.
2. **Developer-centred** — use observed needs and representative research.
3. **Self-service where safe** — remove routine waiting while preserving necessary authority.
4. **Discoverable** — make the right path, owner, status, and support easy to find.
5. **Fast feedback** — return useful information close to the action.
6. **Secure by default** — make compliant behaviour the easiest supported path.
7. **Consistent, not rigid** — provide coherent defaults and governed variation.
8. **Transparent** — explain automation, policy, failure, cost, and ownership.
9. **Measurable with care** — combine system evidence and human feedback.
10. **Accessible and inclusive** — support different abilities, locations, roles, and experience levels.
11. **Product-oriented** — own, operate, support, version, and retire DevEx capabilities.
12. **Continuously improving** — learn from friction, bypasses, incidents, and change.

## 6. Developer Journey

Assess the end-to-end journey:

| Stage | Typical Developer Goal |
|---|---|
| Join | Understand organisation, team, responsibilities, and access |
| Discover | Find systems, owners, documentation, standards, and supported paths |
| Set Up | Establish a working, reproducible, secure environment |
| Change | Understand, build, test, and validate software locally |
| Collaborate | Review, discuss, contribute, and integrate changes |
| Release | Promote verified work through governed automation |
| Operate | Observe health, respond, diagnose, and recover |
| Learn | Find examples, decisions, feedback, and improvement opportunities |
| Transition | Transfer ownership, change role, or offboard safely |

Every stage considers actions, systems, wait, handoffs, errors, cognitive load, risk, support, and evidence.

## 7. When to Use This Playbook

Use this playbook when:

- Onboarding or environment setup is slow or unreliable.
- Engineers cannot find authoritative knowledge or ownership.
- Builds, tests, reviews, releases, or access requests create repeated delay.
- Multiple teams invent different solutions to the same workflow.
- Support tickets, manual handoffs, or workarounds increase.
- Platform capabilities have poor adoption or high abandonment.
- New tools, portals, templates, or AI assistants are proposed.
- Delivery metrics change without a clear explanation.
- Engineers report high cognitive load or low confidence.

Do not create a DevEx initiative for isolated preference or tool fashion without evidence.

## 8. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| DevEx Product Owner | Owns developer outcomes, roadmap, research, prioritisation, adoption, and lifecycle |
| DevEx or Productivity Engineer | Designs, implements, measures, operates, and improves experiences |
| Platform Product Owner | Provides platform-product ownership and aligns shared capabilities |
| Platform Engineer | Builds secure, observable, self-service platform interfaces |
| Developer Representative | Provides journey evidence, pilots changes, and validates outcomes |
| Team Lead or Engineering Manager | Identifies team constraints and protects improvement participation |
| Documentation Owner | Owns information architecture, findability, accuracy, and lifecycle |
| Security Engineer | Ensures safe defaults, access, data protection, and risk-proportionate controls |
| Reliability or Operations Engineer | Ensures operational workflows, support, recovery, and service health |
| Data or Analytics Owner | Protects survey and telemetry data and supports valid measurement |
| Accessibility Representative | Reviews inclusive access and interaction requirements |
| Approver | Authorises high-risk rollout, policy, data collection, or lifecycle decisions |

## 9. Inputs

DevEx work may consume:

- Interviews, observation, surveys, retrospectives, and support conversations.
- Journey maps, onboarding records, documentation searches, and task studies.
- Build, test, review, deployment, incident, access, and platform metrics.
- Tool usage, workflow abandonment, failure, and support data.
- Architecture, platform, security, data, API, and engineering strategy.
- Team topology, role, location, accessibility, and environment constraints.
- Cost, licence, dependency, lifecycle, vendor, and support information.
- Quality, reliability, security, and customer-outcome evidence.

Inputs must distinguish individual anecdotes from repeated patterns while protecting privacy.

## 10. Entry Criteria

Before material DevEx work:

- Target developers and journey are defined.
- Friction is observed or evidenced.
- Current baseline and expected outcome are measurable.
- Product and technical ownership are assigned.
- Existing platform, documentation, process, or simpler changes are assessed.
- Security, privacy, accessibility, support, and data constraints are known.
- Representative pilot users are available.
- Success, stop, rollback, and review criteria are defined.
- Measurement does not create individual performance surveillance.

## 11. Developer Experience Workflow

```text
Understand Developer Goals
          │
          ▼
Map Journey and Identify Friction
          │
          ▼
Prioritise Outcome Opportunity
          │
          ▼
Design and Validate Experience
          │
          ▼
Build or Improve Capability
          │
          ▼
Pilot and Enable
          │
          ▼
Measure Adoption and Outcomes
          │
          ▼
Operate, Learn, and Improve
```

## 12. DevEx Lifecycle

| State | Meaning | Evidence |
|---|---|---|
| Discovered | Journey, users, friction, and baseline are understood | Research and Journey Map |
| Designed | Target experience, controls, and measures are validated | Experience Design |
| Pilot | Representative users exercise a supportable capability | Pilot evidence |
| Supported | Capability is discoverable, documented, operated, and measured | Service and Adoption evidence |
| Scaled | Intended user segments achieve reliable outcomes | Outcome review |
| Deprecated | Replacement and migration are available | Deprecation plan |
| Retired | Tool, workflow, access, documentation, and support are removed | Retirement evidence |

## 13. Detailed Phase Activities

### Phase 1: Understand Developer Needs

**Goal:** understand developers, goals, contexts, and constraints.

Activities:

- Segment users by role, journey, team context, and experience.
- Observe real work and interview representative developers.
- Review support, incident, onboarding, and workflow evidence.
- Identify required security, accessibility, location, and environment differences.
- Define baseline task outcomes and non-goals.
- Protect research confidentiality and voluntary participation.

Outputs:

- Developer Research Summary.
- User and Journey Segments.
- Baseline Evidence.

### Phase 2: Map Journey and Friction

**Goal:** locate avoidable effort across the complete workflow.

Activities:

- Map actions, systems, owners, handoffs, waits, failures, and recovery.
- Measure setup, feedback, review, release, access, and support delays.
- Identify missing knowledge, unclear policy, tool fragmentation, and duplicate work.
- Separate necessary control from accidental process.
- Identify workarounds, bypasses, abandonment, and hidden manual effort.
- Trace friction to developer, quality, security, reliability, and business impact.

Outputs:

- Developer Journey Map.
- Friction and Root-Cause Register.
- Opportunity Backlog.

### Phase 3: Prioritise Outcome Opportunity

**Goal:** select improvements with meaningful leverage.

Activities:

- Score frequency, affected users, delay, cognitive load, risk, quality, and cost.
- Assess existing capability, documentation, policy, and local-fix options.
- Choose eliminate, simplify, document, automate, self-serve, standardise, or stop.
- Define the smallest coherent outcome.
- Assign product, technical, operational, and documentation owners.
- Define success, guardrail, and stop metrics.

Outputs:

- Prioritised DevEx Roadmap.
- Improvement Hypothesis.
- Ownership and Measures.

### Phase 4: Design and Validate Experience

**Goal:** prove usability and safety before implementation.

Activities:

- Design the complete happy, failure, recovery, support, and exception journey.
- Prototype workflow, documentation, messages, and automation.
- Validate with representative developers.
- Review security, privacy, accessibility, reliability, cost, and lifecycle.
- Test discoverability and comprehension without insider guidance.
- Record trade-offs, rejected options, and acceptance criteria.

Outputs:

- Target Experience Design.
- User Validation Report.
- Pilot Plan.

### Phase 5: Build or Improve Capability

**Goal:** deliver a reliable, supportable improvement.

Activities:

- Reuse existing platform capabilities where possible.
- Implement automation, tooling, documentation, templates, or process changes.
- Provide actionable validation, progress, error, and recovery feedback.
- Add telemetry that measures systems without exposing sensitive individual behaviour.
- Test common, edge, failure, accessibility, and support paths.
- Prepare ownership, runbooks, change, maintenance, and retirement.

Outputs:

- DevEx Capability.
- Verification Evidence.
- Documentation and Support Package.

### Phase 6: Pilot and Enable

**Goal:** validate outcomes with limited real use.

Activities:

- Onboard a representative cohort.
- Observe task success, time, errors, confidence, and support.
- Compare against baseline and guardrails.
- Correct product gaps before broad mandate.
- Provide migration, examples, office hours, and feedback routes.
- Decide scale, revise, pause, or stop.

Outputs:

- Pilot Report.
- Adoption and Enablement Plan.
- Go, Revise, or Stop Decision.

### Phase 7: Measure Adoption and Outcomes

**Goal:** establish whether the improvement creates sustained value.

Activities:

- Track eligible, aware, activated, successful, retained, and expanded use.
- Measure task outcomes, flow, quality, security, and reliability.
- Gather voluntary sentiment, cognitive-load, and satisfaction feedback.
- Segment by journey and context, not individual ranking.
- Analyse bypasses, abandonment, tickets, and recurring failure.
- Compare total organisational cost and benefit.

Outputs:

- DevEx Outcome Scorecard.
- Adoption and Feedback Report.
- Investment Recommendation.

### Phase 8: Operate, Learn, and Improve

**Goal:** sustain value and remove experience debt.

Activities:

- Monitor availability, task success, performance, errors, support, and cost.
- Maintain tools, environments, dependencies, documentation, and access.
- Review incidents, workflow breaks, feedback, and platform changes.
- Consolidate duplicate tools and retire unused paths.
- Update journey, roadmap, measures, and enablement.
- Communicate changes and migration clearly.

Outputs:

- Health and Lifecycle Evidence.
- Continuous Improvement Backlog.
- Migration or Retirement Record.

## 14. Developer Enablement

Developer enablement includes:

- Role- and journey-based onboarding.
- Working examples and reference implementations.
- Guided practice, workshops, office hours, and communities.
- Ownership and escalation discovery.
- Contribution guidance and inner-source support.
- Learning paths tied to real engineering tasks.

Enablement is not a substitute for fixing a broken workflow. Repeated training demand may indicate a product or documentation defect.

## 15. Engineering Productivity

Engineering productivity is the system’s ability to convert effort into valuable, safe, maintainable outcomes.

Assess:

- **Flow:** waiting, handoffs, work-in-progress, review, and release.
- **Feedback:** build, test, policy, review, and operational signal speed.
- **Quality:** defects, rework, rollback, reliability, and maintainability.
- **Cognitive load:** knowledge, context switching, complexity, and uncertainty.
- **Satisfaction:** confidence, autonomy, usefulness, and trust.

Do not use commits, lines, tickets, hours, AI usage, or activity as individual productivity measures.

## 16. Tooling Strategy

Engineering tools shall have:

- Validated users and supported outcomes.
- Named product, technical, operational, and security owners.
- Approved access, data, vendor, integration, and lifecycle.
- Versioning, compatibility, update, support, and exit plans.
- Documentation, examples, status, and escalation.
- Usage, outcome, health, cost, and satisfaction measures.

Prefer fewer coherent tools over overlapping choice without ownership. Allow justified exceptions with expiry.

## 17. Documentation Experience

Documentation must be:

- Reachable from the developer’s point of need.
- Written for a named task or understanding goal.
- Authoritative, owned, versioned, and reviewable.
- Searchable using the language developers actually use.
- Linked to systems, interfaces, errors, examples, and support.
- Tested through user tasks and feedback.
- Retired or redirected when obsolete.

Measure successful task completion, not page views alone.

## 18. Developer Self-Service

Self-service means an authorised developer can complete a supported task safely without routine human fulfilment.

It requires:

- Discoverable entry and prerequisites.
- Identity, least privilege, and policy.
- Validated inputs and preview where material.
- Repeatable automation with progress and actionable errors.
- Evidence, audit, cleanup, cancellation, recovery, and support.
- Published service and lifecycle expectations.

A form that creates a ticket is not mature self-service.

## 19. Feedback and Measurement

Use mixed evidence:

- Interviews and observed task studies.
- Short, voluntary, purpose-specific surveys.
- Journey and system telemetry.
- Support, incident, review, and retrospective themes.
- Adoption, abandonment, bypass, and migration evidence.

Feedback collection shall define purpose, access, retention, anonymity, communication, and action. Close the loop by telling developers what changed or why it did not.

## 20. AI-Assisted Developer Experience

AI may assist with:

- Knowledge discovery and explanation.
- Onboarding and contextual support.
- Code, test, documentation, and troubleshooting drafts.
- Workflow and feedback analysis.
- Platform assistance and task guidance.

All AI-assisted work follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

DevEx owners must prevent secrets and prohibited data exposure, validate generated output, preserve source attribution where required, make limitations visible, provide non-AI paths, and retain human authority.

AI adoption is not a DevEx outcome unless it improves measured engineering results safely.

## 21. Platform Integration

Developer Experience defines user journeys and outcomes; Platform Engineering supplies shared product capabilities.

```text
DevEx Research and Outcome
          │
          ▼
Platform Product Opportunity
          │
          ▼
Golden Path and Self-Service
          │
          ▼
Adoption and Journey Evidence
          │
          └────────► DevEx Improvement
```

DevEx must not become a second platform backlog. Platform capabilities follow [`PB-PLATFORM-ENGINEERING`](PB-PLATFORM-ENGINEERING.md).

## 22. Governance

DevEx governance defines:

- Research, product, technical, platform, security, data, and approval ownership.
- Prioritisation and roadmap decision rights.
- Tool evaluation, adoption, exception, and retirement.
- Developer telemetry purpose, minimisation, access, retention, and prohibition on individual surveillance.
- Security, privacy, accessibility, reliability, support, and lifecycle gates.
- Documentation, service, change, incident, and maintenance ownership.
- Measurement interpretation and communication.

## 23. Risk Management

| Risk | Consequence | Treatment |
|---|---|---|
| Optimising activity | Busy metrics replace value | Outcome and guardrail measures |
| Individual surveillance | Trust and psychological safety fail | Aggregate system metrics, strict purpose and access |
| Tool sprawl | Cost, fragmentation, and cognitive load grow | Catalogue, ownership, consolidation, retirement |
| Platform complexity | Abstraction creates new friction | User validation, transparency, escape hatch |
| Automation failure | Errors scale quickly | Validation, staged rollout, recovery, support |
| Documentation decay | Developers follow unsafe or obsolete guidance | Ownership, review, testing, retirement |
| Mandated low-value path | Teams bypass the platform | Earn adoption through product outcomes |
| Excluded users | Workflow blocks accessibility, location, or role needs | Inclusive research and accessibility validation |
| Security bypass | Friction drives unmanaged workarounds | Usable controls and root-cause improvement |
| Survey fatigue | Feedback quality and participation fall | Purposeful cadence and visible action |
| Vendor lock-in | Exit becomes costly | Portable workflows, data controls, exit plan |

## 24. Deliverables

| Deliverable | Purpose |
|---|---|
| Developer Research Summary | Defines users, contexts, goals, and evidence |
| Developer Journey Map | Shows actions, systems, friction, risk, and opportunities |
| DevEx Roadmap | Prioritises outcome-led improvements |
| Target Experience Design | Defines happy, failure, recovery, support, and exception paths |
| DevEx Capability | Provides the implemented workflow, tool, documentation, or automation |
| Enablement Package | Supports adoption, migration, learning, and contribution |
| DevEx Outcome Scorecard | Measures journey, flow, quality, satisfaction, and adoption |
| Tool and Capability Catalogue | Publishes owner, support, data, cost, and lifecycle |
| Continuous Improvement Backlog | Tracks evidence-led changes |
| Lifecycle Record | Governs version, change, deprecation, and retirement |

## 25. Quality Gates

### Gate 1: Opportunity Validated

- Target developers, journey, friction, baseline, and root cause are evidenced.
- Existing and simpler solutions are assessed.
- Expected outcome and guardrails are measurable.
- Ownership and privacy boundaries are explicit.

### Gate 2: Experience Design Ready

- Complete journey, including failure, recovery, support, and exception, is designed.
- Representative developers validate usefulness and comprehension.
- Security, privacy, accessibility, reliability, cost, and lifecycle are reviewed.
- Pilot and stop criteria are approved.

### Gate 3: Pilot Ready

- Capability, documentation, telemetry, support, recovery, and rollback are verified.
- Measurement does not rank or surveil individuals.
- Pilot users, duration, baseline, feedback, and authority are defined.
- Change and operational ownership are ready.

### Gate 4: Supported Experience Ready

- Pilot evidence demonstrates task success and acceptable guardrails.
- Discoverability, self-service, documentation, support, service, and ownership are published.
- Adoption and migration plan exists.
- Launch decision and residual risk are recorded.

### Gate 5: Outcome and Lifecycle Review

- Adoption, task success, flow, quality, satisfaction, reliability, security, and cost are reviewed.
- Bypass, abandonment, support, incidents, and excluded users are examined.
- Invest, improve, consolidate, deprecate, or retire is decided.
- Owners, actions, dates, evidence, and next review are recorded.

## 26. Common Mistakes

- Treating DevEx as developer happiness alone.
- Building tooling before observing a journey.
- Measuring individual activity as productivity.
- Optimising one step while end-to-end flow remains broken.
- Automating an unclear or unstable process.
- Calling ticket intake self-service.
- Mandating a platform path before it earns trust.
- Adding documentation instead of simplifying the system.
- Collecting surveys without acting or closing the loop.
- Ignoring accessibility, remote, role, or experience differences.
- Creating a DevEx team that owns everyone else’s workflow quality.
- Keeping unused tools because migration is inconvenient.

## 27. Best Practices

- Observe real work and include different developer contexts.
- Start with one repeated, measurable journey.
- Fix root cause before adding training or documentation.
- Design feedback, failure, recovery, and support as first-class paths.
- Make secure defaults easier than bypasses.
- Give actionable feedback close to developer action.
- Pilot with representative users before scaling.
- Combine system metrics with qualitative evidence.
- Measure teams and systems, never rank individuals.
- Publish ownership, status, lifecycle, and support.
- Consolidate tools and retire obsolete paths.
- Communicate improvements and unresolved trade-offs honestly.

## 28. Templates

### DevEx Improvement Proposal

```text
Target developers and journey:
Observed friction and evidence:
Root cause:
Current baseline:
Expected outcome and guardrails:
Existing options:
Proposed experience:
Security, privacy, accessibility, reliability, and cost:
Pilot and feedback:
Ownership, support, and lifecycle:
Decision:
```

### Developer Journey Record

```text
Persona or segment:
Goal and trigger:
Stages and actions:
Systems and owners:
Wait and handoffs:
Errors and recovery:
Knowledge and support:
Cognitive load and confidence:
Security and accessibility:
Evidence and opportunities:
```

### Tool Evaluation

```text
Outcome and users:
Current alternatives:
Usability and integration:
Security, privacy, data, and vendor:
Reliability, support, and accessibility:
Cost, portability, and exit:
Pilot evidence:
Ownership and lifecycle:
Decision:
```

## 29. Examples

### Example: Time to First Deployment

Research finds new engineers wait for five manual access requests, follow three conflicting setup guides, and cannot diagnose a failed local dependency.

Improvement:

1. Consolidate authoritative onboarding.
2. Automate eligible access with role-based approval.
3. Provide a reproducible environment and validation command.
4. Link errors to actionable troubleshooting.
5. Provide a guided first service change and deployment.
6. Measure median and tail time, success, support, confidence, and security exceptions.

### Example: Slow Test Feedback

Rather than purchasing a new tool immediately, the team profiles queue time, environment startup, test selection, flaky retries, and failure diagnosis. It removes duplicated suites, adds affected-test selection, fixes the slow environment path, and improves failure output.

The outcome is faster trustworthy feedback, not simply shorter execution.

### Example: Do Not Build a New Portal

Developers cannot find service ownership. The existing catalogue contains the information, but navigation and search terms are poor.

Decision: improve catalogue metadata, search, entry links, and ownership validation. Do not create another portal.

## 30. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Coding Principles](../01-principles/04-coding-principles.md)
- [Testing Principles](../01-principles/05-testing-principles.md)
- [Security Principles](../01-principles/06-security-principles.md)
- [Observability Principles](../01-principles/07-observability-principles.md)
- [Performance Principles](../01-principles/08-performance-principles.md)

## 31. Related Standards

- [Playbook Authoring Standard](../03-standards/PB-AUTHORING.md)
- [Documentation Style Guide](../03-standards/DOC-STYLE.md)
- [Engineering Terminology Standard](../03-standards/TERM-STANDARD.md)
- [Engineering Review Standard](../03-standards/STD-REVIEW.md)
- [Engineering Traceability Standard](../03-standards/STD-TRACEABILITY.md)
- [Engineering Metadata Standard](../03-standards/STD-METADATA.md)
- [Engineering Versioning Standard](../03-standards/STD-VERSIONING.md)

Developer-environment, documentation, automation, engineering-tool, accessibility, and telemetry standards are planned and non-authoritative.

## 32. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)

Onboarding, developer-portal, golden-path, tool-catalogue, DevEx measurement, and inner-source references are planned and non-authoritative.

## 33. Related Playbooks

- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted developer workflows.
- [Coding Playbook](PB-CODING.md), [Code Review Playbook](PB-CODE-REVIEW.md), and [Testing Playbook](PB-TESTING.md) govern execution and feedback journeys.
- [Deployment Playbook](PB-DEPLOYMENT.md) and [Observability Playbook](PB-OBSERVABILITY.md) govern release and operational journeys.
- [Incident Management Playbook](PB-INCIDENT-MANAGEMENT.md), [Change Management Playbook](PB-CHANGE-MANAGEMENT.md), and [Maintenance Playbook](PB-MAINTENANCE.md) govern operational and lifecycle journeys.
- [Platform Engineering Playbook](PB-PLATFORM-ENGINEERING.md) supplies shared platform products.
- [Security Engineering Playbook](PB-SECURITY-ENGINEERING.md) governs secure and privacy-aware experience controls.
- [Data Engineering Playbook](PB-DATA-ENGINEERING.md) governs DevEx measurement data when treated as a data product.
- [API Management Playbook](PB-API-MANAGEMENT.md) governs developer-facing API products.

## 34. Metrics

Use a balanced system view:

| Dimension | Example Metrics | Guardrail |
|---|---|---|
| Onboarding | Time and success to first environment, commit, review, deployment | Segment role and prerequisites |
| Feedback | Build, test, policy, review, and deployment feedback time | Faster wrong feedback is harmful |
| Flow | Wait, handoffs, work age, rework, flow efficiency | Context matters |
| Task Outcome | Setup, build, release, access, diagnosis success | Measure complete journey |
| Experience | Satisfaction, cognitive load, confidence, documentation success | Voluntary and aggregated |
| Platform | Eligible, activated, successful, retained use | Adoption is not value alone |
| Quality | Defects, rollback, failure, flaky tests, rework | Do not trade quality for speed |
| Reliability | Tool availability, errors, recovery, support | Measure developer impact |
| Security | Secure-path use, policy remediation, exception and bypass | Avoid blaming developers |
| Cost | Tool, infrastructure, support, waiting, and unit journey cost | Include migration and exit |

Metrics evaluate systems and teams. They must not rank individual engineers.

## 35. Reference Implementation and Enterprise Appendices

### 35.1 Developer Journey Map

| Stage | Goal | Actions | Systems | Wait | Friction | Recovery | Cognitive Load | Evidence | Opportunity |
|---|---|---|---|---:|---|---|---|---|---|

### 35.2 DevEx Survey Template

Use short, voluntary prompts:

- I can find the authoritative information needed for my work.
- My development environment is reliable and reproducible.
- I receive fast, actionable feedback.
- Supported workflows make safe delivery easier.
- I can diagnose failures and find help.
- Engineering tools reduce rather than add cognitive load.

Collect optional context by journey, not identifying performance.

### 35.3 Onboarding Checklist

- [ ] Team, role, system, owner, and support are clear.
- [ ] Required access is approved and attributable.
- [ ] Environment setup is reproducible and validated.
- [ ] Authoritative documentation and supported paths are discoverable.
- [ ] First build, test, review, deployment, and operational journey succeed.
- [ ] Security, privacy, incident, and escalation responsibilities are understood.
- [ ] Feedback is collected and acted upon.

### 35.4 Engineering Productivity Dashboard

| Dimension | Indicator | Baseline | Target | Current | Trend | Guardrail | Owner |
|---|---|---:|---:|---:|---|---|---|
| Flow | | | | | | | |
| Feedback | | | | | | | |
| Quality | | | | | | | |
| Experience | | | | | | | |
| Reliability | | | | | | | |
| Security | | | | | | | |

### 35.5 Tool Evaluation Matrix

| Criterion | Weight | Option A | Option B | Existing | Evidence |
|---|---:|---:|---:|---:|---|
| User outcome | | | | | |
| Usability | | | | | |
| Integration | | | | | |
| Security and privacy | | | | | |
| Reliability and support | | | | | |
| Accessibility | | | | | |
| Cost and exit | | | | | |

### 35.6 Documentation Health Checklist

- [ ] Purpose, audience, owner, scope, version, and status are visible.
- [ ] Content matches the current system and supported workflow.
- [ ] Developers can find it using expected language.
- [ ] Examples, links, commands, and troubleshooting are verified.
- [ ] Feedback and change triggers exist.
- [ ] Obsolete content is updated, redirected, archived, or removed.

### 35.7 Self-Service Capability Matrix

| Journey | Eligible Users | Current Handoffs | Self-Service | Policy | Recovery | Support | Outcome | Owner |
|---|---|---|---|---|---|---|---|---|

### 35.8 DevEx Maturity Model

| Level | Characteristics |
|---|---|
| 1 — Reactive | Tribal knowledge, manual tickets, fragmented tools |
| 2 — Repeatable | Documented workflows and basic ownership |
| 3 — Productised | Journey research, self-service, support, outcome metrics |
| 4 — Managed | Secure defaults, feedback loops, lifecycle, balanced measures |
| 5 — Adaptive | Evidence-led improvement, composable platform, routine retirement |

### 35.9 Platform Adoption Dashboard

| Stage | Eligible | Aware | Activated | Successful | Retained | Expanded | Abandoned | Action |
|---|---:|---:|---:|---:|---:|---:|---:|---|

### 35.10 Deliverables Checklist

- [ ] Research, journey, friction, root cause, baseline, and measures.
- [ ] Roadmap, experience design, validation, ownership, and pilot.
- [ ] Capability, tests, documentation, telemetry, support, and recovery.
- [ ] Adoption, outcome, feedback, guardrail, and cost evidence.
- [ ] Lifecycle, migration, retirement, approval, and next review.

### 35.11 Continuous Improvement Backlog

| Evidence | Journey | Root Cause | Outcome | Improvement | Priority | Owner | Target | Validation | Status |
|---|---|---|---|---|---|---|---|---|---|

### 35.12 Quarterly DevEx Review Template

```text
Developer segments and journeys reviewed:
Outcome, flow, feedback, quality, and experience trends:
Platform, tool, documentation, support, and adoption:
Security, privacy, accessibility, reliability, and cost:
Top friction, root causes, bypasses, and excluded users:
Experiments and prior action effectiveness:
Decisions: invest / improve / consolidate / deprecate / retire
Actions, owners, dates, approval, and next review:
```

## 36. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Developer Experience Playbook with eight-phase journey workflow, enablement, productivity, tooling, documentation, self-service, feedback, platform integration, five quality gates, metrics, and twelve enterprise appendices |

## 37. Summary

`PB-DEVELOPER-EXPERIENCE` governs how the engineering experience is designed and improved.

It requires teams to:

- Observe real developer goals and journeys.
- Fix root causes across tools, platforms, documentation, automation, and process.
- Provide secure, accessible, supportable self-service.
- Measure system outcomes without surveilling individuals.
- Operate DevEx capabilities as products.
- Consolidate and retire experience debt.

This Draft completes the proposed five-playbook Enterprise Engineering Capability set. Formal review, approval, supporting Standards, References, Templates, and Examples remain required before EEOS v1.0 is considered complete.
