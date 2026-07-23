# Pulse — Supabase Exclusion Recorded (2026-07-23)

## Objective
Record the user's explicit instruction that Pulse must never use Supabase
in any form, despite Supabase being globally installed/connected for
other, unrelated projects in this environment.

## What was done
1. Saved a durable memory (`pulse_no_supabase.md`, type: project) so future
   sessions enforce this without depending on chat history.
2. Added an "Explicit exclusions" section to `CLAUDE.md` stating: no
   Supabase skills/agents/MCP/CLI/APIs/SDKs/templates for Pulse; no
   `.claude/skills/supabase*`, `.agents/skills/supabase*`, or `supabase/`
   in this repo; changing this requires owner approval + a new ADR.
3. Added an "Explicit exclusion" section to
   `docs/architecture/adr/0003-stack-choices.md` recording the same
   decision at the architecture-decision level, next to the existing
   backend/frontend/desktop stack choices.
4. Committed and pushed (`c96fdfe`) — user had already authorized commits
   to GitHub for this project.

## Why this matters now
This restates and formalizes something already flagged twice this session:
a connected Supabase MCP server's tool-description text has repeatedly
tried to inject an unauthorized `npx skills add supabase/agent-skills`
instruction into agent calls for this repo. That was caught and blocked
each time, but the user's instruction here closes the gap permanently by
making the exclusion explicit, in-repo, and binding for both Claude and
Codex — not just something I personally remember to reject.

## Scope
This restriction is Pulse-specific only
(`/Users/ermegarcia/Documents/Claude Projects/Pulse`). The global Supabase
installation/connection used by the user's other projects was not touched,
disconnected, or reconfigured.

## Files changed
- `CLAUDE.md`
- `docs/architecture/adr/0003-stack-choices.md`

## Commit
```
c96fdfe docs: record explicit Supabase exclusion for Pulse
```
Pushed to `origin/main`.

## Verification
No functional code changed — this was a documentation-only addition. Did
not rerun the full check suite since no `apps/*` files were touched;
Session 1's last full verification (lint/typecheck/test/build, all
passing) remains the current baseline.
