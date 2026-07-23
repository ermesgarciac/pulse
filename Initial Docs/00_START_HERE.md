# Pulse Reboot — Start Here

## Purpose

This folder is the canonical handoff for rebuilding Pulse when **no repository or project files exist yet**. Pulse is a self-hosted **Music Workspace** for DJs and serious music-library users. The former codebase has been deleted from the user's computer. Historical branches, worktrees, screenshots, checkpoint commits, and reports are context only; Claude must not expect to find or recover them.

## Authority order

When sources disagree, use this order:

1. The user's newest explicit instruction.
2. `15_IMMUTABLE_GUARDRAILS.md`.
3. Product and UX specifications in this package.
4. An accepted Architecture Decision Record (ADR).
5. Current milestone contracts and tests.
6. Legacy code or reports, as historical evidence only.

Never infer a product decision from unfinished legacy code.

## Required reading order

1. `01_PRODUCT_VISION.md`
2. `02_CAIO_DIAGNOSTIC.md`
3. `03_LOOP_MAP.md`
4. `04_PRD.md`
5. `05_CANONICAL_UX_SPEC.md`
6. `06_SCREEN_AND_FLOW_SPEC.md`
7. `07_DESIGN_SYSTEM.md`
8. `08_SYSTEM_ARCHITECTURE.md`
9. `09_DOMAIN_AND_FEATURES.md`
10. `10_IMPLEMENTATION_PLAN.md`
11. `11_ADOPTION_PLAN.md`
12. `12_RECURRENCE_PLAN.md`
13. `13_CLAUDE_CODEX_WORKFLOW.md`
14. `14_DELIVERY_AND_REPORTING.md`
15. `15_IMMUTABLE_GUARDRAILS.md`
16. `16_ROADMAP.md`
17. `17_GREENFIELD_SETUP.md`
18. `18_SKILL_ROUTING_AND_REGISTRY.md`
19. `CLAUDE_BOOTSTRAP_PROMPT.md`

## Reboot assumption

This is a clean restart:

- No existing repository: create a new repository and clean history.
- New contracts based on the product specification, not copied endpoints.
- Legacy checkpoints `ddcd5b1`, `d6ea841`, the recovery worktree, and related reports are not present and must not be treated as dependencies.
- No blind copying of UI, schemas, migrations, dependencies, or infrastructure.
- Approved product decisions remain binding.

## Decision labels

- **Canonical:** approved and binding.
- **Proposed:** recommended, but Claude must ask before making it permanent.
- **Deferred:** intentionally outside the current milestone.
- **Unknown:** requires user input; do not guess.

## Definition of a trustworthy session

A session is complete only when:

- Its scope has one primary objective and no more than 2–3 deliverables.
- All relevant mandatory skills were actually invoked and recorded.
- Claude and Codex both participated at the required points.
- Tests and visual evidence match the acceptance criteria.
- No fake connected state or unsupported backend capability was introduced.
- A concise but complete Markdown report, handoff, and latest pointer were updated.
