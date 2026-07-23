# ADR-0003: Candidate stack choices

**Status:** Mixed (see per-item status)
**Date:** 2026-07-23

## Context
`Initial Docs/17_GREENFIELD_SETUP.md` treats the former FastAPI/Postgres/
Redis/ARQ/Alembic stack as a candidate, not binding. This session scaffolds
enough to prove real commands work, without adopting unneeded infrastructure.

## Decision
- **Backend — FastAPI (Python 3.13, managed via `uv`): Proposed.**
  Scaffolded this session as `apps/api` with a real `/health` endpoint only;
  PostgreSQL and Alembic are not yet wired up (no domain data exists yet).
- **Job queue — Redis + ARQ: Deferred.** No real job/analysis slice exists
  yet (targeted at Implementation Plan Phase 4); adding a queue now would be
  premature architecture (Codex planning review risk #1).
- **Frontend — React + Vite + TypeScript (managed via `pnpm`): Accepted.**
  Scaffolded this session as `apps/web` with a passing smoke test, lint
  (`oxlint`), typecheck, and build.
- **Desktop — Tauri 2 + Rust: Proposed.** Not scaffolded this session (see
  `apps/desktop/README.md`); deferred to Implementation Plan Phase 3.
- **Package management — pnpm (JS/TS workspace), uv (Python): Accepted.**
  Both already available in this environment and used for the scaffolds
  above.

## Alternatives considered
- npm/yarn workspaces instead of pnpm: rejected — pnpm was already installed
  and has stronger monorepo workspace support.
- pip/poetry instead of uv: rejected — uv was already installed and is
  faster; no existing project convention to preserve.

## Consequences
Anything marked Proposed/Deferred requires its own ADR update (or a new ADR)
before being treated as binding. No PostgreSQL, Redis, or Tauri dependency
exists in this codebase yet — do not assume otherwise.
