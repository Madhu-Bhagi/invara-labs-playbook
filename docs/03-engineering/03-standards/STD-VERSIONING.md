---
title: Engineering Versioning Standard
id: STD-VERSIONING
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
  - versioning
  - governance
  - lifecycle
  - standards
related:
  - STD-METADATA
  - STD-TRACEABILITY
  - STD-REVIEW
  - DOC-STYLE
supersedes: null
superseded_by: null
---

# Engineering Versioning Standard

> **Defines the versioning model and governance for engineering artefacts managed within the Invara Labs Engineering Operating System (ILOS).**

## 1. Overview

Engineering artefacts evolve as products, technologies, evidence, and organisational practices change.

A consistent versioning strategy makes changes transparent, traceable, and governed throughout an artefact's lifecycle.

This standard defines how engineering documents communicate the significance and history of change.

## 2. Purpose

This standard:

- Standardises document versioning.
- Communicates the significance of changes.
- Preserves revision history.
- Supports governance and audits.
- Enables traceability across revisions.
- Simplifies collaboration.
- Supports reliable automation.

## 3. Scope

This standard applies to substantive governed engineering artefacts, including:

- Principles
- Playbooks
- Standards
- References
- Examples
- Templates
- ILOS control documents
- Engineering governance documents

Planned placeholders do not require independent versions until substantive drafting begins. Existing documents shall adopt this standard when substantively revised or through an approved migration plan.

## 4. Versioning Principles

Versioning shall be:

- **Predictable** — Similar changes produce similar increments.
- **Consistent** — All governed artefacts use the same format.
- **Transparent** — Readers can understand what changed.
- **Traceable** — Versions connect to revision history and related decisions.
- **Backward-aware** — Breaking changes are clearly signalled.
- **Proportionate** — Editorial maintenance does not create unnecessary major releases.

## 5. Version Format

ILOS adopts Semantic Versioning:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
2.4.1
```

Versions shall contain three non-negative integer components without prefixes such as `v` in metadata.

## 6. Version Components

### 6.1 Major

Increment `MAJOR` when:

- Guidance changes incompatibly.
- Existing requirements are removed or fundamentally redefined.
- Governance or structure is redesigned in a breaking way.
- Adopters must materially change how they comply or operate.

```text
1.4.2 → 2.0.0
```

Reset `MINOR` and `PATCH` to zero.

### 6.2 Minor

Increment `MINOR` when:

- A compatible section or capability is added.
- Guidance is meaningfully expanded.
- A new compatible requirement is introduced.
- An appendix or supported workflow is added.

```text
1.2.3 → 1.3.0
```

Reset `PATCH` to zero.

If a new requirement breaks existing compliant usage, it requires a Major increment rather than Minor.

### 6.3 Patch

Increment `PATCH` when:

- Grammar or spelling is corrected.
- Formatting is improved.
- Broken links are fixed.
- Meaning-preserving clarification is added.
- Metadata is corrected without changing document obligations.

```text
1.2.3 → 1.2.4
```

## 7. Lifecycle and Version

Lifecycle status and version communicate different facts:

- **Status** describes authority and maturity.
- **Version** describes the sequence and significance of changes.

The approved [ILOS Lifecycle](../../../ilos/ILOS-LIFECYCLE.md) is:

```text
Planned → Draft → Review → Approved → Deprecated → Archived
```

A status transition does not automatically require a version increment. Increment the version when content or obligations change. Record approval, deprecation, or archival in revision history even when the version remains unchanged.

## 8. Initial Versions

- A substantive first draft may begin at `0.1.0` or `1.0.0` according to the established document family convention.
- Approval does not require changing `1.0.0` solely because the document was previously Draft.
- New documents in an existing governed family shall follow that family's current convention.

Until a stricter pre-release convention is approved, contributors shall not introduce custom suffixes such as `-draft1`.

## 9. Revision History

Every substantive governed document shall maintain a concise revision history.

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0.0 | 2026-07-30 | Engineering | Initial release |
| 1.1.0 | 2026-08-12 | Engineering | Added governance guidance |
| 1.1.1 | 2026-08-15 | Engineering | Corrected metadata examples |

Revision history shall:

- Record meaningful revisions.
- Use the same version as metadata.
- Explain the outcome rather than listing mechanical edits.
- Identify approval or deprecation events where relevant.

Multiple editorial changes may be grouped into one Patch release.

## 10. Change Categories

| Change Type | Typical Increment |
|---|---|
| Editorial correction | Patch |
| Formatting or broken-link fix | Patch |
| Meaning-preserving clarification | Patch |
| Compatible new section | Minor |
| Compatible new requirement | Minor |
| Compatible new appendix | Minor |
| Incompatible requirement change | Major |
| Structural redesign | Major |
| Breaking governance change | Major |

The impact on users determines the increment, not the size of the diff.

## 11. Version Governance

### Document Owners

- Select the proposed increment.
- Update metadata and revision history together.
- Explain significant changes.
- Identify compatibility impact.

### Reviewers

- Verify that the increment matches the change.
- Confirm metadata and revision history agree.
- Check related and superseded artefacts.

### Approvers

- Confirm that breaking changes are explicitly communicated.
- Confirm that approved versions are ready to become authoritative.

### Engineering Governance

- Resolves ambiguous versioning decisions.
- Maintains shared conventions.
- Coordinates migrations caused by major changes.

## 12. Supersession and Deprecation

When one artefact replaces another:

- Set `supersedes` on the replacement.
- Set `superseded_by` on the replaced artefact.
- Update lifecycle status where appropriate.
- Link migration or compatibility guidance.
- Preserve the old artefact until archival is approved.

A replacement document starts its own version history unless it is explicitly a new version of the same artefact identity.

## 13. AI-Assisted Versioning

AI may assist with:

- Suggesting version increments.
- Generating revision summaries.
- Comparing revisions.
- Detecting undocumented changes.
- Identifying metadata/history mismatches.
- Highlighting possible breaking changes.

Human review and approval remain mandatory.

## 14. Best Practices

Teams should:

- Increment versions consistently.
- Keep revision history concise.
- Describe meaningful outcomes.
- Avoid unnecessary Major releases.
- Review version and compatibility before approval.
- Update related artefacts when a change affects them.
- Automate consistency checks after conventions stabilise.

## 15. Common Mistakes

- Changing content without updating version or history.
- Using inconsistent formats.
- Incrementing Major for minor edits.
- Treating every status transition as a content release.
- Omitting compatibility impact.
- Reusing an artefact ID for a different document.
- Skipping directly to arbitrary version numbers without history.
- Allowing metadata and revision history to disagree.

## 16. Compliance

Compliance may be verified through:

- Engineering reviews.
- Metadata validation.
- Revision-history checks.
- Repository audits.
- Automated comparison and policy checks.

Exceptions shall be documented through ILOS Governance.

## 17. Related Artefacts

### Standards

- `DOC-STYLE`
- `STD-METADATA`
- `STD-TRACEABILITY`
- `STD-REVIEW`

### References

- `REF-METADATA` — Planned
- `REF-IDENTIFIERS` — Planned

## 18. External References

- Semantic Versioning 2.0.0
- ISO/IEC/IEEE 29148 — Requirements engineering
- ISO/IEC/IEEE 15288 — System life cycle processes

These references inform the standard; ILOS governance remains authoritative for Invara Labs.

## 19. Revision History

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Initial draft replacing the planned versioning placeholder |

## 20. Summary

Consistent versioning enables engineering documentation to evolve in a controlled and transparent manner.

By combining Semantic Versioning, revision histories, lifecycle status, and governance, ILOS keeps engineering knowledge reliable, traceable, and maintainable throughout its evolution.
