---
title: Engineering Metadata Standard
id: STD-METADATA
version: 1.0.0
status: Draft
owner: Invara Labs
classification: Engineering Standard
review_cycle: Quarterly
created: 2026-07-30
last_updated: 2026-07-30
approved_by: TBD
authors:
  - Invara Labs Engineering
tags:
  - metadata
  - documentation
  - governance
  - standards
related:
  - DOC-STYLE
  - TERM-STANDARD
  - STD-REVIEW
  - STD-TRACEABILITY
supersedes: null
superseded_by: null
---

# Engineering Metadata Standard

> **Defines the mandatory metadata model for engineering artefacts to improve consistency, discoverability, governance, traceability, and automation.**

## 1. Overview

Metadata provides structured information about an engineering artefact.

It enables people and tools to understand a document's identity, ownership, lifecycle, purpose, and relationships without first interpreting the entire document.

This standard establishes a common metadata model for engineering documentation governed by ILOS.

## 2. Purpose

This standard:

- Standardises document metadata.
- Improves discovery.
- Supports governance and traceability.
- Enables proportionate automation.
- Supports AI-assisted engineering.
- Improves repository consistency.
- Simplifies maintenance.

## 3. Objectives

- Define mandatory and optional metadata fields.
- Establish valid formats and controlled values.
- Promote consistency across engineering artefacts.
- Enable validation and indexing.
- Improve documentation quality.
- Support relationships defined by `STD-TRACEABILITY`.

## 4. Scope

This standard applies to substantive governed engineering artefacts, including:

- Principles
- Playbooks
- Standards
- References
- Examples
- Templates
- ILOS control documents
- Engineering governance documents

Repository entry-point files may use tailored metadata when their existing format has a clear purpose. Existing documents shall be migrated when substantively revised or through an approved migration plan; this Draft does not make every legacy document immediately non-compliant.

## 5. Metadata Principles

Metadata shall be:

- **Accurate** — It reflects the current artefact.
- **Consistent** — Fields and values follow this standard.
- **Minimal** — Every field has a governance or discovery purpose.
- **Machine-readable** — Tools can parse it deterministically.
- **Human-readable** — Contributors can understand and maintain it.
- **Maintainable** — It changes with the artefact.
- **Extensible** — Document types may add governed fields.
- **Authoritative** — Metadata is not duplicated elsewhere as a competing source of truth.

## 6. Metadata Structure

Engineering documents shall store metadata as YAML front matter at the beginning of the file.

```yaml
---
title: Engineering Metadata Standard
id: STD-METADATA
version: 1.0.0
status: Draft
owner: Invara Labs
classification: Engineering Standard
review_cycle: Quarterly
created: 2026-07-30
last_updated: 2026-07-30
approved_by: TBD
authors:
  - Invara Labs Engineering
tags:
  - metadata
related:
  - STD-TRACEABILITY
supersedes: null
superseded_by: null
---
```

YAML keys use `snake_case`. Dates use ISO 8601 calendar format: `YYYY-MM-DD`.

## 7. Mandatory Fields

| Field | Description |
|---|---|
| `title` | Human-readable document title |
| `id` | Unique governed artefact identifier |
| `version` | Current semantic version |
| `status` | Current ILOS lifecycle status |
| `owner` | Accountable team or individual |
| `classification` | Document type or governance classification |
| `review_cycle` | Expected review frequency |
| `created` | Original creation date |
| `last_updated` | Date of the most recent meaningful revision |
| `authors` | One or more authors |
| `related` | Related governed artefact identifiers |

`related` may be an empty list only when no meaningful relationship exists. Reviewers shall verify that an empty value is intentional.

## 8. Optional Fields

| Field | Description |
|---|---|
| `approved_by` | Approver or approving body |
| `reviewers` | Review participants |
| `tags` | Controlled discovery terms |
| `aliases` | Approved alternative names |
| `supersedes` | Artefact replaced by this document |
| `superseded_by` | Artefact replacing this document |
| `repository` | Authoritative source repository |
| `language` | Document language |
| `audience` | Intended readers |
| `maturity` | Additional maturity signal where lifecycle status is insufficient |

Optional fields shall be used only when they provide meaningful value.

## 9. Field Definitions

### 9.1 `title`

A concise, descriptive title matching the document's primary heading where practical.

```yaml
title: Engineering Review Standard
```

### 9.2 `id`

A unique identifier following the approved identifier convention.

```yaml
id: STD-REVIEW
```

Until `REF-IDENTIFIERS` is approved, existing established prefixes shall be reused consistently rather than expanded ad hoc.

### 9.3 `version`

A valid Semantic Versioning value written as a string-compatible scalar.

```yaml
version: 1.2.0
```

### 9.4 `status`

One value from the approved [ILOS Lifecycle](../../../ilos/ILOS-LIFECYCLE.md):

- `Planned`
- `Draft`
- `Review`
- `Approved`
- `Deprecated`
- `Archived`

### 9.5 `owner`

The team or individual accountable for accuracy, review, and maintenance.

### 9.6 `classification`

The governed document type or control classification.

Common values include:

- `Principle`
- `Playbook`
- `Engineering Standard`
- `Reference`
- `Example`
- `Architecture`
- `Governance`
- `Roadmap`
- `Template`
- `Overview`

### 9.7 `review_cycle`

The expected review frequency.

Approved values:

- `Monthly`
- `Quarterly`
- `Biannual`
- `Annual`
- `Event-driven`

### 9.8 `created`

The original creation date. It shall not change during revision.

### 9.9 `last_updated`

The date of the most recent meaningful change. Purely automated formatting that does not change the artefact need not update this field.

### 9.10 `authors`

A YAML list containing at least one individual, team, or organisational author.

### 9.11 `related`

A YAML list of approved identifiers for meaningfully related artefacts.

Relationships shall follow [`STD-TRACEABILITY`](STD-TRACEABILITY.md). Filesystem paths belong in document content unless a future schema explicitly permits them in metadata.

## 10. Metadata Validation

Validation shall check:

- Required fields exist.
- YAML syntax is valid.
- Dates use valid ISO format.
- IDs are unique.
- Versions follow Semantic Versioning.
- Status, classification, and review-cycle values are allowed.
- List fields are represented as lists.
- Related identifiers resolve where a registry exists.
- Supersession does not create contradictory relationships.

Automated validation is encouraged after conventions and migration expectations are stable.

## 11. Metadata Governance

### Authors

- Create accurate metadata.
- Update it with meaningful revisions.
- Use established identifiers and controlled values.

### Reviewers

- Validate completeness and correctness.
- Confirm relationships and lifecycle state.
- Reject speculative or misleading metadata.

### Approvers

- Confirm that approved documents identify accountable ownership and valid metadata.

### Engineering Governance

- Maintains the schema and controlled values.
- Resolves identifier conflicts.
- Defines migration and validation policy.
- Reviews proposed extensions.

## 12. AI-Assisted Metadata

AI may assist with:

- Generating draft metadata.
- Detecting missing fields.
- Suggesting related documents.
- Validating formats.
- Recommending tags.
- Detecting inconsistencies and duplicate IDs.

Human review remains mandatory. AI shall not approve metadata or invent identifiers without validation.

## 13. Common Mistakes

- Missing or duplicate IDs.
- Invalid or inconsistent dates.
- Broken related identifiers.
- Incorrect classification.
- Unsupported lifecycle values.
- Scalar values where lists are required.
- Empty optional fields with no purpose.
- Updating content without updating metadata.
- Treating tags as uncontrolled synonyms.

## 14. Best Practices

Teams should:

- Keep metadata concise.
- Update it with every meaningful revision.
- Reuse established identifiers and controlled values.
- Maintain accurate relationships.
- Review metadata during every document review.
- Add fields only for a demonstrated use case.
- Automate validation when it reduces real maintenance effort.

## 15. Compliance and Adoption

Compliance may be verified through:

- Engineering reviews.
- YAML parsing.
- Automated schema validation.
- Documentation audits.
- Repository quality checks.

Adoption shall be incremental:

1. Apply the standard to new governed artefacts.
2. Correct metadata when existing documents receive substantive revisions.
3. Plan bulk migration only when automation or governance requires it.

Exceptions shall be documented through ILOS Governance.

## 16. Related Artefacts

### Standards

- `DOC-STYLE`
- `TERM-STANDARD`
- `STD-REVIEW`
- `STD-TRACEABILITY`
- `STD-VERSIONING` — Planned

### References

- `REF-IDENTIFIERS` — Planned
- `REF-TERMINOLOGY` — Planned
- `REF-METADATA` — Planned

## 17. External References

- YAML Specification
- Semantic Versioning 2.0.0
- ISO/IEC/IEEE 29148 — Requirements engineering
- ISO/IEC/IEEE 15288 — System life cycle processes

These references inform the standard; ILOS governance remains authoritative for Invara Labs.

## 18. Revision History

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Initial draft |

## 19. Summary

Metadata is the foundation of a governed Engineering Operating System.

By standardising how artefacts describe themselves, this standard enables discovery, automation, traceability, governance, and AI-assisted engineering while keeping the documentation ecosystem consistent and maintainable.
