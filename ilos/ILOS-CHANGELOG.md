# ILOS Changelog

All changes to the Invara Labs Operating System control layer are recorded here.

## [1.9.0] — 30 July 2026

### Added

- Engineering Acronym Reference (`REF-ACRONYMS`) v1.0.0 as a governed Draft.
- Shared acronym catalogue spanning engineering, architecture, development, testing, operations, governance, and AI.

### Changed

- Defined one ILOS meaning for ambiguous acronyms such as `CD` and `MTTR`.
- Linked the acronym catalogue from terminology governance and the core references.
- Updated the ILOS Roadmap and Engineering Reference index.

## [1.8.0] — 30 July 2026

### Added

- Engineering Terminology Reference (`REF-TERMINOLOGY`) v1.0.0 as a governed Draft.
- Controlled definitions for core documentation, governance, architecture, delivery, quality, operations, and AI-assisted engineering terms.

### Changed

- Linked the terminology reference from its governing standard and related governance artefacts.
- Updated the ILOS Roadmap and Engineering Reference index.

## [1.7.0] — 30 July 2026

### Added

- Engineering Identifier Reference (`REF-IDENTIFIERS`) v1.0.0 as a governed Draft.
- Authoritative registry for primary artefacts, principle families, compatibility IDs, reserved prefixes, and identifier lifecycle.

### Changed

- Linked the identifier registry from metadata, traceability, and versioning standards.
- Updated the ILOS Roadmap and Reference index.
- Reconciled the proposed universal `PR` prefix with established discipline-specific principle IDs.

## [1.6.0] — 30 July 2026

### Added

- Engineering Versioning Standard (`STD-VERSIONING`) v1.0.0 as a governed Draft.
- Semantic versioning rules, lifecycle/version separation, revision-history requirements, compatibility guidance, and supersession governance.

### Changed

- Replaced the generic versioning placeholder with the canonical standard.
- Updated the ILOS Roadmap and shifted the next planned work to engineering references.

## [1.5.0] — 30 July 2026

### Added

- Engineering Metadata Standard (`STD-METADATA`) v1.0.0 as a governed Draft.
- Mandatory YAML metadata model, controlled lifecycle values, validation rules, governance responsibilities, and incremental adoption guidance.

### Changed

- Updated the ILOS Roadmap catalogue and progress dashboard.
- Identified `STD-VERSIONING` as the next planned governance standard.

## [1.4.0] — 30 July 2026

### Added

- Engineering Traceability Standard (`STD-TRACEABILITY`) v1.0.0 as a governed Draft.
- End-to-end traceability requirements covering documentation, decisions, implementation, testing, releases, and operations.

### Changed

- Updated the ILOS Roadmap catalogue and progress dashboard.
- Added `STD-METADATA` as the next planned automation dependency.

## [1.3.0] — 30 July 2026

### Changed

- Expanded ILOS Roadmap into the master backlog for the Engineering Operating System.
- Added delivery phases, the actual engineering documentation catalogue, progress dashboard, dependencies, priorities, success criteria, and roadmap governance.
- Reconciled completion statuses against document metadata and substantive content.
- Recorded the proposed ILOS design-principles document as under consideration rather than creating overlapping content.

## [1.2.0] — 30 July 2026

### Changed

- Expanded ILOS Architecture into the stable constitution for engineering knowledge.
- Added architectural goals, design principles, document relationships, governance and AI architecture, constraints, and evolution rules.
- Added the canonical visual model for ILOS.
- Adapted the proposed `foundation/` structure to the approved `ilos/` control layer and `decisions/adr/` decision system.

## [1.1.0] — 30 July 2026

### Changed

- Expanded the ILOS README into the professional landing page for the Engineering Operating System.
- Added vision, objectives, guiding principles, documentation model, lifecycle, governance, AI-native engineering guidance, and contributor navigation.
- Retained the `ilos/` namespace to avoid conflict with the existing `docs/01-foundation/` company domain.

## [1.0.0] — 30 July 2026

### Added

- Dedicated `ilos/` control layer.
- ILOS architecture.
- ILOS roadmap.
- ILOS governance.
- Document lifecycle and versioning rules.
- Explicit separation between ILOS and managed domain content.

### Confirmed

- Engineering remains the reference domain.
- Root `ROADMAP.md` tracks company and content delivery.
- `ILOS-ROADMAP.md` tracks operating-system development.
- Future repository-wide structural changes require an ADR.
