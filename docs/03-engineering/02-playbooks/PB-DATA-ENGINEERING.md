---
title: Data Engineering Playbook
id: PB-DATA-ENGINEERING
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
  - data-engineering
  - data-platform
  - data-governance
  - analytics
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

# Data Engineering Playbook

> **The standard operating procedure for designing, building, operating, governing, and continuously improving data platforms, pipelines, and data products throughout their lifecycle.**

## Table of Contents

1. Overview
2. Purpose
3. Objectives
4. Scope
5. Data Engineering Principles
6. Data Product Mindset
7. When to Use This Playbook
8. Roles and Responsibilities
9. Inputs
10. Entry Criteria
11. Data Engineering Workflow
12. Data Lifecycle
13. Detailed Phase Activities
14. Data Architecture
15. Data Modelling
16. Data Integration
17. Data Quality Management
18. Metadata and Lineage
19. Data Governance
20. Data Security and Privacy
21. Data Platform Operations
22. AI-Assisted Data Engineering
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

Data Engineering turns raw, operational, partner, and event data into trusted and reusable data products.

A data product is a governed data asset designed for defined consumers. It has an owner, contract, quality expectations, documentation, access rules, operational support, and lifecycle. It may be a table, event stream, API-delivered dataset, feature set, model input, or other consumable data interface.

Data Engineering is not:

- An ETL tool guide.
- A database-administration procedure.
- A SQL style standard.
- Dashboard or report design.
- Statistical analysis.
- A specific warehouse, lake, stream, or orchestration architecture.

Those details belong in implementation-specific Standards and References.

```text
Business or Operational Need
            │
            ▼
Owned Sources and Data Contracts
            │
            ▼
Governed Processing and Quality
            │
            ▼
Discoverable Data Product
            │
            ▼
Consumer Outcome
            │
            ▼
Usage, Quality, Cost, and Lifecycle Evidence
```

## 2. Purpose

This playbook defines how Invara Labs:

- Discovers and validates data-consumer needs.
- Establishes ownership and authoritative sources.
- Designs data products, contracts, models, and integration.
- Builds reliable batch, streaming, and change-data workflows.
- Defines, tests, monitors, and improves data quality.
- Captures metadata, lineage, usage, and dependencies.
- Governs classification, access, retention, privacy, and disposal.
- Operates data platforms and products with service expectations.
- Changes schemas and contracts without unmanaged consumer harm.
- Deprecates and retires data safely.

## 3. Objectives

Applying this playbook should produce:

- Data products with clear purpose, owners, and consumers.
- Traceable sources, transformations, lineage, and outputs.
- Explicit and versioned data contracts.
- Measurable quality, freshness, availability, and performance.
- Secure and privacy-aware data use.
- Discoverable metadata and understandable semantics.
- Reliable pipelines with recovery and replay strategies.
- Controlled schema and lifecycle evolution.
- Transparent cost and operational ownership.
- Evidence supporting analytics, operations, machine learning, and AI.

## 4. Scope

### In Scope

- Data platforms, products, pipelines, stores, and integration.
- Operational, analytical, batch, streaming, and event data.
- Source onboarding, ingestion, transformation, publication, and consumption.
- Data contracts, schemas, models, and semantic meaning.
- Data quality, metadata, catalogue, lineage, and observability.
- Ownership, stewardship, access, privacy, retention, and disposal.
- Backfill, replay, reconciliation, migration, deprecation, and retirement.
- Datasets used by machine learning and AI systems.

### Out of Scope

- Business-report design and dashboard presentation.
- Statistical or scientific methodology.
- Model-training and model-governance procedures.
- Database product documentation.
- Tool-specific pipeline, SQL, or infrastructure standards.
- Legal interpretation of privacy or regulatory obligations.

Out-of-scope functions may still supply requirements and approval.

## 5. Data Engineering Principles

1. **Product-oriented** — design data for named consumers and outcomes.
2. **Owned** — every product, source, contract, and critical pipeline has an accountable owner.
3. **Contract-driven** — producers and consumers share explicit, versioned expectations.
4. **Quality is contextual** — quality means fitness for an agreed use, not abstract perfection.
5. **Secure and private by default** — minimise, classify, restrict, protect, retain, and dispose deliberately.
6. **Discoverable** — meaning, ownership, quality, lineage, and access are findable.
7. **Observable** — freshness, completeness, failures, drift, cost, and consumer impact are measurable.
8. **Reproducible** — processing and outputs can be explained and recreated where required.
9. **Evolution-safe** — schema, semantic, and contract changes protect consumers.
10. **Automated** — repeatable validation, policy, deployment, and recovery are encoded.
11. **Cost-aware** — value, volume, latency, retention, and computation are balanced.
12. **Lifecycle-governed** — unused data, access, products, and pipelines are retired.

## 6. Data Product Mindset

Every material data product shall define:

- Purpose and intended decisions or workflows.
- Product owner, technical owner, data steward, and support.
- Producers, authoritative sources, and consumers.
- Contract, schema, semantics, keys, units, time, and null behaviour.
- Quality dimensions, thresholds, and service expectations.
- Classification, permitted use, access, retention, and disposal.
- Metadata, lineage, dependencies, and discoverability.
- Versioning, compatibility, change, and deprecation policy.
- Cost, capacity, operational health, and lifecycle state.

Publishing a table without these elements creates a data output, not a mature data product.

## 7. When to Use This Playbook

Use this playbook when:

- Creating or changing a shared dataset or event stream.
- Building batch, streaming, CDC, replication, or transformation pipelines.
- Creating analytical, reporting, ML, or AI data products.
- Onboarding a new source or third-party provider.
- Changing schema, semantics, keys, partitions, or timeliness.
- Migrating a data store, platform, model, or integration.
- Addressing data-quality, lineage, privacy, access, or retention risk.
- Backfilling, replaying, correcting, or deleting material data.
- Deprecating or retiring a data product or source.

Routine internal implementation changes may use a lighter profile when contracts, quality, security, and consumer outcomes remain unchanged.

## 8. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| Data Product Owner | Owns consumer outcomes, scope, priority, service expectations, adoption, and lifecycle |
| Data Engineer | Designs, builds, tests, operates, documents, and improves pipelines and products |
| Data Architect | Defines boundaries, models, integration patterns, platform fit, and evolution strategy |
| Data Steward | Owns meaning, classification, quality expectations, permitted use, and governance coordination |
| Source Owner | Owns source semantics, availability, change communication, and source-quality evidence |
| Consumer Representative | Defines use, acceptance criteria, compatibility needs, and validates fitness |
| Platform Engineer | Provides governed compute, storage, orchestration, catalogue, observability, and self-service |
| Security Engineer | Reviews classification, access, protection, threat, audit, and incident requirements |
| Privacy or Legal Representative | Defines applicable purpose, minimisation, rights, retention, and disclosure obligations |
| Reliability or Operations Engineer | Owns service health, capacity, incident, continuity, recovery, and operational readiness |
| Quality Engineer | Designs independent quality, reconciliation, contract, and failure-path verification |
| Risk Owner | Accepts or escalates residual risk within delegated authority |
| Approver | Authorises lifecycle progression when evidence and residual risk are acceptable |

Small teams may combine roles, but responsibilities remain explicit.

## 9. Inputs

Data work may consume:

- Business, operational, analytical, ML, AI, and regulatory needs.
- Consumer journeys, queries, decisions, and service expectations.
- Source-system contracts, owners, schemas, events, APIs, and change history.
- Data classification, privacy, security, residency, retention, and deletion requirements.
- Architecture, technical design, infrastructure, and platform capabilities.
- Existing models, definitions, catalogues, lineage, and quality evidence.
- Volume, velocity, variety, latency, availability, and growth forecasts.
- Incidents, data defects, support cases, usage, cost, and performance evidence.
- Supplier contracts, licences, permitted use, and lifecycle information.

Assumptions about semantics or ownership must be validated.

## 10. Entry Criteria

Before material implementation:

- A named consumer need and outcome are defined.
- Product, source, technical, and stewardship ownership are assigned.
- Authoritative sources and source limitations are known.
- Data classification and permitted use are defined.
- Expected semantics, grain, keys, time, and quality are understood.
- Volume, latency, availability, retention, and recovery needs are known.
- Consumers and compatibility requirements are identified.
- Architecture, security, privacy, cost, and governance constraints are available.
- Acceptance, approval, and residual-risk authorities are named.
- Traceability to initiating requirements, change, incident, or product need exists.

Missing critical ownership, classification, or purpose blocks production publication.

## 11. Data Engineering Workflow

```text
Identify Consumer Need
          │
          ▼
Discover Sources and Context
          │
          ▼
Define Data Product and Contract
          │
          ▼
Design Architecture and Model
          │
          ▼
Build Integration and Processing
          │
          ▼
Verify Quality, Security, and Recovery
          │
          ▼
Publish and Enable Consumers
          │
          ▼
Operate, Observe, and Support
          │
          ▼
Evolve, Improve, or Retire
```

Evidence may return work to an earlier phase.

## 12. Data Lifecycle

| State | Meaning | Required Evidence |
|---|---|---|
| Proposed | Need, consumers, sources, value, and ownership are being validated | Data Product Canvas |
| Designed | Contract, architecture, model, governance, and verification are approved | Design and Contract |
| Pilot | Limited consumers validate usefulness and operation | Pilot evidence |
| Published | Product is discoverable, supported, governed, and consumable | Catalogue and release evidence |
| Operated | Quality, freshness, usage, cost, incidents, and changes are managed | Health and support evidence |
| Deprecated | New adoption stops and migration is active | Deprecation and consumer plan |
| Retired | Processing, access, data, metadata, and dependencies are safely removed | Retirement evidence |

Lifecycle state must be visible to consumers.

## 13. Detailed Phase Activities

### Phase 1: Identify Data Need

**Goal:** validate the consumer problem and expected value.

Activities:

- Identify consumers, decisions, workflows, and current alternatives.
- Define expected business or operational outcome.
- Establish product, source, stewardship, and technical ownership.
- Quantify current quality, delay, manual effort, risk, and cost.
- Identify existing products and avoid duplicate data.
- Define non-goals and success measures.

Outputs:

- Data Need Statement.
- Consumer and Outcome Map.
- Baseline Evidence.

### Phase 2: Discover Sources and Context

**Goal:** understand source meaning, authority, constraints, and risk.

Activities:

- Inventory source systems, owners, interfaces, schemas, and histories.
- Define authoritative source and reconciliation rules.
- Profile semantics, grain, keys, time, nulls, duplicates, distributions, and drift.
- Classify data and permitted use.
- Assess reliability, latency, volume, change, retention, residency, and supplier terms.
- Map initial flow and dependencies.

Outputs:

- Source Assessment.
- Data Classification.
- Initial Lineage.

### Phase 3: Define Data Product and Contract

**Goal:** establish a consumer-facing agreement.

Activities:

- Define purpose, consumers, interface, semantics, grain, fields, keys, units, and time.
- Define quality, freshness, availability, and support expectations.
- Define access, privacy, retention, deletion, and permitted use.
- Define versioning, compatibility, notification, and deprecation.
- Define producer and consumer responsibilities.
- Review the contract with representative producers and consumers.

Outputs:

- Data Product Specification.
- Versioned Data Contract.
- Acceptance Criteria.

### Phase 4: Design Architecture and Model

**Goal:** create an implementation-ready, operable design.

Activities:

- Select batch, streaming, CDC, API, event, or hybrid integration based on need.
- Design logical, physical, event, and semantic models where applicable.
- Define ingestion, transformation, storage, serving, orchestration, and isolation.
- Define idempotency, ordering, late data, replay, backfill, correction, and deletion.
- Define quality controls, metadata, lineage, observability, capacity, cost, continuity, and recovery.
- Review security, privacy, architecture, and lifecycle decisions.

Outputs:

- Data Architecture and Technical Design.
- Data Model.
- Pipeline and Recovery Design.

### Phase 5: Build Pipelines and Product

**Goal:** implement reproducible and testable data processing.

Activities:

- Implement source ingestion and contract validation.
- Implement transformations with explicit semantics.
- Preserve source and processing metadata required for traceability.
- Add schema, quality, reconciliation, security, privacy, and performance tests.
- Implement idempotency, deduplication, checkpoints, retry, quarantine, replay, and cleanup.
- Version code, configuration, contracts, schemas, and infrastructure.

Outputs:

- Data Pipeline and Product.
- Automated Verification.
- Review Package.

### Phase 6: Verify Quality and Readiness

**Goal:** prove fitness for intended use and safe operation.

Activities:

- Verify contract, schema, semantics, grain, keys, and transformations.
- Test completeness, accuracy, validity, consistency, uniqueness, integrity, and timeliness as applicable.
- Reconcile source, intermediate, and published totals.
- Test access, masking, deletion, audit, and prohibited-use controls.
- Test failure, duplicate, late, out-of-order, backfill, replay, rollback, and recovery paths.
- Validate scale, performance, cost, monitoring, support, and residual risk.

Outputs:

- Data Verification Report.
- Quality Baseline.
- Release Readiness Recommendation.

### Phase 7: Publish and Enable Consumers

**Goal:** release a discoverable, governed, supported data product.

Activities:

- Deploy through approved change and release governance.
- Register product, owner, contract, schema, meaning, lineage, quality, and lifecycle in the catalogue.
- Configure least-privilege access and audit.
- Publish documentation, examples, support, service expectations, and known limitations.
- Notify consumers of availability, version, and change policy.
- Validate initial consumer use and operational handover.

Outputs:

- Published Data Product.
- Catalogue and Documentation.
- Consumer and Operational Handover.

### Phase 8: Operate and Support

**Goal:** meet published expectations and protect consumers.

Activities:

- Monitor pipeline health, quality, freshness, volume, drift, usage, cost, and dependencies.
- Route failures and quality breaches by consumer impact.
- Follow Incident Management for material data-product harm.
- Repair, replay, backfill, reconcile, and communicate through governed procedures.
- Review access, retention, deletion, suppliers, capacity, and supported versions.
- Maintain runbooks, ownership, metadata, lineage, and health dashboards.

Outputs:

- Data Health Evidence.
- Incident and Support Records.
- Access, Cost, and Lifecycle Reviews.

### Phase 9: Evolve, Improve, or Retire

**Goal:** preserve value and compatibility throughout change.

Activities:

- Analyse consumer feedback, adoption, quality, cost, incidents, and bypasses.
- Evolve contracts and schemas compatibly where possible.
- Pilot and communicate breaking versions with migration support.
- Remove duplicate, unused, unsupported, or unjustified products and data.
- Execute retention, deletion, deprecation, migration, and retirement.
- Feed learning into platform, security, standards, and future products.

Outputs:

- Improvement Roadmap.
- Version or Migration Plan.
- Deprecation or Retirement Evidence.

## 14. Data Architecture

Data architecture shall define:

- Bounded domains, ownership, authoritative sources, and consumer interfaces.
- Operational and analytical separation where required.
- Batch, stream, event, CDC, API, and external integration.
- Storage, processing, serving, orchestration, and catalogue boundaries.
- Data movement, residency, classification, isolation, and protection.
- Scale, latency, consistency, availability, durability, and recovery.
- Metadata, lineage, quality, observability, and cost.
- Evolution, migration, interoperability, and exit strategy.

Select architecture from outcomes and constraints, not platform fashion.

## 15. Data Modelling

Models shall make meaning explicit:

- Business concepts and ownership.
- Grain and level of detail.
- Identifiers, keys, relationships, constraints, and cardinality.
- Attributes, data types, domains, units, precision, and null semantics.
- Event time, processing time, effective time, and timezone.
- History, slowly changing behaviour, correction, and deletion.
- Logical, physical, event, and semantic views.
- Versioning and compatibility rules.

A technically valid schema can still be semantically unsafe.

## 16. Data Integration

Choose integration using:

| Concern | Questions |
|---|---|
| Latency | When must consumers see change? |
| Volume | What throughput and growth are expected? |
| Ordering | Does event order affect meaning? |
| Delivery | At-most-once, at-least-once, or effectively-once behaviour? |
| Change | How do schemas and source semantics evolve? |
| Recovery | Can data be replayed, backfilled, reconciled, and corrected? |
| Coupling | What producer and consumer dependencies are introduced? |
| Security | What crosses boundaries and how is it protected? |
| Cost | What is the lifecycle cost of the selected latency and scale? |

Every integration defines checkpoints, retry, idempotency, duplicates, late data, poison records, quarantine, replay, and ownership.

## 17. Data Quality Management

Quality dimensions are selected by consumer need:

| Dimension | Meaning |
|---|---|
| Accuracy | Values represent the intended real-world or source state |
| Completeness | Required records and attributes are present |
| Consistency | Equivalent concepts agree across rules or systems |
| Timeliness | Data arrives within useful time |
| Freshness | Data reflects a sufficiently recent state |
| Validity | Values satisfy schema and domain rules |
| Uniqueness | Records expected to be distinct are not duplicated |
| Integrity | Keys, relationships, totals, and constraints hold |
| Availability | Consumers can access the product when promised |

Each quality rule has a purpose, scope, threshold, measurement window, owner, action, and exception path.

## 18. Metadata and Lineage

Required metadata may include:

- Business name, description, terms, purpose, owner, steward, and consumers.
- Technical identity, schema, fields, types, partitions, format, location, and interface.
- Classification, permitted use, access, retention, deletion, and residency.
- Quality, freshness, availability, usage, cost, and lifecycle state.
- Source, transformation, intermediate, output, and consumer lineage.
- Contract, schema, pipeline, code, and deployment versions.

Lineage must support impact analysis, incident investigation, compliance, change, and retirement. Automatically discovered lineage requires owner validation for critical products.

## 19. Data Governance

Data governance defines decision rights and evidence for:

- Ownership, stewardship, and authoritative sources.
- Shared definitions and semantic change.
- Classification, purpose, permitted use, access, and sharing.
- Quality expectations and breach handling.
- Retention, legal hold, deletion, and disposal.
- Catalogue, metadata, lineage, and discoverability.
- Contract, schema, compatibility, and deprecation.
- Risk, exceptions, audit, and approval.

Governance should appear in workflows and interfaces, not rely only on periodic review.

## 20. Data Security and Privacy

Data Engineering shall:

- Minimise collection, movement, duplication, retention, and exposure.
- Classify data before production use.
- Restrict access by identity, purpose, environment, and least privilege.
- Protect data in transit, at rest, in backups, and in temporary processing.
- Apply masking, tokenisation, aggregation, or de-identification where required.
- Separate production, development, test, and analytical access.
- Protect credentials, keys, connection data, logs, and metadata.
- Audit sensitive access, export, change, and deletion.
- Support consent, rights, retention, deletion, residency, and disclosure requirements.
- Verify secure disposal from primary, replica, cache, backup, and derived products where applicable.

Security and privacy controls must follow [`PB-SECURITY-ENGINEERING`](PB-SECURITY-ENGINEERING.md).

## 21. Data Platform Operations

Operate data platforms and products through:

- Pipeline, job, stream, storage, catalogue, and serving health.
- Quality, freshness, volume, schema, distribution, and lineage monitoring.
- Capacity, performance, quota, cost allocation, and optimisation.
- Access, secret, dependency, patch, version, and configuration lifecycle.
- Backup, restore, replay, backfill, reconciliation, and disaster recovery.
- Incident, change, deployment, and maintenance governance.
- Service expectations, support, communication, and ownership.

Operational readiness includes consumer-impact visibility, not only pipeline execution status.

## 22. AI-Assisted Data Engineering

AI may assist with:

- Schema, model, contract, transformation, and test drafts.
- Data profiling and quality-rule suggestions.
- Metadata description and lineage discovery.
- Query, pipeline, and cost analysis.
- Documentation and impact analysis.
- Anomaly, drift, and incident investigation.

All AI-assisted work follows [`PB-AI-ENGINEERING`](PB-AI-ENGINEERING.md).

Engineers must:

- Protect classified, personal, confidential, and proprietary data.
- Use approved tools and permitted contexts.
- Validate generated semantics, queries, transformations, access, and tests.
- Verify results against source and consumer expectations.
- Retain human authority for data use, access, deletion, release, and risk.

Synthetic or AI-generated data must be labelled, validated, and governed.

## 23. Risk Management

| Risk | Consequence | Treatment |
|---|---|---|
| Incorrect semantics | Consumers make invalid decisions | Contracts, stewardship, examples, review |
| Poor quality | Reporting, operations, ML, or AI fails | Rules, reconciliation, monitoring, incident path |
| Schema drift | Pipelines or consumers break | Contract checks, compatibility, versioning |
| Missing lineage | Impact and root cause are unknown | Automated capture plus owner validation |
| Unauthorised access | Privacy, customer, or business harm | Least privilege, audit, review, protection |
| Excess retention | Cost and privacy exposure grow | Purpose-bound retention and verified deletion |
| Duplicate products | Conflicting truth and wasted cost | Catalogue, authoritative ownership, retirement |
| Pipeline failure | Stale or missing outcomes | Recovery, replay, backfill, service expectations |
| Silent partial failure | Wrong data appears healthy | Reconciliation and consumer-impact monitoring |
| Vendor lock-in | Cost or migration becomes prohibitive | Portable contracts, export, exit plan |
| Uncontrolled backfill | Overwrite, duplication, or downstream harm | Plan, isolation, preview, validation, rollback |
| Source change | Meaning changes without notice | Producer contract, monitoring, communication |

Residual risk requires owner, treatment, approval, monitoring, and expiry where applicable.

## 24. Deliverables

| Deliverable | Purpose |
|---|---|
| Data Need Statement | Defines consumers, outcome, baseline, and ownership |
| Data Product Specification | Defines purpose, scope, interface, semantics, and service |
| Data Contract | Defines producer-consumer technical and semantic agreement |
| Data Architecture and Model | Defines boundaries, flows, processing, storage, and meaning |
| Pipeline and Recovery Design | Defines orchestration, failure, replay, backfill, and reconciliation |
| Data Quality Plan | Defines dimensions, rules, thresholds, and action |
| Metadata and Lineage | Supports discovery, impact, traceability, and lifecycle |
| Security and Privacy Assessment | Defines classification, use, access, protection, and retention |
| Verification Report | Demonstrates contract, quality, control, scale, and recovery readiness |
| Operational Runbook | Defines monitoring, support, failure, recovery, and communication |
| Lifecycle Record | Governs version, deprecation, migration, retention, and retirement |

## 25. Quality Gates

### Gate 1: Data Product Opportunity Ready

- Consumers, use, outcome, baseline, and owner are defined.
- Existing products and authoritative sources are assessed.
- Classification, purpose, and governance constraints are known.
- Success and stop criteria are measurable.

### Gate 2: Contract and Design Ready

- Product, contract, semantics, grain, keys, time, quality, and service expectations are reviewed.
- Architecture covers integration, processing, storage, serving, recovery, scale, and cost.
- Security, privacy, retention, metadata, lineage, and lifecycle are designed.
- Producer, consumer, steward, technical, and approval responsibilities are clear.

### Gate 3: Verification Ready

- Implementation and configuration are reviewed.
- Contract, schema, quality, reconciliation, security, and privacy tests exist.
- Failure, duplicate, late, replay, backfill, rollback, deletion, and recovery paths are testable.
- Monitoring, support, documentation, and catalogue content are prepared.

### Gate 4: Publication Ready

- Verification demonstrates fitness for intended use.
- Unacceptable quality, security, privacy, and operational risk blocks publication.
- Access, metadata, lineage, quality, monitoring, runbook, and support are active.
- Residual risk, release authority, consumer notification, and rollback are recorded.

### Gate 5: Lifecycle Review

- Usage, quality, freshness, reliability, cost, access, incidents, and exceptions are reviewed.
- Contracts, sources, lineage, metadata, retention, and consumers remain current.
- Improvement, version, migration, deprecation, or retirement is decided.
- Owners, actions, dates, evidence, and next review are recorded.

## 26. Common Mistakes

- Building pipelines before validating consumer need.
- Treating every output as a new source of truth.
- Leaving semantics and null behaviour undocumented.
- Measuring only job success instead of data correctness.
- Testing transformations without source-to-output reconciliation.
- Assuming exactly-once processing without end-to-end evidence.
- Hiding schema change from consumers.
- Copying sensitive production data into lower environments.
- Collecting data without purpose, owner, retention, or disposal.
- Creating metadata that no operating workflow keeps current.
- Treating automatic lineage as unquestionably correct.
- Backfilling production without impact, isolation, validation, and recovery.
- Optimising latency or scale without outcome or cost justification.
- Retaining unused products because retirement is inconvenient.

## 27. Best Practices

- Begin with the consumer decision or workflow.
- Define authoritative ownership and meaning early.
- Make contracts executable where practical.
- Preserve raw evidence only when purpose, protection, and retention justify it.
- Design idempotency, replay, correction, and deletion before failure.
- Test quality at source, transformation, and product boundaries.
- Reconcile counts, totals, keys, and critical invariants.
- Publish quality and freshness with the product.
- Use catalogue and lineage in change and incident workflows.
- Prefer compatible evolution and time-bound migration.
- Measure end-to-end consumer impact and unit cost.
- Retire duplicate, unused, unsupported, and unjustified data.

## 28. Templates

### Data Product Specification

```text
Name, ID, version, and lifecycle:
Purpose and outcome:
Owner, steward, technical owner, and support:
Producers, authoritative sources, and consumers:
Interface, grain, keys, schema, units, and time:
Quality, freshness, availability, and performance:
Classification, permitted use, access, retention, and deletion:
Metadata, lineage, dependencies, and catalogue:
Versioning, compatibility, change, and deprecation:
Operations, cost, continuity, and recovery:
Acceptance, residual risk, approval, and review:
```

### Data Contract

```text
Producer and owner:
Consumers and intended use:
Interface and delivery:
Schema and semantics:
Keys, ordering, time, nulls, and duplicates:
Quality and service expectations:
Security, privacy, use, retention, and audit:
Version and compatibility:
Change notification and deprecation:
Failure, replay, reconciliation, and support:
```

### Data Quality Rule

```text
Product and field:
Consumer purpose:
Dimension:
Rule and scope:
Threshold and window:
Measurement source:
Severity and consumer impact:
Owner and action:
Exception and expiry:
Evidence and review:
```

## 29. Examples

### Example: Customer Order Data Product

**Need:** finance, operations, and product teams calculate order state differently.

The data product:

1. Names the operational order service as authoritative for state transitions.
2. Defines order grain, identifiers, currency units, event and effective time, cancellation, and refund semantics.
3. Publishes a versioned contract and source-to-product lineage.
4. Reconciles record counts and financial totals.
5. Defines freshness, completeness, availability, retention, access, and support.
6. Monitors late events, duplicates, state violations, and consumer impact.

The product is not published until finance and operational consumers validate semantics.

### Example: Breaking Schema Change

A producer replaces a nullable field with a required nested structure.

The governed path:

1. Identify consumers through catalogue and lineage.
2. Publish a new contract version.
3. Run both versions during a migration window.
4. Provide consumer test data and compatibility evidence.
5. Track migration and exceptions.
6. Deprecate and remove the old version only after exit criteria pass.

### Example: Historical Backfill

A corrected rule requires twelve months of recomputation.

The plan defines isolated execution, source snapshot, idempotent keys, cost and capacity, preview, reconciliation, downstream notification, rollback or correction, audit evidence, and post-backfill monitoring.

## 30. Related Principles

- [Engineering Principles](../01-principles/01-engineering-principles.md)
- [AI Engineering Principles](../01-principles/02-ai-engineering-principles.md)
- [Architecture Principles](../01-principles/03-architecture-principles.md)
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

Data, data-modelling, data-quality, data-security, data-contract, and retention implementation standards are planned and non-authoritative.

## 32. Related References

- [Engineering Identifier Reference](../04-reference/REF-IDENTIFIERS.md)
- [Engineering Terminology Reference](../04-reference/REF-TERMINOLOGY.md)
- [Engineering Acronym Reference](../04-reference/REF-ACRONYMS.md)

Data-product, catalogue, lineage, quality, contract, modelling, and lifecycle references are planned and non-authoritative.

## 33. Related Playbooks

- [Requirements Playbook](PB-REQ.md) governs data requirements.
- [Architecture Playbook](PB-ARCH.md) and [Technical Design Playbook](PB-TECH-DESIGN.md) govern data architecture and implementation-ready design.
- [AI Engineering Playbook](PB-AI-ENGINEERING.md) governs AI-assisted data work.
- [Coding Playbook](PB-CODING.md), [Code Review Playbook](PB-CODE-REVIEW.md), and [Testing Playbook](PB-TESTING.md) govern implementation and verification.
- [Deployment Playbook](PB-DEPLOYMENT.md) governs data release and promotion.
- [Observability Playbook](PB-OBSERVABILITY.md) governs operational data evidence.
- [Incident Management Playbook](PB-INCIDENT-MANAGEMENT.md) governs material data incidents.
- [Change Management Playbook](PB-CHANGE-MANAGEMENT.md) governs production data change.
- [Maintenance Playbook](PB-MAINTENANCE.md) governs data sustainment and retirement.
- [Platform Engineering Playbook](PB-PLATFORM-ENGINEERING.md) supplies governed data-platform capabilities.
- [Security Engineering Playbook](PB-SECURITY-ENGINEERING.md) governs data security and privacy engineering controls.

## 34. Metrics

| Dimension | Example Metrics | Guardrail |
|---|---|---|
| Adoption | Eligible, active, retained consumers and use cases | Usage without value is not success |
| Quality | Rule pass, breach, recurrence, and consumer impact | Average scores can hide critical failure |
| Freshness | Age, lateness, and missed expectation | Different consumers need different windows |
| Reliability | Pipeline success, availability, recovery, replay | A successful job may publish wrong data |
| Contract | Compatibility, schema drift, breaking change | Count governed exceptions |
| Metadata | Ownership, meaning, classification, and catalogue completeness | Completeness does not prove accuracy |
| Lineage | Source-to-consumer coverage and validation | Automatic discovery needs review |
| Security | Access, sensitive-use, retention, and deletion conformance | Do not expose sensitive detail in metrics |
| Operations | Incident, time to detect, time to restore, recurrence | Segment data correction from service restoration |
| Cost | Unit cost by product, consumer, volume, or freshness | Avoid shifting cost to consumers |
| Lifecycle | Supported versions, deprecated consumers, retirement completion | Exceptions require expiry |

Metrics evaluate products and systems, not individual engineer productivity.

## 35. Reference Implementation and Enterprise Appendices

### 35.1 Data Product Canvas

| Area | Questions |
|---|---|
| Consumers | Who uses the data, for which decisions or workflows? |
| Outcome | What improves and how is it measured? |
| Sources | Which sources are authoritative and what are their limits? |
| Product | What interface, grain, meaning, and service are provided? |
| Quality | Which dimensions and thresholds make it fit for use? |
| Governance | Who owns meaning, access, use, retention, and change? |
| Operations | How is it observed, supported, recovered, and funded? |
| Lifecycle | How does it version, migrate, deprecate, and retire? |

### 35.2 Data Contract Template

| Field | Required Content |
|---|---|
| Identity | Product, producer, owner, version |
| Consumers | Intended uses and responsibilities |
| Delivery | Interface, schedule, latency, ordering |
| Semantics | Grain, keys, fields, units, time, nulls |
| Quality | Rules, thresholds, service expectations |
| Governance | Classification, access, purpose, retention |
| Evolution | Compatibility, notification, deprecation |
| Operations | Failure, replay, reconciliation, support |

### 35.3 Data Quality Checklist

- [ ] Quality rules map to consumer use.
- [ ] Grain, keys, nulls, duplicates, time, and units are verified.
- [ ] Source-to-output completeness and critical totals reconcile.
- [ ] Freshness and availability match published expectations.
- [ ] Drift, anomalies, and rule breaches have owners and actions.
- [ ] Correction, replay, exception, and closure evidence exist.

### 35.4 Metadata Template

| Category | Required Metadata |
|---|---|
| Business | Purpose, description, terms, owner, consumers |
| Technical | Interface, schema, fields, partitions, versions |
| Governance | Classification, purpose, access, retention, deletion |
| Quality | Rules, freshness, availability, status |
| Operations | Dependencies, support, service, cost, lifecycle |
| Traceability | Sources, transformations, outputs, consumers |

### 35.5 Data Lineage Template

| Node or Flow | Owner | Input | Transformation | Output | Version | Classification | Quality | Consumer | Evidence |
|---|---|---|---|---|---|---|---|---|---|

### 35.6 Pipeline Readiness Checklist

- [ ] Source, contract, ownership, and change communication are confirmed.
- [ ] Idempotency, checkpoints, ordering, retry, duplicate, and late data are designed.
- [ ] Quarantine, replay, backfill, correction, deletion, and cleanup work.
- [ ] Quality, reconciliation, schema, security, and privacy checks pass.
- [ ] Capacity, performance, cost, monitoring, support, and recovery are ready.
- [ ] Deployment, rollback, consumer notification, and approval are recorded.

### 35.7 Data Governance Matrix

| Decision | Product Owner | Source Owner | Steward | Engineer | Security/Privacy | Consumer | Approver |
|---|---|---|---|---|---|---|---|
| Meaning | A | C | R | C | C | C | I |
| Contract | A | C | R | R | C | C | I |
| Access and use | C | I | R | C | R | I | A |
| Quality | A | C | R | R | I | C | I |
| Breaking change | A | C | R | R | C | C | A |
| Retention and deletion | C | I | R | R | R | I | A |
| Retirement | A | C | R | R | C | C | A |

Adapt authority to organisational policy.

### 35.8 Data Engineering Maturity Model

| Level | Characteristics |
|---|---|
| 1 — Reactive | Unowned pipelines, manual correction, unclear meaning |
| 2 — Repeatable | Basic ownership, documented jobs, recurring checks |
| 3 — Productised | Contracts, catalogue, quality, support, consumer focus |
| 4 — Managed | Automated governance, lineage, service, cost, lifecycle |
| 5 — Adaptive | Evidence-led evolution, self-service, routine consolidation and retirement |

Assess maturity per product or capability.

### 35.9 Data Health Dashboard

| Dimension | Indicator | Target | Current | Trend | Consumer Impact | Owner | Action |
|---|---|---:|---:|---|---|---|---|
| Quality | | | | | | | |
| Freshness | | | | | | | |
| Availability | | | | | | | |
| Volume and drift | | | | | | | |
| Usage | | | | | | | |
| Security and privacy | | | | | | | |
| Cost | | | | | | | |
| Lifecycle | | | | | | | |

### 35.10 Deliverables Checklist

- [ ] Data Need Statement and Product Specification.
- [ ] Contract, architecture, model, pipeline, and recovery design.
- [ ] Quality, security, privacy, metadata, lineage, and lifecycle plan.
- [ ] Implementation, review, test, and reconciliation evidence.
- [ ] Catalogue, documentation, access, monitoring, runbook, and support.
- [ ] Release, residual risk, approval, consumer handover, and next review.

### 35.11 Data Lifecycle Checklist

- [ ] Owner, consumers, purpose, state, version, and support are current.
- [ ] Sources, contracts, semantics, lineage, and quality remain valid.
- [ ] Access, use, retention, deletion, residency, and suppliers are reviewed.
- [ ] Usage, cost, incidents, defects, versions, and exceptions are reviewed.
- [ ] Improvement, migration, deprecation, or retirement is decided.
- [ ] Data, processing, access, metadata, and dependencies are removed at retirement.

### 35.12 Data Product Review Template

```text
Product, version, owner, and lifecycle:
Consumers, uses, value, and adoption:
Sources, contract, semantics, and lineage:
Quality, freshness, availability, and incidents:
Security, privacy, access, retention, and deletion:
Performance, capacity, reliability, and cost:
Compatibility, changes, exceptions, and risks:
Decision: invest / maintain / migrate / deprecate / retire
Actions, owners, dates, approval, and next review:
```

## 36. Revision History

| Version | Date | Author | Status | Summary |
|---|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Draft | Initial Data Engineering Playbook with nine-phase data-product workflow, architecture, modelling, integration, quality, lineage, governance, privacy, platform operations, five quality gates, metrics, and twelve enterprise appendices |

## 37. Summary

`PB-DATA-ENGINEERING` governs data as an owned engineering product.

It requires teams to:

- Start with named consumers and outcomes.
- Define authoritative sources, contracts, semantics, and quality.
- Build reliable, observable, secure, privacy-aware data processing.
- Publish discoverable metadata, lineage, ownership, and support.
- Evolve schemas and products without unmanaged consumer harm.
- Improve, deprecate, and retire data deliberately.

This Draft establishes Data Engineering as the third Enterprise Engineering Capability. Formal review and approval remain required before it is Stable.
