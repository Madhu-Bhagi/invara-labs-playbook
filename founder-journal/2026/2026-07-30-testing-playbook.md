# Testing Playbook — 30 July 2026

## Context

The Execution Layer needed a governed verification and validation process after Code Review and before Deployment.

## Decision

Create `PB-TESTING` as an enterprise testing SOP rather than a tool-specific quality-assurance manual.

The playbook:

- Consumes the reviewed revision and known conditions from `PB-CODE-REVIEW`.
- Plans testing from requirements, design, risk, and user outcomes.
- Separates verification, validation, test levels, test types, and decision authority.
- Governs environments, data, evidence, defects, fix verification, and regression.
- Preserves human accountability when AI assists.
- Produces a release-readiness recommendation without taking deployment authority.

Specialised testing, security, severity, and test-data standards and references remain planned and non-authoritative until separately approved.

## Outcome

`PB-TESTING` v1.0.0 is a Draft with 34 sections, eight workflow phases, five quality gates, and twelve enterprise appendices.

## Next Step

Review and approve `PB-TESTING`, then author `PB-DEPLOYMENT` against its governed handoff.
