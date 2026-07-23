# ADR-0001: Repository layout

**Status:** Accepted
**Date:** 2026-07-23

## Context
Session 1 must stand up a workspace foundation before any deployable unit's
internal structure is decided in detail. `Initial Docs/17_GREENFIELD_SETUP.md`
requires a repository/workspace layout decision but forbids pre-creating
structure that prejudges later choices.

## Decision
Single pnpm-workspace monorepo at the repository root:

```
Pulse/
├── apps/{web,api,desktop}
├── docs/architecture/adr/
├── docs/contracts/
├── docs/design/
├── docs/session-reports/
├── docs/LATEST_SESSION_REPORT.md
├── .claude/{rules,handoffs}/
├── Initial Docs/        # canonical reboot package, read-only
├── CLAUDE.md
└── README.md
```

## Alternatives considered
- **Polyrepo** (separate repos per app): rejected — contracts, dev commands,
  and coordinated releases span all three deployable units, and a solo
  maintainer benefits from one coordinated history (per Codex planning
  review, this session).

## Consequences
Contract changes, ADRs, and app code all version together. Each app remains
independently buildable/deployable (see ADR-0002); the monorepo does not
imply shared runtime coupling.
