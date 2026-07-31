# ADR-009 — Engineering Governance Framework and Identifier Family

**Status:** Accepted
**Date:** 31 July 2026
**Owner:** Invara Labs

## Context

The repository now contains core lifecycle and enterprise capability playbooks, but engineering decision rights, exception authority, domain governance, and review cadence are distributed across individual artefacts.

The proposed framework introduces `EGF-ENGINEERING-GOVERNANCE`. `EGF` was not previously registered, and adding a first-class artefact family is a structural convention requiring an ADR under ILOS Governance.

## Decision

1. Establish `EGF` as the identifier prefix for Engineering Governance Frameworks using `EGF-<NAME>`.
2. Create `EGF-ENGINEERING-GOVERNANCE` as the first framework.
3. Place engineering-wide governance frameworks at the root of `docs/03-engineering/` so they sit above its knowledge categories without restructuring the stable repository domains.
4. Keep engineering governance distinct from `ILOS-GOVERNANCE`, which governs the documentation operating system.
5. Require future governance frameworks to follow ILOS metadata, review, versioning, traceability, and lifecycle rules.

## Consequences

- Engineering decision rights and exceptions gain one discoverable source.
- The stable information architecture remains intact.
- `REF-IDENTIFIERS` must register `EGF`.
- Future framework artefacts require governance review and should be created only for demonstrated cross-domain needs.

## Alternatives Considered

### Place the framework in `ilos/`

Rejected because ILOS governs documentation architecture and lifecycle, while the new framework governs engineering work and organisational authority.

### Create a new `docs/01-governance/` domain

Rejected because it conflicts with the established `docs/01-foundation/` domain and would restructure the approved information architecture.

### Use the reserved `GOV` prefix

Rejected because the requested artefact is a specific Engineering Governance Framework family, while `GOV` remains a broad reserved domain prefix without a first-class pattern.
