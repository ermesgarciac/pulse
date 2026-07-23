# Recurrence and Maintenance Plan

## Purpose

Pulse should keep a Library healthy without becoming noisy or making hidden changes.

## Recurring activities

| Activity | Default trigger | Output |
| --- | --- | --- |
| Source availability scan | On mount/connect plus scheduled | Availability changes |
| Incremental ingest | Source change or manual scan | New/changed asset candidates |
| Analysis | After approved ingest | Versioned results/jobs |
| Review prioritization | After new findings | Ranked queue |
| Duplicate detection | After ingest/analysis | Explainable candidates |
| Integration drift check | Manual initially | Proposed sync differences |
| Database maintenance | Scheduled operations | Health/result log |
| Backup verification | Scheduled operations | Verified/failed status |

Exact schedules are deployment preferences, not hardcoded product assumptions.

## Notification policy

Notify only when:

- User action is required.
- A meaningful operation completed or partially failed.
- A source/integration changed health materially.
- Risk is time-sensitive.

Do not notify for normal successful background scans with no meaningful changes.

## Recurrence safeguards

- Jobs are idempotent or deduplicated.
- Per-Library concurrency limits prevent storms.
- Mount/NAS sleep windows do not become false missing-file incidents.
- Backoff and retry are bounded.
- Every recurrent rule can be paused and inspected.
- A recurring task may propose a change; destructive application still requires explicit policy/approval.

## Review backlog hygiene

- Collapse repeated evidence into one issue.
- Reopen resolved issues only when material evidence changes.
- Allow snooze/defer with reason.
- Track aging and impact without gamifying the workspace.

## Operational review cadence

- Per release: migrations, backup/restore, adapter compatibility, accessibility, and performance.
- Per milestone: contract ownership and mock-data audit.
- Periodically: analyzer/model-version drift and reanalysis policy.
- Before adapter updates: destination-version compatibility and round-trip tests.

