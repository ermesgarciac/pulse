# ADR-0006: Local development

**Status:** Accepted
**Date:** 2026-07-23

## Context
Session 1 needs a documented, executable local dev flow without introducing
Docker/Proxmox deployment (explicitly excluded this session per the
bootstrap prompt).

## Decision
- `pnpm install` at repo root installs all JS/TS workspace dependencies.
- `cd apps/api && uv sync` (or `uv add`/`uv run`) manages Python
  dependencies in an isolated `.venv`.
- Root `package.json` scripts fan out to both apps:
  `format`, `lint`, `typecheck`, `test`, `build`.
- No Docker Compose this session — there is no backend service worth
  containerizing yet (only a `/health` endpoint); revisit once the API has
  real persistence.

## Alternatives considered
- Docker Compose from day one: rejected — `Initial Docs/CLAUDE_BOOTSTRAP_PROMPT.md`
  explicitly excludes "production Docker/Proxmox deployment" from Session 1,
  and there is no service yet that benefits from containerized local dev.

## Consequences
Contributors run `pnpm install` + `uv sync` once, then use root `pnpm`
scripts for day-to-day checks. Docker/Proxmox setup is deferred to a later
ADR when the API has real state to run.
