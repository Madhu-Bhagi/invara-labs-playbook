---
title: Engineering Identifier Reference
id: REF-IDENTIFIERS
version: 1.0.1
status: Draft
owner: Invara Labs
classification: Engineering Reference
review_cycle: Quarterly
created: 2026-07-30
last_updated: 2026-07-30
approved_by: TBD
authors:
  - Invara Labs Engineering
tags:
  - identifiers
  - reference
  - naming
  - governance
related:
  - TERM-STANDARD
  - STD-METADATA
  - STD-TRACEABILITY
  - REF-TERMINOLOGY
supersedes: null
superseded_by: null
---

# Engineering Identifier Reference

> **Provides the authoritative catalogue of engineering artefact identifiers used throughout the Invara Labs Engineering Operating System (ILOS).**

## 1. Overview

Identifiers uniquely distinguish engineering artefacts within ILOS.

A consistent identifier system improves discovery, traceability, cross-referencing, repository organisation, automation, and AI-assisted engineering.

This reference catalogues identifier prefixes already established in the repository and those reserved for governed future use. It is a reference registry, not a replacement for a future naming standard.

## 2. Purpose

This reference:

- Provides one source of truth for engineering identifier prefixes.
- Records established and reserved identifier families.
- Supports cross-document traceability.
- Simplifies navigation and interpretation.
- Reduces ambiguity and accidental collisions.
- Enables future automated validation.

## 3. Scope

The registry covers identifiers used by:

- Principles and principle statements
- Playbooks
- Standards
- References
- Examples
- Templates
- Architecture Decision Records
- Requirements, RFCs, tests, risks, and operational artefacts when introduced

## 4. Identifier Model

The common form is:

```text
<PREFIX>-<TOKEN>
```

Examples:

```text
STD-REVIEW
PB-REQ
REF-IDENTIFIERS
ADR-008
EP-001
```

An identifier should be:

- Short
- Descriptive
- Stable
- Human-readable
- Unique within its governed namespace

## 5. Registry Status

| Status | Meaning |
|---|---|
| Established | Already used by authoritative repository content |
| Reserved | Approved for a defined future artefact family but not yet broadly used |
| Proposed | Under consideration and not available for general use |

## 6. Primary Artefact Prefixes

| Prefix | Artefact | Pattern | Example | Status |
|---|---|---|---|---|
| `PB` | Engineering Playbook | `PB-<NAME>` | `PB-REQ` | Established |
| `STD` | Engineering Standard | `STD-<NAME>` | `STD-TRACEABILITY` | Established |
| `REF` | Engineering Reference | `REF-<NAME>` | `REF-IDENTIFIERS` | Established |
| `EX` | Engineering Example | `EX-<NAME>` | `EX-TRACEABILITY` | Reserved |
| `ADR` | Architecture Decision Record | `ADR-<NNN>` | `ADR-008` | Established |

`PR` is not currently approved as the universal Principle prefix because the repository already uses specialised principle families.

## 7. Principle Identifier Families

Principle documents contain individually numbered principles using discipline-specific prefixes.

| Prefix | Principle Family | Example | Status |
|---|---|---|---|
| `EP` | Engineering Principles | `EP-001` | Established |
| `AP` | AI Engineering Principles | `AP-001` | Established |
| `AR` | Architecture Principles | `AR-001` | Established |
| `CP` | Coding Principles | `CP-001` | Established |
| `TP` | Testing Principles | `TP-001` | Established |
| `SP` | Security Principles | `SP-001` | Established |
| `OP` | Observability Principles | `OP-001` | Established |
| `PP` | Performance Principles | `PP-001` | Established |

New principle families require registry review to avoid collisions and ambiguous abbreviations.

## 8. Established Compatibility Identifiers

The following established IDs predate the canonical `STD-*` convention and remain valid:

| Identifier or Prefix | Artefact | Status |
|---|---|---|
| `DOC-STYLE` | Engineering Documentation Style Guide | Established |
| `TERM-STANDARD` | Engineering Terminology Standard | Established |
| `PB-AUTHORING` | Playbook Authoring Standard | Established |

These identifiers shall not be renamed solely for cosmetic consistency. New exceptions require an explicit compatibility reason.

## 9. Reserved Lifecycle Prefixes

These prefixes may be introduced only when the corresponding artefact type and governance are established.

| Prefix | Reserved Artefact |
|---|---|
| `RFC` | Request for Comments |
| `REQ` | Requirement |
| `NFR` | Non-functional requirement |
| `US` | User story |
| `EPIC` | Epic |
| `TASK` | Engineering task |
| `BUG` | Defect |
| `TC` | Test case |
| `TR` | Test report |
| `RISK` | Risk record |
| `DEC` | Engineering decision outside the ADR system |
| `API` | API specification |
| `DB` | Database design |
| `UI` | User-interface specification |

Reservation does not require every project to create these artefacts.

## 10. Reserved Domain Prefixes

| Prefix | Reserved Domain |
|---|---|
| `SEC` | Security |
| `DEV` | Developer guidance |
| `OPS` | Operations |
| `GOV` | Governance |
| `TMP` | Templates |
| `INT` | Integration |
| `PERF` | Performance |
| `OBS` | Observability |
| `REL` | Release |

Reserved domain prefixes shall not be used as first-class identifiers until their artefact pattern is documented.

## 11. Token Conventions

### Named Tokens

- Use uppercase ASCII letters and digits.
- Separate multiple words with hyphens.
- Prefer recognised abbreviations.
- Avoid punctuation, spaces, and underscores.

```text
STD-METADATA
REF-IDENTIFIERS
PB-REQ
```

### Numeric Tokens

- Use zero-padded three-digit sequences where the established family does so.
- Allocate the next available number.
- Never reuse a retired number.

```text
ADR-008
EP-001
```

### Avoid

```text
StandardReview
review-standard
std_review
Review1
MyDocument
```

## 12. Identifier Usage

Identifiers appear in:

- YAML metadata
- Cross-references
- Traceability relationships
- Review reports
- Repository indexes
- Requirements and decisions
- Templates

```yaml
related:
  - STD-TRACEABILITY
  - TERM-STANDARD
  - PB-REQ
```

An identifier is not necessarily a filename, though matching them is preferred when it improves discovery.

## 13. Identifier Lifecycle

- **Updated** — Retain the identifier.
- **Renamed** — Retain the identifier where practical.
- **Deprecated** — Retain it for historical traceability.
- **Replaced** — Record `superseded_by` and `supersedes`.
- **Archived** — Keep the identifier reserved permanently.

Identifiers shall not be recycled.

## 14. Registration Process

Before introducing a new prefix:

1. Confirm that no established prefix fits.
2. Define the artefact family and intended pattern.
3. Check for collisions and ambiguous meanings.
4. Add the prefix to this registry with status Reserved or Established.
5. Update relevant templates and validation only after the convention is approved.

Repository-wide identifier changes require governance review and may require an ADR.

## 15. Automation Considerations

Consistent identifiers enable:

- Uniqueness validation.
- Cross-reference validation.
- Link generation.
- Dependency mapping.
- Repository indexing.
- Search optimisation.
- Knowledge graphs.
- Documentation analytics.

Automation shall use this registry rather than hard-coded undocumented assumptions.

## 16. Related Artefacts

### Standards

- `TERM-STANDARD`
- `STD-METADATA`
- `STD-TRACEABILITY`
- `STD-VERSIONING`

### References

- [`REF-TERMINOLOGY`](REF-TERMINOLOGY.md) — Draft
- `REF-ACRONYMS` — Planned

## 17. External References

- ISO/IEC/IEEE 15288 — System life cycle processes
- ISO/IEC/IEEE 29148 — Requirements engineering

These references inform the registry; ILOS governance remains authoritative for repository identifiers.

## 18. Revision History

| Version | Date | Author | Summary |
|---|---|---|---|
| 1.0.1 | 2026-07-30 | Invara Labs Engineering | Linked the terminology reference and updated its status |
| 1.0.0 | 2026-07-30 | Invara Labs Engineering | Initial draft reconciled with established repository identifiers |

## 19. Summary

Engineering identifiers provide a consistent mechanism for identifying, organising, and connecting artefacts throughout ILOS.

By maintaining an authoritative registry that preserves established IDs and governs future prefixes, ILOS improves navigation, traceability, automation, and long-term maintainability.
