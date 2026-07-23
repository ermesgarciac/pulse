# Pulse Session 1 — Repository Foundation Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Stand up Pulse's minimal git-backed workspace foundation (working api + web scaffolds, ADRs, and the Claude–Codex operating contract) with real, passing format/lint/typecheck/test/build commands — no feature UI, no backend domain logic.

**Architecture:** pnpm-workspace monorepo. `apps/api` = FastAPI + uv-managed Python service with one real `/health` endpoint. `apps/web` = Vite + React + TypeScript with one real smoke test. `apps/desktop` = documented-but-unscaffolded placeholder (Tauri init deferred to the milestone that actually needs native code, per "do not pre-create a monorepo structure that prejudges those decisions"). ADRs in `docs/architecture/adr/` record every choice as accepted/proposed/deferred/unknown.

**Tech Stack:** pnpm (workspaces), uv (Python/FastAPI), Vite + React + TypeScript, ruff + mypy (Python), eslint + prettier + tsc (TS), pytest, vitest.

---

### Task 1: `.gitignore` and canonical-package commit

**Files:**
- Create: `.gitignore`

- [ ] **Step 1: Write `.gitignore`**

```gitignore
# OS
.DS_Store

# Node
node_modules/
dist/
*.log
.vite/

# Python
__pycache__/
*.pyc
.venv/
.pytest_cache/
.mypy_cache/
.ruff_cache/

# Rust / Tauri
target/

# Editors
.vscode/
.idea/
```

- [ ] **Step 2: Stage and commit the canonical package**

```bash
git add "Initial Docs" Images .gitignore
git commit -m "docs: add canonical Pulse reboot package"
```

Expected: commit succeeds, `git log --oneline -1` shows the message.

---

### Task 2: Root pnpm workspace tooling

**Files:**
- Create: `package.json`
- Create: `pnpm-workspace.yaml`
- Create: `README.md`

- [ ] **Step 1: Write root `package.json`**

```json
{
  "name": "pulse",
  "private": true,
  "version": "0.0.0",
  "scripts": {
    "format": "pnpm --filter web format",
    "lint": "pnpm --filter web lint && (cd apps/api && uv run ruff check .)",
    "typecheck": "pnpm --filter web typecheck && (cd apps/api && uv run mypy app)",
    "test": "pnpm --filter web test -- --run && (cd apps/api && uv run pytest)",
    "build": "pnpm --filter web build"
  }
}
```

- [ ] **Step 2: Write `pnpm-workspace.yaml`**

```yaml
packages:
  - "apps/*"
```

- [ ] **Step 3: Write root `README.md`**

```markdown
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
```

- [ ] **Step 4: Commit**

```bash
git add package.json pnpm-workspace.yaml README.md
git commit -m "chore: add root workspace tooling"
```

---

### Task 3: `apps/api` — FastAPI skeleton with real health endpoint

**Files:**
- Create: `apps/api/pyproject.toml`
- Create: `apps/api/app/__init__.py`
- Create: `apps/api/app/main.py`
- Create: `apps/api/tests/__init__.py`
- Create: `apps/api/tests/test_health.py`
- Create: `apps/api/README.md`

- [ ] **Step 1: Initialize the uv project**

```bash
mkdir -p "/Users/ermegarcia/Documents/Claude Projects/Pulse/apps/api"
cd "/Users/ermegarcia/Documents/Claude Projects/Pulse/apps/api"
uv init --no-readme --python 3.13 .
```

Expected: creates `pyproject.toml`, `.python-version`, `main.py` (delete the default `main.py`, we replace it below).

- [ ] **Step 2: Add dependencies**

```bash
uv add fastapi "uvicorn[standard]"
uv add --dev pytest httpx ruff mypy
```

- [ ] **Step 3: Write `app/__init__.py`**

```python
```

(empty file, marks `app` as a package)

- [ ] **Step 4: Write `app/main.py`**

```python
from fastapi import FastAPI

app = FastAPI(title="Pulse API", version="0.1.0")


@app.get("/health")
def health() -> dict[str, str]:
    return {"status": "ok"}
```

- [ ] **Step 5: Delete uv's default `main.py` and write the failing test**

```bash
rm -f main.py
mkdir -p tests
touch tests/__init__.py
```

`tests/test_health.py`:

```python
from fastapi.testclient import TestClient

from app.main import app

client = TestClient(app)


def test_health_returns_ok() -> None:
    response = client.get("/health")
    assert response.status_code == 200
    assert response.json() == {"status": "ok"}
```

- [ ] **Step 6: Run test to verify it passes**

```bash
uv run pytest
```

Expected: `1 passed`.

- [ ] **Step 7: Run lint and typecheck**

```bash
uv run ruff check .
uv run mypy app
```

Expected: both exit 0 (fix any import/type issues ruff/mypy report before moving on).

- [ ] **Step 8: Write `apps/api/README.md`**

```markdown
# Pulse API

FastAPI skeleton. Real endpoints only — no mock/placeholder data.

- `uv run uvicorn app.main:app --reload` — run locally
- `uv run pytest` — tests
- `uv run ruff check .` — lint
- `uv run mypy app` — typecheck
```

- [ ] **Step 9: Commit**

```bash
cd "/Users/ermegarcia/Documents/Claude Projects/Pulse"
git add apps/api
git commit -m "feat(api): add FastAPI skeleton with health endpoint"
```

---

### Task 4: `apps/web` — Vite + React + TS skeleton with real smoke test

**Files:**
- Create: `apps/web/` (via `pnpm create vite`)
- Modify: `apps/web/package.json` (add format/lint/typecheck/test scripts)
- Create: `apps/web/src/App.test.tsx`

- [ ] **Step 1: Scaffold with Vite**

```bash
cd "/Users/ermegarcia/Documents/Claude Projects/Pulse/apps"
pnpm create vite web --template react-ts
cd web
pnpm install
```

- [ ] **Step 2: Add test/format tooling**

```bash
pnpm add -D vitest @testing-library/react @testing-library/jest-dom jsdom prettier
```

- [ ] **Step 3: Add scripts to `apps/web/package.json`** (merge into existing `"scripts"` block)

```json
{
  "scripts": {
    "dev": "vite",
    "build": "tsc -b && vite build",
    "lint": "eslint .",
    "typecheck": "tsc -b --noEmit",
    "format": "prettier --write .",
    "test": "vitest"
  }
}
```

- [ ] **Step 4: Write `apps/web/vitest.config.ts`**

```typescript
import { defineConfig } from "vitest/config";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
  test: {
    environment: "jsdom",
    globals: true,
  },
});
```

- [ ] **Step 5: Write `apps/web/src/setupTests.ts`**

```typescript
import "@testing-library/jest-dom";
```

Register it by adding `setupFiles: ["./src/setupTests.ts"]` to the `test` block in `vitest.config.ts`.

- [ ] **Step 6: Write failing smoke test `apps/web/src/App.test.tsx`**

```tsx
import { describe, expect, it } from "vitest";
import { render, screen } from "@testing-library/react";
import App from "./App";

describe("App", () => {
  it("renders without crashing", () => {
    render(<App />);
    expect(document.body).toBeTruthy();
  });
});
```

- [ ] **Step 7: Run the test suite**

```bash
pnpm test -- --run
```

Expected: `1 passed` (uses Vite's default `App.tsx` — real render, not a mock).

- [ ] **Step 8: Run lint, typecheck, build**

```bash
pnpm lint
pnpm typecheck
pnpm build
```

Expected: all exit 0; `build` produces `apps/web/dist/`.

- [ ] **Step 9: Commit**

```bash
cd "/Users/ermegarcia/Documents/Claude Projects/Pulse"
git add apps/web
git commit -m "feat(web): add Vite/React/TS skeleton with smoke test"
```

---

### Task 5: `apps/desktop` — documented placeholder only

**Files:**
- Create: `apps/desktop/README.md`

- [ ] **Step 1: Write the placeholder README**

```markdown
# Pulse Desktop (placeholder)

Not yet scaffolded. Per `Initial Docs/17_GREENFIELD_SETUP.md`, Session 1 must
not pre-create application structure that prejudges undecided details. The
candidate stack (Tauri 2 + Rust, native macOS local-filesystem/playback/DJ-db
access) is recorded as **proposed** in
`docs/architecture/adr/0003-stack-choices.md`.

Real Tauri scaffolding happens in the milestone that first needs native
desktop code (Phase 3 — Playback and Track Workspace core, per
`Initial Docs/10_IMPLEMENTATION_PLAN.md`), not in this foundation session.
```

- [ ] **Step 2: Commit**

```bash
git add apps/desktop
git commit -m "docs(desktop): record placeholder pending native-code milestone"
```

---

### Task 6: Architecture Decision Records

**Files:**
- Create: `docs/architecture/adr/0001-repository-layout.md`
- Create: `docs/architecture/adr/0002-application-boundaries.md`
- Create: `docs/architecture/adr/0003-stack-choices.md`
- Create: `docs/architecture/adr/0004-contract-strategy.md`
- Create: `docs/architecture/adr/0005-testing-strategy.md`
- Create: `docs/architecture/adr/0006-local-development.md`

Each ADR uses this shape (fill per topic below):

```markdown
# ADR-000N: <Title>

**Status:** Accepted | Proposed | Deferred | Unknown
**Date:** 2026-07-23

## Context
<why this decision is needed now>

## Decision
<what was decided>

## Alternatives considered
<bullet list with why rejected/deferred>

## Consequences
<what this enables or constrains>
```

- [ ] **Step 1: `0001-repository-layout.md`** — Status: Accepted.
  Decision: single pnpm-workspace monorepo, `apps/{web,api,desktop}`,
  `docs/architecture/adr/`, `docs/contracts/`, `docs/design/`,
  `docs/session-reports/`. Alternatives: polyrepo (rejected — contracts/dev
  commands need to stay coordinated for a solo maintainer, per Codex review).

- [ ] **Step 2: `0002-application-boundaries.md`** — Status: Accepted.
  Decision: web/api/desktop are independently deployable units communicating
  only through the published API contract; workers (when they exist) are a
  backend deployment component, not a fourth product application; no shared
  DB access between web/desktop and the API. Source: `Initial Docs/08_SYSTEM_ARCHITECTURE.md`.

- [ ] **Step 3: `0003-stack-choices.md`** — Status: mixed.
  - Backend: FastAPI + PostgreSQL + Alembic — **Proposed** (matches former
    candidate per `17_GREENFIELD_SETUP.md`; not yet implemented beyond the
    `/health` skeleton, no DB wired up this session).
  - Redis/ARQ job queue — **Deferred** until a real job/analysis slice needs
    it (Phase 4 per roadmap).
  - Frontend: React + Vite + TypeScript — **Accepted**, scaffolded this
    session.
  - Desktop: Tauri 2 + Rust — **Proposed**, not scaffolded this session (see
    `apps/desktop/README.md`).
  - Package management: pnpm (JS), uv (Python) — **Accepted**, both already
    available locally and used in this session's scaffold.

- [ ] **Step 4: `0004-contract-strategy.md`** — Status: Proposed (not yet
  implemented — no contract exists to generate from yet). Decision on paper:
  OpenAPI 3.1-first under `docs/contracts/openapi/`, versioned at `/api/v1`,
  RFC 9457 problem details, idempotency keys for retryable mutations,
  opaque cursor pagination, explicit entity versions/ETags for optimistic
  concurrency. Source: `Initial Docs/08_SYSTEM_ARCHITECTURE.md` + Codex
  planning review (this session).

- [ ] **Step 5: `0005-testing-strategy.md`** — Status: Accepted for what's
  scaffolded, Proposed for future layers. This session: `pytest` for API
  (`apps/api/tests/test_health.py`), `vitest` + Testing Library for web
  (`apps/web/src/App.test.tsx`). Future/proposed: Postgres-backed
  integration + migration-upgrade tests for the API once a DB exists;
  contract-conformance tests once OpenAPI exists; thin cross-unit E2E per
  vertical slice (not before real slices exist, per
  `Initial Docs/10_IMPLEMENTATION_PLAN.md`).

- [ ] **Step 6: `0006-local-development.md`** — Status: Accepted.
  Decision: `pnpm install` at root for JS deps; `cd apps/api && uv sync` for
  Python deps; root `package.json` scripts (`format`/`lint`/`typecheck`/`test`/`build`)
  fan out to both apps. No Docker Compose this session (deferred — no
  backend service worth containerizing yet).

- [ ] **Step 7: Commit**

```bash
git add docs/architecture
git commit -m "docs: add Session 1 architecture decision records"
```

---

### Task 7: Operating documents

**Files:**
- Create: `CLAUDE.md`
- Create: `.claude/rules/pulse-operating-contract.md`

- [ ] **Step 1: Write compact `CLAUDE.md`**

```markdown
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

## Commands
`pnpm install`, `pnpm format`, `pnpm lint`, `pnpm typecheck`, `pnpm test`,
`pnpm build` from repo root. See root `README.md`.
```

- [ ] **Step 2: Write `.claude/rules/pulse-operating-contract.md`**

```markdown
# Pulse Operating Contract

Binding execution workflow. Source: `Initial Docs/13_CLAUDE_CODEX_WORKFLOW.md`,
`14_DELIVERY_AND_REPORTING.md`, `15_IMMUTABLE_GUARDRAILS.md`.

## Authority order
1. User's newest explicit instruction.
2. `Initial Docs/15_IMMUTABLE_GUARDRAILS.md`.
3. Canonical product/UX/design specs.
4. Accepted ADRs.
5. Current milestone contracts/tests.
6. Legacy/historical info — non-binding context only.

## Claude vs Codex authority
- **Claude leads:** UI direction/fidelity, design tokens/typography/materials/
  layout/motion, component composition, screenshot/visual QA, UX copy.
- **Codex leads:** backend, data models, migrations, APIs, contract design,
  analysis/job infra, adapters/sync, Tauri/native non-visual behavior,
  security/reliability/non-visual verification.
- Every milestone requires joint participation: planning/contracts review,
  implementation (each in their lane), integration review, final
  verification (Claude signs off visual fidelity, Codex signs off
  runtime/data correctness). Mentioning Codex without an actual recorded
  task/result/verification is invalid.

## Atomic session limits
- One primary objective, max 2–3 deliverables per session.
- No giant multi-phase sessions.
- Explicit exclusions stated up front.

## Skill invocation
- Inspect each skill's current `SKILL.md` before using it — installed does
  not mean active or unchanged.
- Use only the smallest relevant set for the current phase; never invoke
  every installed skill as ritual.
- Record: skills invoked + concrete action each governed; skills considered
  but omitted and why; conflicts and which instruction won.

## Collision avoidance
- Assign file ownership before concurrent Claude/Codex work.
- No simultaneous edits to the same files.
- Use handoff artifacts for cross-agent work; small commits with tests.

## Truthfulness
- No mock data presented as connected production data.
- Unsupported fields/capabilities use honest unavailable states, never fake
  success.
- Legacy code/docs are evidence only, never product authority.

## Evidence and completion gate
- Never claim "complete"/"working"/"passed" from inference — run fresh
  commands and cite output.
- Every session produces: a dated report in `docs/session-reports/`, an
  updated `docs/LATEST_SESSION_REPORT.md` pointer, and a handoff in
  `.claude/handoffs/` when work continues into a next session.
- A milestone is not complete if: a required agent didn't participate
  without valid justification, mandatory relevant skills were skipped,
  contracts/tests/visual evidence are missing, connected UI uses fabricated
  state, or the report/handoff/pointer wasn't updated.
```

- [ ] **Step 3: Commit**

```bash
git add CLAUDE.md .claude/rules
git commit -m "docs: add CLAUDE.md and Pulse operating contract"
```

---

### Task 8: Session report, Codex handoff, latest pointer

**Files:**
- Create: `docs/session-reports/2026-07-23-session1-foundation.md`
- Create: `.claude/handoffs/2026-07-23-session2-library-selector-planning.md`
- Create: `docs/LATEST_SESSION_REPORT.md`

- [ ] **Step 1: Write the session report** using the template from
  `Initial Docs/14_DELIVERY_AND_REPORTING.md` (Objective / Scope completed /
  Explicitly not completed / Decisions made / Files changed / Contracts
  changed / Tests and commands / Visual evidence / Skills invoked / Claude
  participation / Codex participation / Risks / Commits / Next atomic
  session). Populate every section with the real content from this session
  — exact commands run, exact test output counts, the actual Codex task and
  its returned recommendations, the injected-instruction incident and its
  cleanup, and the real commit hashes (get them with `git log --oneline`
  after Task 9).

- [ ] **Step 2: Write the Codex handoff** for Session 2, stating: repo root
  `/Users/ermegarcia/Documents/Claude Projects/Pulse`, branch `main`,
  starting state (Session 1 foundation merged), objective (Library
  Selector + active-Library shell **planning/contracts only**, not
  implementation), owned/protected files (none yet — no concurrent edits
  needed until real endpoints exist), required reading (`05_CANONICAL_UX_SPEC.md`,
  `06_SCREEN_AND_FLOW_SPEC.md`, `08_SYSTEM_ARCHITECTURE.md`, ADR 0002/0004),
  acceptance criteria, verification commands, known blockers (none), what
  not to do (no Library UI implementation, no Dashboard, no other excluded
  Session-1-adjacent scope).

- [ ] **Step 3: Write `docs/LATEST_SESSION_REPORT.md`**

```markdown
# Latest Session Report

Points to: `docs/session-reports/2026-07-23-session1-foundation.md`
```

- [ ] **Step 4: Commit**

```bash
git add docs/session-reports docs/LATEST_SESSION_REPORT.md .claude/handoffs
git commit -m "docs: add Session 1 report, Codex handoff, and latest-report pointer"
```

---

### Task 9: Final verification pass

- [ ] **Step 1: Run every documented command from a clean state**

```bash
cd "/Users/ermegarcia/Documents/Claude Projects/Pulse"
pnpm install
pnpm format
pnpm lint
pnpm typecheck
pnpm test
pnpm build
```

Expected: every command exits 0. Record actual output/counts in the
session report (Task 8, Step 1) — do not write "tests pass" without citing
the real pytest/vitest summary lines.

- [ ] **Step 2: Confirm git history is coherent**

```bash
git log --oneline
git status
```

Expected: clean tree, sequence of small coherent commits matching Task 1–8.

- [ ] **Step 3: Request Codex's final non-visual review** — bounded,
  read-only task: point Codex at the repo root, ask it to verify the
  scaffold matches the ADRs (no scope creep, no mock data, boundaries
  respected) and that `apps/api`/`apps/web` commands are real (not stubbed
  to always pass). Capture the verbatim result in the session report.

- [ ] **Step 4: Resolve any valid Codex findings and re-run affected
  checks from Step 1.**
</content>
