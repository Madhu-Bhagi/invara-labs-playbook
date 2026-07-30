# Project Context

**Company:** Invara Labs  
**Repository:** Invara Labs Playbook  
**Current Phase:** Playbook Authoring
**Repository Version:** 1.25.0
**ILOS Version:** 1.20.0
**Last Updated:** 30 July 2026

## Purpose

Build a durable operating system for Invara Labs that captures the company's vision, mission, values, engineering philosophy, business model, delivery standards, decisions, and long-term roadmap.

## Founder Intent

The founder has strong technical and enterprise engineering experience and wants to build a company that:

- Solves real problems faced by startups and established businesses.
- Provides credible and dependable technology solutions.
- Builds client trust through quality deliverables.
- Develops long-term client relationships rather than one-off transactions.
- Uses engineering expertise to simplify complex business problems.
- Applies AI where it creates measurable value.
- Builds repeatable systems instead of depending on individual heroes.
- Eventually develops reusable platforms, AI-assisted delivery systems, and SaaS products.

## Approved Chapters

1. `docs/01-foundation/01-founder-vision.md`
2. `docs/01-foundation/02-mission.md`
3. `docs/01-foundation/03-vision.md`

## Current Chapter

Chapter 04 — Core Values

## Approved Vision

> To become a globally trusted engineering and technology solutions company that helps businesses solve meaningful challenges, build dependable digital products, and create lasting value through exceptional engineering, thoughtfully applied AI, and enduring partnerships.

## Core Positioning

> Invara Labs is an engineering-first technology solutions company that solves real business problems through reliable software, intelligent automation, expert guidance, and long-term partnerships.

## Core Principles

- Engineering First
- AI Enabled
- Business Focused
- Systems over Heroes
- Real Problems before Technology
- Trust through Delivery
- Long-Term Partnerships
- Quality, Trust, and Commitment
- AI Amplifies Engineers; It Does Not Replace Engineering Judgement
- Every Project Should Improve the Company

## Accepted Strategic Decisions

- Engineering-first, not AI-first.
- Systems over individual heroes.
- Invara Labs is a technology solutions company, not merely a software development vendor.
- Business problems come before tools and frameworks.
- The repository is the permanent source of truth.
- Approved chapters, decisions, and session notes must be version-controlled.
- Information architecture v1.0 is stable; future structural changes require an ADR.
- The dedicated `ilos/` control layer governs repository architecture, governance, roadmap, and document lifecycle.
- The ILOS README is the entry point for the Engineering Operating System and its documentation model.
- ILOS Architecture is the stable constitution for engineering document structure, relationships, governance, and evolution.
- ILOS Roadmap is the master backlog and reports status from actual document metadata and content.
- `STD-TRACEABILITY`, `STD-METADATA`, and `STD-VERSIONING` remain Draft and now reference the identifier registry.
- `REF-IDENTIFIERS`, `REF-TERMINOLOGY`, and `REF-ACRONYMS` form the Draft engineering vocabulary foundation and require formal review before approval.
- Repository design is paused; substantive work proceeds one playbook at a time.
- `PB-ARCH` v1.2.3 is the Draft reference implementation for future playbooks and is awaiting gold-standard review.
- `PB-AUTHORING` v1.1.0 remains normative while allowing the phase-oriented reference implementation profile.
- `PB-TECH-DESIGN` v1.0.4 is the second Draft flagship playbook; it directly consumes the `PB-ARCH` baseline and connects implementation-ready design to governed Code Review.
- `PB-AI-ENGINEERING` v1.3.2 is the Draft enterprise Engineering AI Operating Procedure with SDLC-wide guidance, explicit risk management, human accountability, capability governance, and a direct Code Review handoff.
- `PB-CODING` v1.1.1 is the Draft first Execution Layer playbook with explicit governance, risk, secure coding, accountability, Standards integration, production-readiness controls, and a governed Code Review handoff.
- `PB-CODE-REVIEW` v1.0.0 is the Draft independent verification SOP with eight review phases, explicit findings governance, human approval authority, and twelve enterprise appendices.

## Open Work

- Define Chapter 04 — Core Values.
- Define Chapter 05 — Engineering Philosophy.
- Define Chapter 06 — Company Manifesto.
- Define Chapter 07 — Founder Principles.
- Refine market positioning and service packaging after the foundation phase.
- Review and approve `PB-ARCH`.
- Review and approve `PB-TECH-DESIGN` after `PB-ARCH` reaches a stable baseline.
- Review and approve `PB-AI-ENGINEERING`.
- Establish ownership and approval authority before populating `REF-AI-TOOLS`.
- Author `REF-PROMPT-PATTERNS` only from reviewed, reusable engineering practice.
- Review and approve `PB-CODING`.
- Review and approve `PB-CODE-REVIEW`.
- Author `PB-TESTING` after the Code Review workflow is stable.
- Keep ILOS structure stable and focus on substantive playbook content.

## Working Method

1. Discuss one chapter or strategic topic.
2. Challenge assumptions and refine wording.
3. Obtain founder approval.
4. Update the relevant Markdown document.
5. Add or update ADRs where necessary.
6. Record a Founder Journal summary.
7. Update project context, changelog, and roadmap.
8. Commit to Git.
