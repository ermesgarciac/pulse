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
