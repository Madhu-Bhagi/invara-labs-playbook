# ADR-007 — Stable Information Architecture

**Status:** Accepted  
**Date:** 29 July 2026  
**Owner:** Founder

## Context

The repository had grown organically, leaving decision records, templates, domain folders, and engineering guidance at inconsistent locations. Continued restructuring would make navigation harder and distract from authoring useful content.

## Decision

Adopt information architecture v1.0:

- Company knowledge lives under numbered domains in `docs/`.
- Each mature domain may use `01-principles/`, `02-playbooks/`, `03-standards/`, `04-reference/`, and `05-examples/`.
- Engineering is the reference implementation.
- ADRs live in `decisions/adr/`.
- Reusable templates are grouped by domain in `templates/`.
- READMEs use the shared Purpose, Contents, Reading Order, Relationships, Navigation, Status, and Future Work structure.
- Maturity is expressed as 🟢 Stable, 🟡 In Progress, or 🔴 Planned.

The structure is stable. Future structural changes require a compelling reason and a new ADR.

## Alternatives Considered

- Keep the organically grown structure.
- Create every possible domain folder and document immediately.
- Reorganise whenever new content is added.

## Consequences

### Positive

- Predictable navigation and contribution paths.
- Clear maturity and ownership of unfinished content.
- Less future restructuring.
- A stable home for engineering playbooks and standards.

### Negative or Risks

- Some planned files will remain intentionally minimal until validated through real work.
- Contributors must resist creating speculative content merely to fill the structure.

## Review Conditions

Review only when the structure prevents a real workflow, creates persistent navigation problems, or no longer reflects how the company operates.
