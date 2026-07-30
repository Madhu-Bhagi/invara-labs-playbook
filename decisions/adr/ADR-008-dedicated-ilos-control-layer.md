# ADR-008 — Dedicated ILOS Control Layer

**Status:** Accepted  
**Date:** 30 July 2026  
**Owner:** Founder

## Context

ADR-007 established stable information architecture v1.0 and made Engineering the reference domain. The repository still lacked an explicit boundary between the operating system that governs documentation and the company or engineering content governed by it.

Placing ILOS architecture, roadmap, governance, or lifecycle inside `docs/03-engineering/` would incorrectly make repository-wide governance appear subordinate to one domain.

## Decision

Create a dedicated root-level `ilos/` control layer containing:

- `README.md`
- `ILOS-ARCHITECTURE.md`
- `ILOS-ROADMAP.md`
- `ILOS-GOVERNANCE.md`
- `ILOS-LIFECYCLE.md`
- `ILOS-CHANGELOG.md`

ILOS governs the documentation system. Domain documents, including Engineering, contain the knowledge managed by that system.

The existing numbered domains remain unchanged. This decision extends ADR-007 rather than replacing its domain architecture.

## Alternatives Considered

- Store ILOS documents inside `docs/03-engineering/`.
- Store ILOS documents loosely at the repository root.
- Use separate `roadmap/` and `architecture/` folders.

## Consequences

### Positive

- Clear separation between governance and managed content.
- One predictable location for repository-wide operating-system guidance.
- Independent roadmaps for company content and ILOS development.
- Engineering remains a managed domain rather than the owner of repository governance.

### Negative or Risks

- Contributors must understand the distinction between root context, ILOS controls, and domain content.
- ILOS adds a small documentation layer that must remain intentionally stable.

## Review Conditions

Review only if the control layer becomes unclear, duplicates repository-level context, or fails to govern multiple domains effectively.
