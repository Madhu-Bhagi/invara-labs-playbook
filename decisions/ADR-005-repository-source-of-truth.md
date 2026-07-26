# ADR-005 — Repository as the Source of Truth

**Status:** Accepted  
**Date:** 27 July 2026

## Context

Important company knowledge was being developed through chat conversations. Chat history is difficult to govern, version, search, and transfer across tools.

## Decision

The Invara Labs Playbook repository will be the permanent source of truth.

Approved chapters, strategic decisions, session summaries, context, roadmap, and revision history must be stored in version-controlled files.

## Consequences

- Important decisions must not remain only in chat.
- Every significant session should update the repository.
- AI assistants should read repository context before continuing work.
- Git history becomes part of the company's institutional memory.
- The company can switch tools without losing context.
