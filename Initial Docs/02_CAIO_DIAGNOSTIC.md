# CAIO Diagnostic — Pulse

## Why this document exists

This diagnostic evaluates where automation and AI create genuine leverage, where deterministic systems are safer, and where human approval is mandatory.

## Current problem

Music preparation is fragmented across file browsers, DJ software, tagging tools, key/energy analyzers, duplicate finders, spreadsheets, and memory. Each application owns part of the truth. This produces:

- Conflicting metadata and grids.
- Repeated analysis.
- Duplicate or missing files.
- Weak visibility into confidence and provenance.
- Manual transfer between preparation and performance systems.
- Fear of bulk operations because rollback is unclear.

## Capability assessment

| Area | Best mechanism | Human role | Risk |
| --- | --- | --- | --- |
| File identity and checksums | Deterministic | Resolve ambiguous duplicates | Low |
| BPM/key/loudness analysis | DSP + confidence | Review uncertain results | Medium |
| Energy 1–10 | Model + signal features | Correct subjective misses | Medium |
| Mood/genre/tag suggestions | AI | Accept, edit, reject | Medium |
| Cue/structure suggestions | DSP/ML | Audition and approve | High |
| Metadata normalization | Rules + reference data | Approve batch preview | Medium |
| Duplicate resolution | Rules + similarity | Choose canonical asset | High |
| Crate suggestions | Rules/AI | Decide usefulness | Low |
| Sync/export | Deterministic adapter | Confirm destination/changes | High |
| UI prioritization | Rules from status | Configure preferences | Low |

## Automation readiness

Pulse is ready for assisted automation, not autonomous library control. The correct maturity sequence is:

1. Observe and inventory.
2. Analyze without modifying source data.
3. Explain findings and confidence.
4. Suggest reversible changes.
5. Preview batches and conflicts.
6. Apply approved changes with audit history.
7. Export/sync through destination-specific adapters.
8. Learn user preferences without hiding rules.

## Required trust controls

- Provenance for every derived or suggested value.
- Confidence where uncertainty exists.
- Before/after preview for bulk edits.
- Separate Save from Sync.
- Operation history and recoverability.
- Dry-run mode for imports, rules, duplicate merges, and exports.
- Explicit unavailable/unsupported states.
- No fabricated results during backend gaps.

## AI boundaries

AI may:

- Suggest tags, moods, energy, structural labels, related tracks, and cleanup actions.
- Explain why a track was flagged.
- Rank review work.
- Help translate natural-language intent into visible rules.

AI may not:

- Delete or move source audio without explicit confirmation.
- Silently overwrite trusted metadata.
- Claim certainty it does not have.
- impersonate real backend analysis in the UI.
- export to DJ software without a visible change plan.

## Diagnostic conclusion

Pulse has high-value automation potential because its work is repetitive, evidence-rich, and reviewable. The central product challenge is not model capability; it is constructing a trustworthy loop that joins local file access, deterministic contracts, transparent suggestions, user approval, and adapter-safe export.

