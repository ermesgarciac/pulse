# Pulse

Self-hosted Music Workspace for DJs. See `Initial Docs/00_START_HERE.md` for
the canonical product/UX/architecture package and `docs/architecture/adr/`
for accepted technical decisions.

## Workspace commands (run from repo root)

- `pnpm install` — install JS dependencies
- `pnpm format` — format the web app
- `pnpm lint` — lint web (eslint) and api (ruff)
- `pnpm typecheck` — typecheck web (tsc) and api (mypy)
- `pnpm test` — run web (vitest) and api (pytest) test suites
- `pnpm build` — build the web app

Python commands for `apps/api` also work directly via `cd apps/api && uv run <cmd>`.
