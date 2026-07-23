# Domain and Feature Specification

## Core entities

### Library

Top-level isolation boundary. Owns settings and every workspace entity.

### Track

The conceptual musical item the user organizes and prepares. It may reference multiple Audio Assets.

### Audio Asset

A particular audio encoding/version with technical properties and one or more Locations.

### Location

A runtime-specific resolvable place: server path, NAS, Mac-local path, external volume, or adapter source. Availability is observed, not assumed.

### Metadata Value

Stores value, field, source, confidence when relevant, created/updated timestamps, and approval state. The model must distinguish imported, analyzed, suggested, and user-approved values.

### Cue

Typed, ordered preparation marker with timestamp, label/color, provenance, and destination mapping. Target primary-cue count is eight.

### Structure Segment

Time range such as intro, breakdown, buildup, drop, outro, or user-defined label.

### Crate

Manual membership/order or smart-rule result. It references Tracks and never duplicates audio.

### Review Issue

Typed, explainable concern with severity/confidence, evidence, state, and resolution.

### Job

Long-running operation with type, scope, progress, state, timestamps, and structured failure.

### Sync Plan

Previewable set of destination-specific changes, warnings, conflicts, and expected results.

## Track field families

- Identity: title, artist(s), mix/version, album/release.
- Musical: BPM, key, energy 1–10, vocal, mood, genre, tags.
- Technical: duration, codec, bitrate, sample rate, bit depth, channels, loudness.
- Preparation: cues, grid, structure, rating/favorite, notes, prepared state.
- Operational: availability, analysis version, review state, sync state.
- History: added, last played, play count, edits, provenance.

## Duplicate taxonomy

- Exact bytes/checksum.
- Same audio, different container/encoding.
- Same master with metadata differences.
- DJ edit/remix/version.
- Likely but uncertain match.

Actions must include keep both, link as versions, choose preferred asset, consolidate safe metadata, ignore match, and—only with explicit confirmation—remove a location/file through an authorized runtime.

## Smart rules

- Typed operators per field.
- Human-readable expression.
- Nested AND/OR with visible grouping.
- Preview and count before save.
- Stable behavior when a field is unknown.
- Rule versioning or migration when schema semantics change.

## Analysis

Every result records:

- Source asset.
- Analyzer and version.
- Configuration/model version.
- Timestamp.
- Output and confidence/quality flags.
- Whether a user accepted, edited, or rejected it.

## Adapter contract

Each DJ integration declares:

- Supported import entities.
- Supported export/write fields.
- Cue/color/count constraints.
- Playlist/crate mapping.
- Grid/key differences.
- File-path/volume mapping.
- Conflict detection level.
- Validation capability.

## Deferred backend gaps from the former attempt

The former product-recovery work identified missing real contracts for artwork, waveform/cues, structure, notification count, sync-conflict listing, global search, track-list total count, and some Job status-message fields. The reboot must treat these as unimplemented until deliberately specified and tested. Never restore them as `dashboardUnavailable` forever; use that state only honestly while a capability is absent.

