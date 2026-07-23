# ADR-0002: Application boundaries

**Status:** Accepted
**Date:** 2026-07-23

## Context
`Initial Docs/08_SYSTEM_ARCHITECTURE.md` requires frontend/backend
separation and a native macOS desktop companion with distinct
responsibilities from the backend.

## Decision
Three independently deployable units, communicating only through the
published API contract:

- `apps/web` — static frontend, no direct DB or filesystem access.
- `apps/api` — owns authentication, authorization, durable domain state
  (PostgreSQL, once introduced), orchestration, server-side jobs.
- `apps/desktop` — native macOS companion owning user-approved local
  filesystem access, local playback, DJ database integration, USB/export
  workflows (not scaffolded this session — see `apps/desktop/README.md`).

Workers (when introduced) are a backend deployment component, not a fourth
product application, and never become a second domain authority.

## Alternatives considered
- Shared backend/frontend DB access: rejected — violates
  `Initial Docs/15_IMMUTABLE_GUARDRAILS.md` #7 (frontend/backend separated)
  and the contract-first principle in ADR-0004.

## Consequences
Every cross-unit interaction must go through a versioned contract (ADR-0004).
No unit may read another unit's internal storage directly.
