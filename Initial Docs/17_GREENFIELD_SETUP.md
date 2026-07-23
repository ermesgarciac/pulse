# Greenfield Setup — No Existing Project

## Starting condition

The former Pulse project was deleted completely from the user's Mac. There is no repository, worktree, branch, code, dependency lockfile, Docker configuration, Claude configuration, Codex handoff, or reusable local project artifact.

This is intentional. Do not begin with recovery work.

## User-side folder setup

Create a new parent folder named `Pulse`, place the entire `PULSE_CLAUDE_REBOOT` folder inside it, and open the parent `Pulse` folder in VS Code/Claude Code.

Initial state:

```text
Pulse/
└── PULSE_CLAUDE_REBOOT/
    ├── 00_START_HERE.md
    ├── ...
    └── CLAUDE_BOOTSTRAP_PROMPT.md
```

Then paste the contents of `CLAUDE_BOOTSTRAP_PROMPT.md` into a new Claude Code session.

## What Claude creates in Session 1

Claude, with Codex review, must create only the foundation agreed in the bootstrap prompt. The intended documentation skeleton is:

```text
Pulse/
├── .claude/
│   ├── handoffs/
│   └── rules/
│       └── pulse-operating-contract.md
├── docs/
│   ├── architecture/
│   │   └── adr/
│   ├── contracts/
│   ├── design/
│   ├── session-reports/
│   └── LATEST_SESSION_REPORT.md
├── PULSE_CLAUDE_REBOOT/
├── CLAUDE.md
├── README.md
└── project/workspace files selected by accepted ADRs
```

The exact application folders and stack are decided through ADRs in the first session. Do not pre-create a monorepo structure that prejudges those decisions.

## Required Session 1 decisions

- Repository/workspace layout.
- Frontend technology and shared UI strategy.
- Backend language/framework.
- Desktop host/runtime strategy for macOS.
- Package/dependency management.
- Test layers and commands.
- Local development orchestration.
- Contract-generation strategy.
- Formatting, linting, and type checking.

The former FastAPI/PostgreSQL/Redis/ARQ/Alembic approach is a candidate, not a requirement. The decision must be grounded in the current product and operational target.

## Claude–Codex bootstrap

Before implementation:

1. Claude summarizes the canonical product and proposes the bounded foundation scope.
2. Codex reviews architecture, contracts, backend/runtime boundaries, testing, and repository risks.
3. Claude reconciles the review and records decisions as ADRs.
4. File ownership is assigned before concurrent edits.
5. Both agents verify the finished foundation.

The first session is invalid if Codex is only mentioned in a report but never actually participates.

## Persistent project memory

`CLAUDE.md` should be compact and point to canonical sources instead of duplicating the entire specification. The operating contract must preserve:

- Product authority order.
- Immutable guardrails.
- Claude and Codex authority.
- Required joint checkpoints.
- Atomic session limits.
- Skill invocation and reporting.
- Contract/data truthfulness.
- Testing and visual evidence.
- Session report, handoff, and latest-pointer rules.

## First commit sequence

A sensible sequence is:

1. `docs: add canonical Pulse reboot package`
2. `chore: initialize Pulse workspace foundation`
3. `docs: add architecture decisions and operating contract`
4. `docs: add initial session report and handoff`

Claude may choose a slightly different coherent sequence, but must not create one enormous commit containing unrelated generated files and speculative features.

## “Day zero” completion checklist

- New Git repository exists.
- Canonical package is committed.
- Development checks are documented and executable.
- Claude operating files exist.
- Codex participation is real and recorded.
- ADRs capture meaningful stack choices.
- No feature implementation or fake API was added.
- First report and next atomic handoff exist.
- The next session is Library Selector + Library shell planning/contracts, not a broad app build.

## What not to recreate

- Old worktree paths.
- Old branches or commit hashes.
- Old recovery orchestration.
- Old generated OpenAPI schemas.
- Old migrations.
- Old dashboards or mock-connected fields.
- Any tool wrapper merely because the previous attempt used it.

