# Adoption Plan

## Goal

Move a DJ from fragmented tools to Pulse without forcing an all-at-once migration or risking the working performance library.

## Adoption stages

### Observe

Connect read-only sources and inventory files/databases. Pulse explains what it sees and changes nothing.

### Understand

Run analysis and show suggested cleanup, confidence, missing files, and duplicates.

### Organize

Create Pulse crates, tags, saved views, and preferences without writing to DJ software.

### Prepare

Use Track Workspace, cues, structure, energy, and Review Center. Save within Pulse.

### Export cautiously

Enable the first adapter with preview, backup guidance, limited scope, and post-operation validation.

### Expand

Add more sources, automation rules, adapters, and recurring maintenance only after trust is established.

## Onboarding principles

- Explain the difference between Track, Asset, Location, Save, and Sync.
- Show why desktop access is needed for Mac-local files.
- Ask for the smallest necessary filesystem scope.
- Provide an ingest preview before committing.
- Use a small representative folder for the first run.
- Never demand immediate migration of the performance library.

## Trust milestones

- User confirms inventory accuracy.
- User accepts/rejects suggestions and understands provenance.
- User completes a reversible Pulse-only edit.
- User resolves a review issue.
- User previews a destination change plan.
- User completes a validated export.

## Documentation needed for adoption

- Quick start.
- Source and privacy explanation.
- Backup/recovery guide.
- Save vs Sync.
- Integration capability matrix.
- Troubleshooting and diagnostics export.
- “What Pulse changed” history.

## Product analytics

For a self-hosted product, telemetry must be optional, transparent, minimal, and never include audio, filenames, paths, or library content without explicit consent. Local metrics can still support the user's own health dashboard.

