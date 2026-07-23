# Canonical UX Specification

## Information architecture

### Level 0 — Library selector

The pre-entry environment shows available Libraries, status, recent access, creation, and connection needs. It is not the internal app sidebar.

### Level 1 — Active Library shell

The shell contains:

- Top bar with current Library identity and Library switcher.
- Global search/command access.
- Health/status access.
- Notification access.
- User/account menu.
- Library-scoped sidebar.
- Primary content canvas.
- Persistent Media Engine region when a track is loaded.

### Sidebar model

The internal sidebar contains only resources and tools of the active Library. It may include:

- Dashboard
- Tracks
- Built-in collections
- Crates
- Review Center
- Jobs
- Activity
- Integrations
- Storage
- Settings

“Libraries” must not appear as an item in this sidebar. Switching is handled by the top-level Library control.

## Interaction laws

- Single click selects.
- Double click opens and plays where appropriate.
- Selection and playback are related but not identical.
- Context menus expose secondary actions without hiding primary actions.
- Destructive and bulk actions preview impact.
- Back/forward preserves workspace context.
- Each collection remembers columns, widths, density, sort, filters, grouping, and scroll where practical.
- Loading never replaces the whole shell with a spinner.
- Empty, loading, unavailable, permission-denied, offline, and error states are distinct.

## Media Engine

The Media Engine is the continuous preparation surface:

- Top: analysis summary and editable attributes.
- Center: detailed waveform, playhead, phrases/structure, cues, zoom, and seek.
- Bottom: compact Mini Player with transport, time, output, and essential identity.

It may expand into the Track Workspace overlay while preserving the underlying list context.

## Track Workspace

The Track Workspace is a focused overlay or layered workspace, not a separate dead-end settings page. It includes:

- Artwork and track identity.
- Waveform and cue editing.
- Analysis/provenance.
- Metadata and tags.
- Locations and availability.
- Crate membership.
- Review issues.
- Save/sync state.

Closing returns the user to the prior selection, scroll, and filters.

## Save mode

On first edit:

- Present Autosave and Manual Save.
- Explain the difference plainly.
- Include “Remember my choice.”
- Allow changing the preference later.

In manual mode, navigating away with dirty edits requires a contextual choice. Playback replacement is blocked only when it would discard or obscure unsaved editing context.

## Status semantics

- **Available:** usable now.
- **Local only:** available to the desktop runtime, not the server.
- **Remote/NAS:** reachable through an identified location.
- **Offline:** known but currently unreachable.
- **Missing:** expected location no longer resolves.
- **Unanalyzed:** no valid current analysis.
- **Review required:** a specific uncertainty or conflict exists.
- **Sync pending:** Pulse state differs from a destination.
- **Conflict:** both sides changed or mapping is ambiguous.

## Dashboard philosophy

Dashboard modules answer:

- What needs my attention?
- What changed?
- What can I continue?
- Is my Library healthy?
- What have I been using?

Every module must have a clear action or navigation destination.

