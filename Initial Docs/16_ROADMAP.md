# Product Roadmap

## Milestone sequence

| Milestone | User value | Exit proof |
| --- | --- | --- |
| M0 Foundation | Trustworthy project workflow | ADRs, CI, operating contract |
| M1 Libraries | Enter an isolated workspace | Two-Library isolation |
| M2 Real catalog | See actual tracks and availability | Real ingest and table |
| M3 Prepare a track | Play and edit safely | Local playback + save modes |
| M4 Analyze | Obtain explainable results | Real job and provenance |
| M5 Review | Resolve uncertainty | One end-to-end queue |
| M6 Organize | Build crates and views | Manual/smart crates |
| M7 Dashboard | See actionable state | Real modular overview |
| M8 Find and operate | Search and monitor work | Search + separate centers |
| M9 Integrate | Move preparation to DJ software | Validated adapter round trip |
| M10 Harden | Operate reliably | backup, recovery, performance, a11y |

## Prioritization rule

Prefer the smallest milestone that closes a complete user loop. Backend breadth without user value and visual breadth without real contracts are both incomplete.

## Release gates

### Alpha

- One user, one Mac, one backend.
- Library selection, real ingest, tracks, local playback, core edits, one analyzer, one review queue.

### Beta

- Crates, Dashboard, search, operational centers, first adapter, robust onboarding, backup/recovery.

### V1

- Stable daily use on the target deployment.
- Proven performance on the user's realistic catalog size.
- Adapter round-trip confidence.
- Accessibility and degraded-mode coverage.
- Migration and support documentation.

## Deferred candidates

- Additional adapters after the first is stable.
- Broader offline mutation queue.
- Mobile companion.
- Collaborative/multi-user workflows beyond foundational authorization.
- Advanced recommendation/mix planning.
- Playback telemetry.
- Automatic background sync.

Deferred does not mean rejected; it prevents premature architecture and scope expansion.

