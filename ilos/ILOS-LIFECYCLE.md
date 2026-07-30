# ILOS Document Lifecycle

**Version:** 1.0.0  
**Status:** Approved  
**Approved On:** 30 July 2026

## Purpose

Define how documents are proposed, developed, approved, maintained, deprecated, and archived.

## Lifecycle

```text
Planned → Draft → Review → Approved → Deprecated → Archived
```

### Planned

A known document need with little or no substantive content.

### Draft

Content is being developed and may change significantly.

### Review

The document is coherent and awaiting owner or founder approval.

### Approved

The document is authoritative and may only change through an explicit revision.

### Deprecated

The document is no longer recommended but remains available for context or migration.

### Archived

The document is retained for historical reference and removed from active navigation.

## Approval Rules

- Foundation and ILOS documents require founder approval.
- Domain documents require the designated owner; strategic changes may also require founder approval.
- Standards must be enforceable before approval.
- Examples cannot override principles, playbooks, or standards.

## Versioning

Use semantic versioning:

- **Major** — fundamental change in meaning, scope, or governance
- **Minor** — meaningful compatible addition
- **Patch** — editorial correction or clarification

Planned placeholders do not need independent versions until substantive drafting begins.

## Required Metadata

Substantive documents should identify:

- Version
- Status
- Owner
- Created or approved date
- Last updated date when relevant

Approved documents should include revision history when revised.

## Change Flow

1. Identify the need.
2. Confirm the correct location and relationships.
3. Draft the smallest complete document.
4. Review against approved context.
5. Obtain the required approval.
6. Update status and version.
7. Update context, changelog, roadmap, journal, or ADRs as applicable.
8. Verify navigation and links.

## Review and Deprecation

Documents are reviewed when:

- Their assumptions materially change.
- Repeated confusion suggests unclear guidance.
- A new decision supersedes them.
- They obstruct a real workflow.

Deprecation must identify the replacement or explain why no replacement is needed.
