# ILOS Changelog

All changes to the Invara Labs Operating System control layer are recorded here.

## [1.22.0] — 30 July 2026

### Added

- Deployment Playbook (`PB-DEPLOYMENT`) v1.0.0 as a governed Draft.
- Seven-phase release workflow, release authority, recovery, environment and change controls, five quality gates, and twelve enterprise appendices.

### Changed

- Connected upstream engineering playbooks to the governed Deployment stage.
- Moved Deployment from Planned to In Progress in the ILOS Roadmap.

## [1.21.0] — 30 July 2026

### Added

- Testing Playbook (`PB-TESTING`) v1.0.0 as a governed Draft.
- Eight-phase risk-based testing workflow, test and defect governance, five quality gates, and twelve enterprise appendices.

### Changed

- Connected Technical Design, AI Engineering, Coding, and Code Review to the governed Testing stage.
- Moved Testing from Planned to In Progress in the ILOS Roadmap.

## [1.20.0] — 30 July 2026

### Added

- Code Review Playbook (`PB-CODE-REVIEW`) v1.0.0 as a governed Draft.
- Eight-phase independent verification workflow, review decisions, findings classification, accountability controls, and twelve enterprise appendices.

### Changed

- Connected Technical Design, Coding, and AI Engineering to the governed Code Review stage.
- Moved Code Review from Planned to In Progress in the ILOS Roadmap.

## [1.19.0] — 30 July 2026

### Changed

- Expanded `PB-CODING` to v1.1.0 as a 34-section enterprise execution SOP.
- Added governance, risk, secure-coding, accountability, Standards-integration, documentation-phase, and production-readiness controls.
- Aligned the twelve enterprise appendices with the implementation governance layer.

## [1.18.0] — 30 July 2026

### Added

- Coding Playbook (`PB-CODING`) v1.0.0 as a governed Draft and the first Execution Layer playbook.
- Implementation workflow, executable deliverables, coding gates, self-review, automated evidence, review-package controls, and enterprise appendices.

### Changed

- Connected Technical Design and AI Engineering to the Coding execution stage.
- Moved Coding from Planned to In Progress in the ILOS Roadmap.

## [1.17.0] — 30 July 2026

### Changed

- Elevated `PB-AI-ENGINEERING` to v1.3.0 as a vendor-neutral enterprise AI operating procedure.
- Added dedicated SDLC, AI risk, intellectual-property, human-accountability, and approved-capability sections.
- Added twelve enterprise appendices aligned with the flagship playbook quality model.

## [1.16.0] — 30 July 2026

### Changed

- Refined `PB-AI-ENGINEERING` to v1.2.0 around process, governance, approved usage, and human verification.
- Removed embedded changeable tool and prompt guidance from the playbook.
- Aligned the flagship document to 32 sections and corrected appendix numbering.

### Added

- Planned AI Tools Reference (`REF-AI-TOOLS`).
- Planned Engineering Prompt Patterns Reference (`REF-PROMPT-PATTERNS`).

## [1.15.0] — 30 July 2026

### Added

- AI Engineering Playbook (`PB-AI-ENGINEERING`) v1.1.0 as a governed Draft and foundational cross-lifecycle playbook.
- Common controls for approved tools, safe context, prompt task briefs, independent verification, security and privacy, human acceptance, and AI contribution traceability.

### Changed

- Renamed the narrower Draft `PB-AI-DEVELOPMENT` identity and expanded the SOP to 33 sections.
- Linked `PB-ARCH` v1.2.3 and `PB-TECH-DESIGN` v1.0.2 to the AI control layer.
- Moved AI Engineering from Planned to In Progress in the ILOS Roadmap.

## [1.14.0] — 30 July 2026

### Added

- Technical Design Playbook (`PB-TECH-DESIGN`) v1.0.0 as a governed Draft.
- Nine-phase technical-design workflow, five quality gates, implementation deliverables, templates, AI controls, and enterprise review appendices.

### Changed

- Connected the approved-architecture output of `PB-ARCH` v1.2.1 to the implementation-readiness input of `PB-TECH-DESIGN`.
- Moved Technical Design from Planned to In Progress in the ILOS Roadmap.

## [1.13.0] — 30 July 2026

### Changed

- Expanded `PB-ARCH` to v1.2.0 as the Draft reference implementation for future playbooks.
- Added a phase governance matrix and traceability from business need through operational evidence.
- Added reusable review, decision, quality, risk, technology-evaluation, approval, deliverables, and maturity controls.
- Added a gold-standard review gate before approval.
- Updated `PB-AUTHORING` to v1.1.0 so its mandatory coverage aligns with the phase-oriented reference implementation.

## [1.12.0] — 30 July 2026

### Changed

- Refined `PB-ARCH` to v1.1.0 as an explicit nine-phase architecture standard operating procedure.
- Added phase outcomes, deliverables, approval flow, handover criteria, and phase-specific AI accountability.
- Adopted the established `PB-ARCH.md` filename across repository navigation.

## [1.11.0] — 30 July 2026

### Added

- Software Architecture Playbook (`PB-ARCH`) v1.0.0 as a governed Draft.
- End-to-end architecture workflow covering drivers, options, decisions, validation, review, delivery, and evolution.

### Changed

- Moved the active repository phase from foundation design to playbook authoring.
- Updated the Playbooks index, ILOS Roadmap, and progress dashboard.
- Selected the Technical Design Playbook as the next playbook after architecture review.

## [1.10.0] — 30 July 2026

### Changed

- Expanded `REF-ACRONYMS` to v1.1.0 with additional architecture, development, testing, operations, and security entries.
- Kept artefact prefixes in `REF-IDENTIFIERS` and rejected `PR` as a universal Principle prefix.
- Preserved one ILOS meaning for ambiguous acronyms.

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
