# Product Requirements Document

## Scope

This PRD defines the target product. The implementation roadmap deliberately delivers it in narrow vertical slices.

## Functional requirements

### Libraries

- A Library is a top-level isolated environment.
- The user selects or creates a Library before entering it.
- Each Library owns tracks, assets, crates, tags, jobs, review queues, dashboard layout, notifications, integrations, storage, and settings.
- Switching Libraries occurs outside the internal Library sidebar.
- Cross-Library data must not leak into counts, search, playback, or activity.

### Tracks and assets

- Store musical identity separately from physical file locations.
- Support local Mac, external drive, NAS, and server-reachable locations.
- Expose availability and preferred playback asset.
- Provide list, detail, bulk selection, filtering, sorting, and reversible edits.
- Preserve raw/imported values and normalized/approved values.

### Collections and crates

- Built-ins: All Tracks, Recently Added, Recently Played, Unanalyzed, Favorites, Prepared Tracks.
- Manual crates do not duplicate audio.
- Smart crates use inspectable rules.
- Manual crate order and track order can be controlled.
- Each collection remembers its view configuration.

### Analysis and metadata

- BPM, key, loudness/audio quality, energy 1–10, vocal yes/no, mood, tags, structure, cues, and confidence where relevant.
- AI suggestions never overwrite approved values automatically.
- Maximum eight primary cue points for target DJ workflows.
- Analysis versions and provenance are retained.

### Media Engine

- Waveform is the central interaction.
- Clicking the waveform seeks.
- Cue points navigate immediately.
- Analysis panel is above the central waveform region.
- Mini Player lives at the bottom.
- Double-clicking a track opens and plays it.
- Selecting another track replaces current playback unless manual-save mode has unsaved edits, in which case Pulse protects the edit.

### Editing

- On the first meaningful edit, ask whether to autosave or require manual save.
- Offer “remember my choice.”
- Save and Sync remain different operations.
- Dirty, saving, saved, conflict, and sync-pending are visually distinct.

### Review Center

- Queues for uncertain beatgrid/key, metadata issues, duplicates, artwork, suggested cues/structure, audio quality, missing assets, and sync conflicts.
- Explain why each item is present.
- Support audition, compare, accept, reject, skip, and bulk action where safe.

### Dashboard

- Entry point after opening a Library.
- Modular and editable per user.
- Includes useful summaries and actions, not decorative analytics.
- Most Played supports selectable periods.
- Modules link directly to the relevant work.
- Dashboard is one view inside the Music Workspace, not the product identity.

### Search and commands

- Global search is accessible from anywhere inside a Library.
- Results are grouped by type and scoped to the active Library.
- Keyboard-first command access for navigation and actions.
- Search must not be represented as connected until a real contract exists.

### Jobs, activity, notifications, and status

- Jobs show work currently running or queued.
- Activity is an audit/history stream.
- Notifications are user-attention messages.
- Status represents Library/system health.
- These concepts must remain separate in data and UI.

### Integrations

- Architect adapters for Traktor, Rekordbox, Serato, VirtualDJ, and CDJ-oriented exports.
- Begin with a single adapter after core identity and editing are trustworthy.
- Capability matrices define what each adapter can read/write.
- No universal-sync abstraction that hides destination differences.

## Non-functional requirements

- Docker-first backend on Proxmox.
- Frontend and backend fully separated.
- Native macOS desktop companion for local filesystem, playback, DJ databases, USB/external drives, and progressive offline behavior.
- API contracts versioned and testable.
- Responsive for supported desktop window sizes.
- Keyboard navigation and screen-reader semantics.
- No secrets in source or reports.
- Observability, migrations, backup/restore guidance, and safe failure states.

## Acceptance outcomes

A first useful release must let a user create/select a Library, ingest real tracks through the appropriate runtime, browse and search them, play an available local track on Mac, inspect/edit core metadata, save changes, run at least one real analysis job, and resolve at least one Review Center category without mock data.

