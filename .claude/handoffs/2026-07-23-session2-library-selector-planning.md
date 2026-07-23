# Handoff — Session 2: Library Selector + active-Library shell planning

## Repository
- Root: `/Users/ermegarcia/Documents/Claude Projects/Pulse`
- Remote: `origin` = `https://github.com/ermesgarciac/pulse.git`
- Branch: `main` (Session 1 foundation committed locally; not yet pushed)

## Starting state
Session 1 foundation is complete and verified (see
`docs/session-reports/2026-07-23-session1-foundation.md`): working
`apps/api` (FastAPI, `/health` only), `apps/web` (Vite/React/TS shell,
Vite starter content — no Pulse UI yet), `apps/desktop` (placeholder only),
6 ADRs, operating contract, all root commands (`format`/`lint`/`typecheck`/
`test`/`build`) passing. No database, no OpenAPI contract, no domain models
exist yet.

## Objective
Plan and write contracts for the Library Selector (Level 0) and the active-
Library shell (Level 1) per `Initial Docs/05_CANONICAL_UX_SPEC.md` and
`06_SCREEN_AND_FLOW_SPEC.md`. **Planning and contract design only — do not
implement the Library Selector or internal Library UI this session.**

## Owned and protected files
No concurrent-edit conflicts exist yet — no backend domain code exists to
divide. Before any implementation session (Session 3+), assign explicit
file ownership between Claude (UI/visual) and Codex (backend/data) per
`.claude/rules/pulse-operating-contract.md` before either starts editing.

## Required reading
- `Initial Docs/05_CANONICAL_UX_SPEC.md` — Library selector (Level 0) and
  active-Library shell (Level 1) information architecture.
- `Initial Docs/06_SCREEN_AND_FLOW_SPEC.md` §1 (Library Selector).
- `Initial Docs/08_SYSTEM_ARCHITECTURE.md` — domain boundaries (Identity:
  users, devices, Libraries).
- `Initial Docs/09_DOMAIN_AND_FEATURES.md` — Library entity definition.
- `docs/architecture/adr/0002-application-boundaries.md`,
  `0004-contract-strategy.md` — binding boundaries and contract shape this
  session's plan must fit inside.
- `Initial Docs/15_IMMUTABLE_GUARDRAILS.md` #2–#6 — Library isolation rules
  (never appears in internal sidebar, switching from a higher-level
  selector, no cross-Library data leakage).

## Acceptance criteria
- A real Library create/list/select API contract is designed (OpenAPI
  fragment under `docs/contracts/openapi/`, per ADR-0004), not implemented.
- Library isolation/authorization approach is specified (how the API will
  guarantee no cross-Library leakage).
- UI plan for Library Selector + shell entry point exists at a
  contract/wireframe level, not built components.
- Codex has reviewed the contract/data-ownership plan and Claude has
  reconciled findings, both recorded per the operating contract.
- Session stays to 2–3 deliverables; explicit exclusions stated up front
  (no built UI, no auth implementation, no database migrations yet unless
  the plan requires a schema ADR).

## Commands to verify
Same as Session 1 — from repo root: `pnpm install`, `pnpm format`,
`pnpm lint`, `pnpm typecheck`, `pnpm test`, `pnpm build`. All must still
pass after this session even though it's planning-focused (no regressions
introduced to the existing scaffold).

## Known blockers
None. Toolchain confirmed available: node v25.9.0, npm 11.12.1, pnpm,
python3.13, uv, cargo/rustc (via `~/.cargo/bin`) — no Go.

## What not to do
- Do not implement the Library Selector or internal Library UI (excluded
  until Session 3+ per the bootstrap prompt's phase sequencing).
- Do not add "Libraries" as a sidebar item inside an active Library
  (guardrail #4).
- Do not wire up PostgreSQL/Alembic without a dedicated ADR superseding
  ADR-0003's "Proposed" status for the backend persistence layer.
- Do not scaffold `apps/desktop`/Tauri — still deferred to Phase 3.
- Do not push to `origin`, force-push, or open a PR without explicit user
  approval — user authorized local commits only in Session 1.
