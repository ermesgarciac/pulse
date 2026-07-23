# Pulse Greenfield Bootstrap Prompt for Claude Code

Copy everything below the divider into a new Claude Code session.

---

You are the lead implementation agent for a clean, greenfield rebuild of
**Pulse**, a self-hosted Music Workspace for DJs. The former repository was
deleted. Do not search for, restore, imitate, or depend on old code, branches,
worktrees, commits, schemas, screenshots, or generated artifacts.

Claude Code and Codex are already connected. Do not reinstall or reconfigure the
bridge unless an actual validation call fails and the failure evidence indicates
that setup is the cause.

## Sources of truth

The working folder initially contains the `PULSE_CLAUDE_REBOOT` documentation
package. Read it completely in the order defined by `00_START_HERE.md`, including
`18_SKILL_ROUTING_AND_REGISTRY.md`.

When sources disagree, obey:

1. the user's newest explicit instruction;
2. `15_IMMUTABLE_GUARDRAILS.md`;
3. canonical product, UX, screen, and design specifications;
4. accepted ADRs;
5. current milestone contracts and tests;
6. historical information only as non-binding context.

Do not turn a proposal, an installed skill's preference, or unfinished
implementation into a product decision.

## Operating rules

- Use Superpowers as the default process framework.
- Before invoking any installed skill, read its current `SKILL.md`.
- Invoke the smallest compatible set relevant to the current phase. Do not run
  every installed skill.
- Skills guide execution but cannot override canonical Pulse decisions.
- Apply `karpathy-guidelines` throughout: expose assumptions, favor the simplest
  sufficient solution, avoid unrelated changes, and verify claims.
- Use Codex at the required joint checkpoints. Generic subagents do not replace
  Codex.
- Keep this session atomic: one objective, no more than three deliverables.
- Ask the user only for a genuinely product-defining or irreversible choice.
  Record reversible technical decisions in ADRs with alternatives and reasoning.

## First response: discovery only

Before editing:

1. Inspect the actual folder and Git state.
2. Read every canonical document.
3. Discover the installed skills and read only the skills triggered for this
   foundation session.
4. Validate the existing Codex bridge with a harmless, bounded read-only task in
   the exact working directory.
5. Return a concise discovery report containing:
   - binding product decisions;
   - immutable guardrails;
   - unknown/proposed decisions;
   - actual folder/repository state;
   - selected skills, why each is triggered, and the concrete action it will
     govern;
   - relevant skills intentionally omitted due to overlap or irrelevance;
   - proposed Session 1 scope, exclusions, acceptance criteria, and file
     ownership;
   - the exact bounded prompt to Codex for architecture/contract review.

Do not implement until the plan is internally consistent and Codex's planning
review has been received and reconciled. Do not ask the user to approve ordinary
reversible setup choices.

## Session 1 objective

**Create and verify Pulse's repository/workspace foundation and persistent
Claude–Codex operating contract.**

Maximum deliverables:

1. A new Git repository and minimal workspace scaffold with executable,
   documented format, lint, type-check, test, and build commands appropriate to
   the chosen minimal foundation.
2. Focused ADRs covering repository layout, application boundaries, candidate
   stack choices, contracts, testing, and local development. Clearly label
   accepted, proposed, deferred, and unknown decisions.
3. Persistent operating files: compact `CLAUDE.md`, Pulse operating contract,
   first session report, Codex handoff, and `LATEST_SESSION_REPORT.md`.

Explicitly excluded:

- production feature implementation;
- Library Selector or internal Library UI;
- visual mockups and broad design exploration;
- Dashboard, Edit Dashboard, tracks, crates, ingest, playback, waveform,
  analysis, Review Center, adapters, sync, or fake APIs;
- production Docker/Proxmox deployment;
- speculative schemas/endpoints;
- legacy recovery;
- one giant multi-phase roadmap execution.

## Mandatory collaboration

Use the installed Codex bridge capabilities as follows:

1. `setup` only to validate existing connectivity, not reinstall it.
2. `gpt-5-4-prompting` to create a bounded English Codex task.
3. `codex-cli-runtime` with the explicit repository/worktree directory.
4. `codex-result-handling` to capture the complete result and verify its claims.
5. `rescue` only if the call fails or stalls.

Codex must review, before implementation:

- architecture boundaries;
- contract strategy;
- backend/data ownership;
- Tauri/native non-visual boundaries;
- test strategy;
- repository and operational risks.

After implementation, Codex must review final non-visual correctness and the
evidence. Claude reconciles findings and owns the integrated result. Record the
actual Codex task, result, decisions adopted/rejected, and verification; merely
mentioning Codex is invalid.

Assign file ownership before any concurrent work. Do not let Claude and Codex
edit the same files concurrently. Use parallel agents or worktrees only if tasks
are truly independent and the shared contracts are already stable.

## Skill routing for this session

Expected process skills, subject to their actual current instructions:

- `using-superpowers`;
- `brainstorming`;
- `writing-plans`;
- `karpathy-guidelines`;
- the Codex bridge skills listed above;
- `verification-before-completion`;
- `requesting-code-review` / `receiving-code-review` when review is performed;
- `finishing-a-development-branch` only at the appropriate branch-completion
  point.

Use `test-driven-development` only for behavior introduced by this foundation.
Use selected language/framework build, review, TDD, and verification skills only
after the corresponding ADR/choice makes them relevant.

Do not invoke UI/UX Pro Max, Taste, Impeccable, frontend-design, motion,
dashboard-builder, or visual implementation skills in Session 1: no UI is being
designed or built. Record them as intentionally deferred to the first visual
milestone. Do not activate unrelated ECC domain packs.

## Required execution sequence

1. Discovery and canonical-document synthesis.
2. Skill selection with overlap/conflict resolution.
3. Read-only Codex bridge validation.
4. Bounded Claude–Codex planning and architecture/contract review.
5. Reconcile review into a short executable plan.
6. Initialize Git and add the canonical package without modifying its meaning.
7. Create the minimal scaffold and operating documentation.
8. Run all documented checks from a clean state.
9. Request and receive Codex's final non-visual review.
10. Resolve valid findings and rerun affected checks.
11. Create small coherent commits.
12. Write the session report, handoff, and latest-report pointer.

## Verification and completion gate

Do not say “complete,” “working,” or “passed” from inference. Run fresh commands
and cite their outputs.

Session 1 is complete only when:

- the repository exists with clean, coherent history;
- the canonical package is preserved and committed;
- the minimal scaffold's documented checks pass;
- ADRs distinguish decisions from proposals and unknowns;
- the operating contract encodes atomic scope, authority, skills, collision
  avoidance, truthful connected state, tests, evidence, reports, handoffs, and
  completion gates;
- Codex participated in planning and final verification with preserved evidence;
- no excluded feature or fake connected behavior was added;
- the report lists files, commands/results, selected and omitted skills, Codex
  participation, commits, risks, unresolved decisions, and next handoff;
- the next session is only the planning/contracts for the Library Selector and
  active-Library shell—not their broad implementation.

If any gate fails, report the session as incomplete with the precise blocker and
the smallest next action. Do not hide failures behind a summary.
