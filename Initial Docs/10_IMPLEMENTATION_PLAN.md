# Implementation Plan

## Strategy

Build thin, real vertical slices. Do not construct the entire backend and then a disconnected visual shell. Each slice must include contracts, state, UI, failure states, tests, and verification.

## Phase 0 — Decision and repository foundation

Deliverables:

- Repository scaffold and development commands.
- Architecture/stack ADRs.
- Persistent operating contract for Claude–Codex collaboration.

Exit: clean build/test/lint pipelines run locally; no feature UI.

## Phase 1 — Library selection and shell

Deliverables:

- Real Library create/list/select contract.
- Library selector and active-Library shell.
- Isolation/authorization tests.

Exit: two seeded Libraries prove complete UI/data isolation; no internal “Libraries” sidebar item.

## Phase 2 — Track identity and ingest

Deliverables:

- Track/asset/location model and one real ingest path.
- Track table with honest states.
- Availability and provenance tests.

Exit: real user-approved files appear with stable identities and no mock rows.

## Phase 3 — Playback and Track Workspace core

Deliverables:

- Desktop local playback for a selected available asset.
- Track Workspace identity/metadata editing.
- Autosave/manual-save preference and dirty protection.

Exit: select, play, edit, save, close, and return to preserved list context.

## Phase 4 — Analysis and jobs

Deliverables:

- One real analyzer pipeline.
- Job progress/error contracts.
- Analysis display with provenance.

Exit: run analysis on real tracks and observe accurate lifecycle.

## Phase 5 — Review Center first queue

Deliverables:

- Review Issue domain.
- One high-value real queue.
- Accept/edit/reject resolution history.

Exit: issue creation through resolution is tested end-to-end.

## Phase 6 — Organization

Deliverables:

- Manual crates with ordering.
- Smart-crate rule builder.
- Built-in collections and remembered views.

Exit: organization never duplicates audio and rules are explainable.

## Phase 7 — Dashboard

Deliverables:

- Actionable modules based on existing real contracts.
- Edit Dashboard per Library/user.
- Health/status semantics.

Exit: every visible value has a contract owner and every module leads to work.

## Phase 8 — Search and operational centers

Deliverables:

- Real Library-scoped search.
- Separate Jobs, Activity, Notifications, and Status surfaces.
- Keyboard command access.

Exit: semantics and counts are not conflated.

## Phase 9 — First DJ adapter

Deliverables:

- Capability matrix and import.
- Previewable export/sync plan.
- Conflict and partial-result handling.

Exit: a verified, reversible real-world round trip for the selected adapter.

## Implementation rules

- A milestone may be split further; it must not be expanded casually.
- Database/API and visual work meet at written contracts.
- Use fixtures only in tests/story environments clearly labeled as such.
- Feature flags may hide incomplete real work; they may not disguise mocks as production.
- Do not optimize for screenshot appearance at the cost of state correctness.

