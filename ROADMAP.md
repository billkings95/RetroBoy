# RetroBoy Roadmap

This roadmap expresses sequence and exit criteria, not delivery dates.

## Phase 0A — Project foundation

**Goal:** establish the shared product, architecture, design, testing, privacy, and contribution baseline.

- [x] Define V1 product scope and non-goals.
- [x] Record the proposed technology stack and architecture boundaries.
- [x] Establish design workflow and UI principles.
- [x] Record validation questions, testing strategy, and privacy posture.
- [x] Register the official Figma file without changing it.
- [x] Select the MIT application license.
- [ ] Select the minimum supported macOS version.

## Phase 0B — Technical validation

**Goal:** retire the highest-risk assumptions with disposable prototypes and recorded evidence.

**Status:** started. The SameBoy integration spike is the first active validation track.

- Validate SameBoy C integration and licensing obligations.
- Compare WebGL2 and a native rendering path for latency, pacing, shader flexibility, maintainability, and Tauri compatibility.
- Prototype low-latency audio and controller input.
- Define and benchmark the rewind snapshot model and non-destructive selection interaction.
- Confirm app sandbox, file access, signing, notarization, and packaging constraints.
- Record decisions as ADRs before production scaffolding.

## Phase 1 — Vertical slice

**Goal:** load one legally redistributable test ROM and complete a representative local play loop.

- Application shell and library skeleton.
- ROM import, launch, input, audio, video, pause, and clean shutdown.
- Battery save persistence with atomic writes and recovery behavior.
- Initial Storybook foundation and accessibility checks.
- Automated smoke and core integration tests.

## Phase 2 — V1 feature completion

**Goal:** deliver the committed single-user macOS experience.

- Library metadata and user-managed covers.
- Save states and save management.
- Rewind timeline and non-destructive selection.
- Cheats with clear per-game management.
- Built-in and custom shaders; custom bezels.
- Keyboard/controller remapping and polished full-screen play.
- Import/export and backup paths for user data.

## Phase 3 — Release readiness

**Goal:** produce a trustworthy public V1.

- Compatibility, performance, accessibility, and data-integrity validation.
- Signed and notarized Apple Silicon build.
- Third-party notices, selected app license, release notes, and support guidance.
- Clean-install, upgrade, rollback, and removal tests.

## Future ideas — not V1 scope

Cross-platform support, additional systems, multiplayer, cloud sync, accounts, achievements, and automatic online metadata are deliberately deferred. The architecture should avoid gratuitous lock-in, but V1 will not pay the complexity cost of implementing them.
