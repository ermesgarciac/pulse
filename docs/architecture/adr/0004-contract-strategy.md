# ADR-0004: Contract strategy

**Status:** Proposed
**Date:** 2026-07-23

## Context
No API contract exists yet — `apps/api` only exposes `/health`. This ADR
records the intended strategy so future sessions build toward it instead of
inventing conventions ad hoc, per `Initial Docs/08_SYSTEM_ARCHITECTURE.md`
and this session's Codex planning review.

## Decision (not yet implemented)
- OpenAPI 3.1-first; contract lives under `docs/contracts/openapi/` and is
  generated/validated in CI once real endpoints exist.
- Versioned at `/api/v1`; breaking changes require a new major version.
- RFC 9457-style problem details for errors.
- Idempotency keys required for retryable mutations/jobs.
- Opaque cursor pagination for large collections (no offset pagination).
- Explicit entity version/ETag fields for optimistic concurrency on
  editable entities.

## Alternatives considered
- GraphQL: rejected — canonical docs assume a REST/OpenAPI contract model
  (`08_SYSTEM_ARCHITECTURE.md` "API-first and versioned. OpenAPI generated
  and validated.").

## Consequences
Session 2+ must not add ad hoc endpoints without an OpenAPI definition.
Until a real contract exists, `apps/web` must not claim any backend
capability beyond `/health`.
