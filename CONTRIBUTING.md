# Contributing to RetroBoy

RetroBoy is at an early foundation stage. Before opening a change, read `README.md`, `AGENTS.md`, `ROADMAP.md`, and the relevant documents under `docs/`.

## Before contributing

- Use an issue or short proposal for changes to product scope, architecture, dependencies, data formats, privacy, or design foundations.
- Keep pull requests focused on one outcome.
- Do not add dependencies without explaining the unmet need, alternatives considered, maintenance cost, license, and bundle/runtime impact.
- Do not include commercial ROMs, copyrighted artwork, user saves, credentials, or other private data.

## Design changes

The Figma file is the official collaborative design surface, but it must not be changed without owner approval. Product UI work must follow `docs/DESIGN_WORKFLOW.md`, `docs/UI_FOUNDATION.md`, and `docs/DESIGN_PRINCIPLES.md`.

## Code changes (future phases)

When application code exists:

1. Add or update tests for behavior changes.
2. Run formatting, linting, type checks, unit tests, integration tests, and relevant benchmarks.
3. Document user-visible changes and architectural decisions.
4. Verify keyboard access, focus behavior, reduced motion, contrast, and screen-reader semantics for UI changes.

Exact commands will be added after Phase 0B chooses and scaffolds the toolchain.

## Commit and pull request guidance

- Write imperative, outcome-oriented commit subjects.
- Explain why the change is needed and how it was validated.
- Call out data migrations, performance effects, privacy implications, and unresolved risks.
- Avoid mixing formatting-only changes with behavior changes.

## Licensing

The application license is pending. Contributions cannot be accepted under a clear long-term licensing model until it is selected. Third-party code and assets must have compatible licenses and preserved attribution.
