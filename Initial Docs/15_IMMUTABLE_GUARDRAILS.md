# Immutable Guardrails

These rules remain binding unless the user explicitly changes them.

## Product

1. Pulse is a Music Workspace, not “a dashboard.”
2. Libraries are top-level isolated environments.
3. A Library is selected before entering.
4. “Libraries” never appears inside an active Library's sidebar.
5. Switching Libraries happens from a higher-level selector, such as the top header or pre-entry screen.
6. The sidebar inside a Library contains only that Library's content and tools.
7. Frontend and backend remain separated.
8. Backend deployment is self-hosted, Docker-first, and targeted to Proxmox.
9. Pulse Desktop on macOS owns local filesystem, local playback, DJ database, external-drive, and other native responsibilities.
10. AI suggests; it does not silently overwrite user-approved data.
11. Changes are previewable and reversible where technically possible.
12. Save in Pulse is not Sync/export.
13. Crates do not duplicate audio files.
14. Primary cue design targets a maximum of eight.
15. Energy uses a 1–10 scale.

## UX

16. Visual direction is Apple-inspired macOS/iOS/visionOS with restrained blur, glass, floating depth, and native feeling.
17. Waveform is central to the Media Engine.
18. Analysis is above; Mini Player is below.
19. Single click selects; double click opens/plays where applicable.
20. Collection view preferences persist.
21. First edit establishes Autosave or Manual Save with “remember my choice.”
22. Manual unsaved edits are protected before playback/context replacement.
23. Dashboard is editable per user.
24. Jobs, Activity, Notifications, and Status are distinct concepts.
25. Status LED/indicator represents overall Library health, not an arbitrary job state.

## Engineering and truthfulness

26. No mock data presented as connected production data.
27. Unsupported artwork, waveform, cue, structure, notification, sync-conflict, search, count, or job fields use honest unavailable states until real contracts exist.
28. Legacy code is evidence, not product authority.
29. No milestone is complete without relevant tests and evidence.
30. Claude and Codex collaborate at every milestone under their defined authority.
31. Sessions stay small and atomic.
32. Every session produces a Markdown report, handoff, and latest pointer update.
33. Relevant mandatory skills must be invoked and recorded.
34. No giant session combining many unrelated phases.

## Prohibited shortcuts

- Rebuilding the old visual shell merely because screenshots exist.
- Copying legacy endpoints before revalidating the domain.
- Creating placeholder “success” flows.
- Treating NAS and Mac-local paths as interchangeable.
- Hiding adapter-specific limitations behind a generic sync button.
- Using visual polish to mask missing state ownership.
- Declaring complete with skipped Codex review, skipped skills, or missing report.

