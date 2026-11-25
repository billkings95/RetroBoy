# Testing Strategy

## Goals

Testing must protect emulation correctness, save integrity, timing, accessibility, privacy, and release packaging. A green UI test suite alone is insufficient.

## Test layers

- **Core adapter tests:** ownership, error translation, configuration, save RAM, state serialization, and deterministic stepping against a pinned SameBoy revision.
- **Domain unit tests:** library identity, migrations, settings, cheat parsing, rewind state machine, path validation, and atomic-write recovery.
- **UI component tests:** states, keyboard/focus behavior, accessible names, reduced motion, and visual regression in Storybook.
- **Integration tests:** typed Tauri commands/events, session lifecycle, import, launch, save, state, rewind, customization, and failure propagation.
- **End-to-end tests:** clean-user journeys on packaged builds with controlled local fixtures.
- **Performance tests:** startup, launch, frame pacing, audio stability, input latency, renderer cost, rewind capture/restore, memory growth, and energy impact.
- **Release tests:** clean install, upgrade/migration, rollback where supported, signing, notarization, Gatekeeper, offline operation, and removal guidance.

## ROM and fixture policy

Only self-authored, public-domain, or explicitly redistributable test ROMs and assets may enter the repository or CI. Record provenance and license alongside every fixture. Commercial ROM hashes may be used as local user-supplied identifiers only when legally appropriate; never upload ROM contents.

## Compatibility

Maintain a result matrix covering GB/GBC hardware modes, cartridges/core features relevant to supported games, saves/RTC, input, audio/video edge cases, and representative SameBoy test suites. Compatibility claims must name the core revision and configuration.

## Save integrity

Test interruption before, during, and after writes; insufficient space; permissions; corrupt/truncated files; incompatible versions; concurrent requests; restore from backup; and migration. Tests must assert that the last known-good data remains recoverable.

## Rewind

Use deterministic input traces and state fingerprints to verify preview, random seek, repeated seek, cancel, confirm/branch, buffer rollover, resource exhaustion, pause/background transitions, and audio recovery. Include long-running memory tests.

## Accessibility

Combine automated checks with manual keyboard, controller, VoiceOver-oriented semantic review, contrast, text scaling where applicable, reduced motion, and high-frequency interaction testing. Automation is a floor, not proof of usability.

## Continuous integration

The exact CI matrix will be selected after scaffolding. It should eventually gate formatting, linting, types, Rust checks, licenses/notices, unit/integration tests, Storybook build, accessibility checks, and a bounded smoke test. Performance trends may begin as non-blocking until stable baselines exist.
