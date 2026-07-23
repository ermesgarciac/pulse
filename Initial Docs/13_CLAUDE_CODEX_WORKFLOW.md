# Claude–Codex Collaboration Workflow

## Authority

### Claude leads

- UI direction and fidelity.
- Design tokens, typography, materials, layout, motion.
- Component composition and screen-level interaction.
- Screenshot comparison and visual QA.
- User-facing copy and UX coherence.

### Codex leads

- Backend, data models, migrations, and APIs.
- Contract design and API client correctness.
- Analysis/job infrastructure.
- Adapters and sync logic.
- Tauri/native non-visual behavior and runtime integration.
- Security, reliability, and non-visual verification.

Neither role removes the need for joint review.

## Mandatory participation per milestone

1. **Planning and contracts:** both agents review boundaries, states, and ownership.
2. **Implementation:** Claude owns visual work; Codex implements/reviews non-visual work when applicable.
3. **Integration review:** both verify contract-to-UI behavior and failure states.
4. **Final verification:** Claude signs off visual fidelity; Codex signs off runtime/data correctness.

If Codex has no implementation task, it still participates in contract and final integration review unless a written, valid justification explains why the milestone is purely visual and contract-neutral.

## Session shape

- One primary objective.
- At most 2–3 concrete deliverables.
- Clear excluded scope.
- Explicit acceptance criteria.
- Short report and handoff.

Do not combine screenshots, broad fidelity work, Edit Dashboard, Docker, runtime, Codex integration, and polish into one giant 8–12 phase session.

## Collision avoidance

- Assign file ownership before edits.
- Avoid simultaneous edits to shared contracts.
- Use handoff artifacts for cross-agent work.
- Do not duplicate the same audit independently unless adversarial review is the point.
- Integrate in small commits with tests.

## Skills

Every session must:

- Identify relevant and mandatory skills for its phase.
- Invoke them, not merely mention them.
- Record which were used and why.
- Explain any mandatory-skill exception.

“Use every installed skill” is not the rule. Use all relevant/required skills; do not invoke irrelevant or contradictory ones.

## Completion gate

The milestone cannot be declared complete if:

- A required agent did not participate without valid justification.
- Mandatory relevant skills were skipped.
- Contracts, tests, or visual evidence are missing.
- Connected UI uses fabricated state.
- The report/handoff/latest pointer was not updated.

## Tooling note

The former workflow used `codex-companion.mjs task "<prompt>" --write`, required an explicit `cd` into the correct worktree, and avoided relying on `--resume`. For the clean reboot, preserve the lessons—explicit working directory, bounded prompts, fresh context, collision control—but do not hardcode the legacy worktree path or assume the old wrapper remains appropriate.

