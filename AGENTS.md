# Agent Instructions

These instructions apply to the entire repository.

## Current phase

RetroBoy is in Phase 0. Do not install dependencies, scaffold application code, vendor SameBoy, or alter the official Figma design unless the task explicitly advances the project beyond foundation work and the owner approves it.

## Sources of truth

1. `docs/PRODUCT_REQUIREMENTS.md` defines committed scope and acceptance criteria.
2. `docs/ARCHITECTURE.md` defines approved technical boundaries.
3. `docs/UI_FOUNDATION.md` and `docs/DESIGN_PRINCIPLES.md` define UI constraints.
4. `ROADMAP.md` defines sequencing, not a promise of dates.

When documents conflict, surface the conflict instead of silently choosing a direction.

## Engineering rules

- Keep the emulation core isolated from UI and platform code.
- Pin the vendored SameBoy revision; preserve its upstream license and notices.
- Add dependencies only for a demonstrated need and document the trade-off.
- Prefer platform and browser capabilities before adding a library.
- Keep emulator state and user-library state separate.
- Treat ROMs, saves, screenshots, cheats, covers, and rewind snapshots as private local data.
- Never add telemetry, analytics, accounts, remote ROM fetching, or cloud synchronization without an explicit product decision.
- Record consequential decisions in documentation or a future ADR.

## Quality rules

- Tests must be deterministic and use legally redistributable fixtures.
- Never commit commercial ROMs, copyrighted cover art, secrets, signing credentials, build output, local databases, save files, or user paths.
- Validate accessibility and keyboard behavior for every interactive UI component.
- Benchmark emulation, audio, rendering, save integrity, and rewind behavior before calling a milestone complete.

## Design workflow

Use `.agents/skills/retroboy-design/SKILL.md` for product UI work. The official Figma file is linked in `docs/DESIGN_WORKFLOW.md`. Reading for context is allowed; design mutations require owner approval.

## Change discipline

- Preserve existing work and keep commits focused.
- Explain assumptions and unresolved decisions in the relevant document.
- Update documentation when behavior or scope changes.
- Do not present proposed choices as settled decisions.
