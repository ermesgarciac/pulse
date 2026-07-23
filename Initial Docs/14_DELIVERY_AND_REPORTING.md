# Delivery and Reporting Contract

## Required repository documents

- `CLAUDE.md`: concise project rules and pointers.
- `.claude/rules/pulse-operating-contract.md`: binding execution workflow.
- `docs/architecture/adr/`: accepted technical decisions.
- `docs/contracts/`: current product/API/runtime contracts.
- `docs/design/`: canonical screen, state, and visual specifications.
- `docs/session-reports/`: immutable dated reports.
- `.claude/handoffs/`: current bounded handoffs.
- `docs/LATEST_SESSION_REPORT.md`: pointer to the newest report.

## Session report template

```md
# Pulse Session Report — YYYY-MM-DD HHMM — short-name

## Objective
## Scope completed
## Explicitly not completed
## Decisions made
## Files changed
## Contracts changed
## Tests and commands
## Visual evidence
## Skills invoked
## Claude participation
## Codex participation
## Risks / known gaps
## Commit(s)
## Next atomic session
```

## Evidence rules

- List exact commands and outcomes; do not say “tests pass” without naming them.
- UI completion requires screenshots for relevant states and sizes.
- Contract completion requires generated schema/diff plus tests.
- Runtime work requires real-environment or clearly labeled simulated verification.
- Record unavailable dependencies without substituting fake success.

## Commit rules

- Small, coherent commits.
- Separate mechanical/generated changes when useful.
- Do not mix unrelated cleanup.
- Never rewrite or discard user changes.
- Reports name the exact commits they describe.

## Handoff rules

A handoff states:

- Current branch/worktree/repository.
- Exact starting state.
- One objective.
- Owned and protected files.
- Required reading.
- Acceptance criteria.
- Commands to verify.
- Known blockers.
- What not to do.

## Decision management

- Canonical product changes require explicit user approval.
- Technical choices with meaningful consequences use ADRs.
- Temporary implementation compromises are labeled with owner and removal condition.
- Unknowns are not quietly converted into defaults.

