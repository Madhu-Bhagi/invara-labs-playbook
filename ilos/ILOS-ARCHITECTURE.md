# ILOS Architecture

**Version:** 1.0.0  
**Status:** Approved  
**Approved On:** 30 July 2026

## Purpose

Define the boundaries, layers, and information architecture of the Invara Labs Operating System.

## Core Model

```text
ILOS control layer
├── Architecture
├── Governance
├── Roadmap
├── Document lifecycle
└── Change history
        │
        ▼
Managed knowledge
├── Company and foundation
├── Domain documentation
├── Decisions and journals
├── Prompts and templates
└── Supporting assets
```

ILOS defines how knowledge is managed. Domain documents contain the knowledge itself.

## Repository Layers

### 1. Control Layer — `ilos/`

Defines repository architecture, governance, lifecycle, roadmap, and ILOS change history.

### 2. Context Layer — repository root

Provides current state and contributor entry points:

- `README.md`
- `PROJECT_CONTEXT.md`
- `AI_GUIDE.md`
- `CODEX.md`
- `ROADMAP.md`
- `CHANGELOG.md`
- `CONTRIBUTING.md`

The root roadmap tracks company and playbook delivery. The ILOS roadmap tracks development of the operating system itself.

### 3. Knowledge Layer — `docs/`

Stores approved and evolving company knowledge by domain.

Mature domains may use:

```text
Domain/
├── README.md
├── 01-principles/
├── 02-playbooks/
├── 03-standards/
├── 04-reference/
└── 05-examples/
```

Engineering is the reference implementation of this domain pattern.

### 4. Memory and Governance Layer

- `decisions/adr/` — durable strategic and architectural decisions
- `founder-journal/` — founder discussions and session outcomes
- `meeting-notes/` — operational meeting records

### 5. Enablement Layer

- `prompts/` — reusable AI roles and workflows
- `templates/` — repeatable document structures
- `assets/` — diagrams, images, and logos

## Architectural Rules

1. ILOS documents must not be placed inside an individual business domain.
2. Domain content must not redefine ILOS governance.
3. Repository-wide structural changes require an ADR.
4. Do not create folders or documents without a known purpose.
5. Engineering remains the reference domain; other domains adopt its pattern only when useful.
6. Navigation must remain possible from the root README and relevant local README.
7. The repository must distinguish stable, in-progress, and planned work.

## Maturity Model

- 🟢 **Stable** — approved and dependable
- 🟡 **In Progress** — actively being developed or reviewed
- 🔴 **Planned** — intended but not yet substantive

## Relationships

- Governed by [ILOS Governance](ILOS-GOVERNANCE.md)
- Evolved through [ILOS Lifecycle](ILOS-LIFECYCLE.md)
- Sequenced by [ILOS Roadmap](ILOS-ROADMAP.md)
- Established by [ADR-008](../decisions/adr/ADR-008-dedicated-ilos-control-layer.md)
