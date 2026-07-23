# Screen and Flow Specification

## 1. Library Selector

**Purpose:** choose the isolated workspace before entering.

**Content:** Library cards/rows, health, last opened, location summary, create/import action, connection warnings.

**Key states:** first run, healthy, backend unavailable, storage unavailable, migration required, empty.

**Acceptance:** entering one Library never displays another Library's counts or resources.

## 2. Library Dashboard

**Purpose:** actionable overview and continuation.

**Modules:** continue preparation, review backlog, recent tracks, most played with period control, analysis/jobs, storage/availability, sync attention, Library health.

**Edit Dashboard:** enter an explicit edit mode; add/remove modules, reorder, resize where supported, reset, cancel, save. Layout is per user and per Library.

## 3. Tracks

**Purpose:** high-density catalog work.

**Layout:** toolbar, filters/chips, configurable table, optional inspector, persistent Media Engine.

**Core columns:** artwork/status, title, artist, mix/album, BPM, key, energy, rating/favorite, vocal, tags, duration, added/played, availability, review/sync.

**Behavior:** shift/range selection, command-toggle selection, keyboard navigation, column management, saved view state, bulk action preview.

## 4. Built-in Collections

Use the Tracks surface with a fixed semantic query and its own remembered view. Built-ins are not ordinary user-deletable crates.

## 5. Crates

**List:** manual and smart crates, counts, updated date, optional artwork mosaic.

**Manual crate:** add/remove membership, drag ordering, optional sort override, no audio duplication.

**Smart crate:** human-readable rule builder, live count, test results, explicit AND/OR grouping, invalid-rule explanation.

## 6. Track Workspace

**Sections:** Overview, Analysis, Cues & Structure, Metadata, Tags, Locations, Crates, History.

**Primary path:** select track → open/play → inspect evidence → edit → audition → save → optionally prepare sync.

**Protection:** dirty manual edits cannot disappear through an accidental selection change.

## 7. Review Center

**Queue rail:** Beatgrid/Key, Metadata, Duplicates, Artwork, Cues/Structure, Audio Quality, Missing Files, Sync Conflicts.

**Work area:** evidence, comparison, waveform/player where applicable, suggested resolution, confidence, source/provenance.

**Actions:** accept, edit, reject, skip, defer, apply to safe batch, undo when supported.

## 8. Duplicate Resolution

Show why items match: checksum, acoustic similarity, metadata, duration, bitrate, location, modification time. Distinguish exact duplicate, alternate encoding, edit/version, and uncertain match. Never reduce duplicate resolution to “delete one.”

## 9. Jobs

Queue/running/completed/failed/cancelled states; type, scope, progress, timestamps, actionable failure. Job progress must come from real job contracts.

## 10. Activity

Chronological audit of user and system actions. Filters by actor, action, entity, integration, and outcome. Activity is not the Notification Center.

## 11. Notification Center

Attention-worthy, dismissible items with severity and deep link. Notification counts must not be fabricated from jobs or activity.

## 12. Global Search / Command Palette

Search tracks, crates, tags, views, settings, and actions inside the active Library. Support recent searches and keyboard commands. Until a real backend/index contract exists, use an honest unavailable state.

## 13. Integrations

Adapter cards show connection, capability, last import/export, pending changes, and errors. Adapter detail exposes read/write capability matrix and operation history.

## 14. Storage and Sources

Locations, runtime visibility, capacity where available, availability, scan controls, ignore rules, and safe removal. Clearly state whether the backend or desktop companion can access each source.

## 15. Settings

Library settings, analysis preferences, metadata behavior, save mode, playback, integrations, storage, appearance/accessibility, advanced/diagnostics. Keep global account preferences separate from Library settings.

## 16. Onboarding

Create/select Library → connect backend → install/connect desktop companion → choose sources → scan preview → ingest → first analysis → explain Review Center → enter Dashboard. Each step is skippable only when the product can remain coherent.

## 17. Offline and degraded mode

The shell remains navigable. Cached metadata is labeled. Local playback may continue through the desktop runtime. Server mutations queue only when conflict handling is defined; otherwise controls become disabled with explanation.

