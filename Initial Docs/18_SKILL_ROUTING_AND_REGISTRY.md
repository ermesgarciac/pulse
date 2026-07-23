# Pulse Skill Routing and Registry

## Principle

Installed does not mean active. Claude must inspect the current `SKILL.md` before
invoking a skill because plugin instructions can change. Use the smallest
compatible set that fully covers the current atomic session. Never invoke every
installed skill as a ritual.

For every session, record:

- skills considered;
- skills invoked and the concrete action each one changed;
- skills intentionally omitted due to irrelevance or overlap;
- any conflict and which instruction won;
- verification evidence produced by the selected skills.

## Precedence

1. User's latest instruction and canonical Pulse documentation.
2. Safety and repository rules.
3. The active milestone's accepted plan and contracts.
4. Language/framework-specific build, TDD, security, and verification skills.
5. General process skills.
6. Visual inspiration and taste guidance.

No skill may override a canonical Pulse product or UX decision.

## Default workflow stack

Use these process capabilities when their trigger applies:

| Moment | Primary skill | Purpose |
| --- | --- | --- |
| New product/UX uncertainty | `brainstorming` | Clarify intent, constraints, alternatives, and acceptance criteria before implementation. |
| Non-trivial scoped work | `writing-plans` | Produce an executable, bounded plan with files, tests, and checkpoints. |
| Plan already accepted | `executing-plans` | Execute the accepted plan without silently expanding it. |
| Behavior change or bug fix | `test-driven-development` | Establish a failing test, implement minimally, then refactor. |
| Unexpected failure | `systematic-debugging` | Reproduce, gather evidence, isolate cause, then fix. |
| Before claiming success | `verification-before-completion` | Run fresh checks and cite actual outputs. |
| Review needed | `requesting-code-review` | Ask a reviewer with scope, contracts, diff, and risks. |
| Review received | `receiving-code-review` | Validate feedback technically before applying it. |
| Branch is complete | `finishing-a-development-branch` | Reconcile, verify, report, and choose the correct integration path. |
| Isolated concurrent work | `using-git-worktrees` | Create collision-safe worktrees with explicit ownership. |

`using-superpowers` is the router for the Superpowers pack. `writing-skills` is
only for creating or changing skills, not for normal Pulse implementation.

## Parallel and subagent skills

- `dispatching-parallel-agents`: use only for independent tasks with disjoint
  file ownership and no unresolved shared contract.
- `subagent-driven-development`: use only when an accepted plan can be split
  into bounded implementation tasks followed by review.
- Do not use either during initial product decisions, shared schema design,
  design-token selection, or edits to the same files.
- Claude remains responsible for integrating and verifying all delegated work.
- Codex participation is mandatory under `13_CLAUDE_CODEX_WORKFLOW.md`; generic
  subagents do not replace Codex's authority.

## Codex bridge

| Capability | Use in Pulse |
| --- | --- |
| `setup` | Confirm the already-connected Claude–Codex bridge and working directory; do not reinstall it without evidence of failure. |
| `codex-cli-runtime` | Run a fresh, bounded Codex task in the explicit repository/worktree. |
| `gpt-5-4-prompting` | Shape precise Codex prompts with objective, authority, scope, exclusions, inputs, and required evidence. |
| `codex-result-handling` | Capture Codex output, validate claims, preserve handoffs, and prevent “Codex participated” from becoming an unsupported statement. |
| `rescue` | Diagnose a failed/stalled bridge call or malformed result; not a normal workflow step. |

Every Codex task must state the exact working directory, role, editable files,
read-only files, objective, exclusions, checks, and expected report. Never
delegate an open-ended “build Pulse” task.

## Visual/UI chain

These skills overlap, so use them sequentially with distinct responsibilities:

1. `frontend-design-direction` or the pack's `frontend-design`: choose a clear
   screen-level visual direction grounded in Pulse's canonical design.
2. `ui-ux-pro-max`: query relevant styles, palettes, type, interaction and
   accessibility guidance; produce design-system recommendations, not product
   requirements.
3. `design-system`: encode approved tokens, primitives, component states, and
   governance.
4. `motion-foundations` then `motion-patterns` (and `motion-advanced` only when
   genuinely necessary): define motion semantics and reduced-motion behavior.
5. Framework implementation skills such as `react`, `typescript`,
   `react-build`, and their TDD/verification variants.
6. `frontend-a11y` / `accessibility`: audit keyboard use, focus, semantics,
   contrast, motion, and assistive technology.
7. `impeccable`: critique and polish an already functional UI against common
   AI-design failure modes.

Taste pack routing:

- `taste-skill` / `gpt-tasteskill`: broad aesthetic judgment and anti-generic
  guidance. Use one as a direction aid, not both by default.
- `minimalist`, `soft`, `brandkit`, `brutalist`: optional aesthetic lenses.
  Pulse normally favors `minimalist` and restrained `soft`; `brutalist` is not
  canonical unless the user changes direction.
- `image-to-code`: use only when a real approved reference image is an input.
- `imagegen-frontend-web` / `imagegen-frontend-mobile`: use for exploratory
  bitmap references, never as the source of exact UI geometry or behavior.
- `redesign`: use for an existing screen that needs rethinking.
- `stitch`: use to reconcile multiple coherent visual artifacts.
- `output`: package a visual outcome according to that pack's instructions.
- `taste-skill-v1`: legacy alternative; do not combine with the current
  `taste-skill` unless its source explicitly requires it.

`impeccable-manual-edit-applier` is only for applying a deliberate Impeccable
manual edit set. It does not replace the critique or verification step.

## ECC technical routing

ECC is a large toolbox. Choose by touched subsystem:

| Family | When relevant |
| --- | --- |
| `typescript-*`, `react-*`, frontend build/review/TDD/verification | Pulse web UI, shared TypeScript packages, hooks, state, tests, and frontend build failures. |
| `python-*`, `fastapi-*` | Only if an ADR selects Python/FastAPI for services. |
| `rust-*` | Tauri/native desktop core, file access, local analysis/runtime, or Rust services. |
| `go-*`, `kotlin-*`, `java-*`, `swift-*`, `dart-flutter-*`, `cpp-*`, `csharp-*`, `fsharp-*`, `django-*`, `springboot-*`, `laravel-*`, `quarkus-*` | Only if that language/framework is actually selected or reviewed. Do not activate speculatively. |
| `docker-patterns`, `deployment-patterns` | Container topology, images, health checks, persistence, release/deploy design. |
| `database-migrations`, `postgres-patterns`, `redis-patterns` | Schema evolution, queries, persistence and queues/caching when selected. |
| `mysql-patterns`, `clickhouse-patterns` | Only if an ADR selects those systems. |
| `git-workflow`, `github-ops` | Branch/commit/review/release operations. |
| `terminal-ops`, `pm2` | Terminal/runtime operations; PM2 only if selected. |
| `code-review`, language reviewers | Adversarial correctness review after implementation. |
| `security-review`, `security-scan` | Trust boundaries, auth, uploads, filesystem, networking, secrets and dependency exposure. |
| Framework-specific security skills | Only for the chosen framework. |
| `cyber-neo` | Specialized security investigation; not a routine frontend skill. |

The DeFi, healthcare, homelab, BGP/network, trade/market, scientific, customs,
energy-procurement, marketing, SEO, social, investor, Jira, and other
domain-specific families are not part of Pulse's default workflow. Invoke one
only if a future atomic requirement genuinely enters that domain.

## ECC planning and agentic workflows

ECC contains several competing orchestration systems:

- `plan`, `plan-prd`, `plan-orchestrate`, `feature-dev`;
- `prp-plan`, `prp-implement`, `prp-commit`, `prp-pr`, `prp-prd`;
- `gan-build`, `gan-design`, `style-harness`;
- `multi-plan`, `multi-execute`, `multi-frontend`, `multi-backend`,
  `multi-workflow`;
- `santa-loop`, `loop-start`, `loop-status`, `autonomous-loops`,
  `continuous-agent-loop`;
- `harness-audit`, `quality-gate`.

Do not stack orchestration frameworks. Pulse defaults to Superpowers for
brainstorming/planning/execution/TDD/verification. Use an ECC orchestrator only
when the session explicitly adopts it and documents why it is a better fit.
Autonomous loops require a bounded stop condition, budget, file ownership, and
human-visible checkpoints. `quality-gate` and `harness-audit` may supplement
verification but cannot replace fresh project checks.

## ECC utility and configuration

- `resume-session`, `save-session`, `sessions`: context continuity.
- `compress`, Caveman `compress`, and Caveman mode: reduce context/token cost;
  never compress away acceptance criteria, failures, contracts, or evidence.
- `cost-report`, `cost-tracking`, `token-budget-advisor`, `model-route`: cost
  and model governance, not product implementation.
- `learn`, `learn-eval`, `instinct-*`: capture and manage reusable learned
  patterns; never promote an inference into canonical product truth.
- `skill-create`, `skill-health`, `skill-scout`, `skill-stocktake`: manage the
  skill ecosystem; not normal milestone work.
- `hookify*`: create or manage hooks only with an explicit, reversible purpose.
- `update-codemaps`, `update-docs`: maintain maps/docs after verified changes.
- `repo-scan`: inventory an existing repository; in greenfield Session 1 it is
  useful only to establish the actual initial state.
- `update-config`, `keybindings-help`, `simplify`,
  `fewer-permission-prompts`, `loop`, `schedule`, `claude-api`: configuration
  or operational utilities. Use only on an explicit trigger.

## Other installed packs

- `karpathy-guidelines`: persistent behavioral guardrail—make assumptions
  explicit, prefer simple solutions, avoid unrelated changes, verify instead
  of bluffing.
- Caveman `caveman`, `cavecrew`, `caveman-commit`, `caveman-help`,
  `caveman-review`, `caveman-stats`, `compress`: mode-specific compact
  execution, crew orchestration, commit/review/help/stats, and compression.
  Do not combine `cavecrew` with another agent orchestration system.
- `artifact-design`, `artifact-capabilities`: design and choose the correct
  artifact form.
- `dataviz`: use for genuine quantitative relationships, not decorative
  dashboard charts.
- `dashboard-builder`: use only for Dashboard implementation after its product
  contracts and module rules are accepted.
- `ui-demo`: create bounded demonstrations, not production substitutes.
- `ui-to-vue`: irrelevant unless Vue is selected by ADR.
- `run`: execute the checks or workflow defined by its source; do not treat its
  name alone as evidence.

## Pulse phase matrix

| Phase | Required/likely | Conditional |
| --- | --- | --- |
| Session 1: foundation | `using-superpowers`, `brainstorming`, `writing-plans`, `karpathy-guidelines`, Codex bridge skills, `verification-before-completion` | `repo-scan`, `git-workflow`, selected stack review skills |
| Architecture/contracts | `brainstorming`, `writing-plans`, Codex bridge, `security-review`, `verification-before-completion` | selected language/framework, DB, migrations, Docker |
| UI direction/design system | `frontend-design-direction`, `ui-ux-pro-max`, `design-system`, `taste-skill`, `frontend-a11y`, Codex contract review | motion skills, `image-to-code`, `impeccable` after implementation |
| Feature implementation | `executing-plans`, `test-driven-development`, selected language/framework TDD/build, Codex participation, `verification-before-completion` | parallel agents/worktrees only for independent ownership |
| Bug fix | `systematic-debugging`, `test-driven-development`, relevant language skill, `verification-before-completion` | security review if trust boundary involved |
| Milestone close | `requesting-code-review`, `receiving-code-review`, `verification-before-completion`, `finishing-a-development-branch`, Codex final review | `impeccable` for visual work, security scan for exposed surfaces |

## Session report template

```md
## Skills

### Invoked
- `skill-name` — trigger; concrete action/result.

### Considered but omitted
- `skill-name/family` — irrelevant, redundant, conflicting, or deferred.

### Conflicts resolved
- Conflict, precedence applied, and resulting decision.

### Codex
- Task ID or handoff:
- Working directory:
- Scope/ownership:
- Result received:
- Claims independently verified:
```

