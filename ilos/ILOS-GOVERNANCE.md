# ILOS Governance

**Version:** 1.0.0  
**Status:** Approved  
**Approved On:** 30 July 2026

## Purpose

Define how the operating system is maintained and who may approve changes.

## Governance Principles

1. The repository is the source of truth.
2. Founder intent and approved content must be preserved.
3. Structure serves content; content must not be created merely to fill structure.
4. Important reasoning belongs in ADRs, not only in chat.
5. The smallest coherent change is preferred.
6. Navigation, context, and history must remain consistent after substantive changes.

## Decision Rights

### Founder

- Approves company direction and foundation chapters.
- Approves changes to ILOS architecture and governance.
- Resolves conflicts involving founder intent.

### Document Owner

- Maintains assigned documents.
- Proposes lifecycle and version changes.
- Ensures accuracy and relationships remain current.

### Contributor

- Follows approved structure and templates.
- Updates the minimum necessary files.
- Raises strategic or structural decisions as ADRs.

### AI Assistant

- Reads context and relevant approved documents before editing.
- Preserves approved meaning unless explicitly asked to revise it.
- Identifies inconsistencies and proposes minimal corrections.
- Never treats chat output as authoritative until recorded in the repository.

## Change Classes

### Content Change

Updates knowledge inside an established location. Follow the document lifecycle and versioning rules.

### Structural Change

Adds, removes, renames, or redefines repository-wide locations or conventions. Requires an ADR before implementation.

### Editorial Change

Corrects clarity, spelling, formatting, or links without changing meaning. A patch version is sufficient where documents are versioned.

## Required Updates

Substantive work must update the affected document and, where relevant:

- `PROJECT_CONTEXT.md`
- `CHANGELOG.md`
- `ROADMAP.md`
- Founder Journal
- ADRs
- ILOS documents when the control system changes

## Review Standard

A change is ready when:

- Its purpose is clear.
- It fits the approved architecture.
- Links and navigation work.
- Status and version are accurate.
- Related context and history are updated.
- No approved content was silently replaced.

## Exceptions

Exceptions must identify the constraint, explain why the current rule fails, and record the decision in an ADR.
