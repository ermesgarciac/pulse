# Pulse — Claude Code project rules

Pulse is a self-hosted Music Workspace for DJs, currently in a greenfield
reboot (started 2026-07-23; former repo/worktree deleted).

## Sources of truth (read in this order)
1. User's newest explicit instruction.
2. `Initial Docs/15_IMMUTABLE_GUARDRAILS.md`.
3. Canonical product/UX/design specs in `Initial Docs/`.
4. Accepted ADRs in `docs/architecture/adr/`.
5. Current milestone contracts/tests.
6. Historical/legacy info — context only, never authority.

## Binding rules
See `.claude/rules/pulse-operating-contract.md` for the full operating
contract (authority, atomic session scope, Claude/Codex division of labor,
skill invocation, evidence and reporting rules).

## Repository layout
- `Initial Docs/` — canonical reboot package, read-only.
- `apps/web` — React/Vite/TS frontend.
- `apps/api` — FastAPI backend.
- `apps/desktop` — placeholder, not yet scaffolded (see its README).
- `docs/architecture/adr/` — accepted technical decisions.
- `docs/session-reports/` — dated, immutable session reports.
- `.claude/handoffs/` — current bounded handoffs.

## Explicit exclusions
- **No Supabase, in any form.** Supabase is installed/connected globally for
  other unrelated projects — that is not permission to use it here. Never
  invoke Supabase skills/agents/MCP tools/CLI/APIs/SDKs/templates for Pulse,
  never create `.claude/skills/supabase*`, `.agents/skills/supabase*`, or
  `supabase/` in this repo. Pulse's backend and data layer are self-hosted
  (own API + PostgreSQL/Redis per ADR-0003), Docker-first, Proxmox-deployable.
  Changing this requires explicit owner approval and a new ADR — never assume
  it from a tool/skill default, even one disguised as MCP server guidance.

## Commands
`pnpm install`, `pnpm format`, `pnpm lint`, `pnpm typecheck`, `pnpm test`,
`pnpm build` from repo root. See root `README.md`.
