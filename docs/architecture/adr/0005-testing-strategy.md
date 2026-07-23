# ADR-0005: Testing strategy

**Status:** Accepted for what is scaffolded this session; Proposed for
future layers.
**Date:** 2026-07-23

## Context
`Initial Docs/15_IMMUTABLE_GUARDRAILS.md` #29 requires tests/evidence for
every milestone. Session 1 only has a health endpoint and a static frontend
shell, so only smoke-level tests are real right now.

## Decision
This session (real, passing):
- `apps/api/tests/test_health.py` — pytest, asserts `/health` returns
  `{"status": "ok"}`.
- `apps/web/src/App.test.tsx` — vitest + Testing Library, asserts the app
  renders without crashing.

Future/proposed (not yet implemented):
- PostgreSQL-backed integration tests and migration-upgrade tests for the
  API once a database exists.
- Contract-conformance tests once the OpenAPI spec (ADR-0004) exists.
- Thin cross-unit E2E tests per real vertical slice, not before real slices
  exist, per `Initial Docs/10_IMPLEMENTATION_PLAN.md` ("Use fixtures only
  in tests/story environments clearly labeled as such").

## Alternatives considered
- Skipping tests until "real" features land: rejected — guardrail #29
  requires tests per milestone, and a smoke test still catches scaffold
  regressions cheaply.

## Consequences
`pnpm test` (root) runs both suites. No test in this repo may assert against
mock/fake backend data as if it were a real contract.
