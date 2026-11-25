# Technology Validation Plan

Phase 0B should answer the following with small disposable prototypes, repeatable measurements, and written decisions. Prototype code is not automatically production code.

Validation plans and ADR conventions live in `docs/validation/` and `docs/adr/`. The first active track is the SameBoy integration spike.

## 1. SameBoy integration

Validate:

- a pinned upstream revision builds for Apple Silicon through the intended Rust/C toolchain;
- core initialization, ROM loading, frame stepping, input, audio, video, save RAM, RTC, and serialized state work through a narrow adapter;
- allocation, pointer ownership, panic/error boundaries, and thread confinement are explicit;
- upstream license, source availability, modifications, and notice obligations are compatible with RetroBoy's MIT License and distribution model;
- an update/patch policy can preserve reproducible builds.

Deliverable: integration spike, API boundary sketch, license note, benchmark baseline, and ADR.

## 2. Graphics pipeline: WebGL2 vs native

Build equivalent minimal presenters and compare pixel scaling, color, shader chain, custom shader safety, resize/full screen, frame pacing, latency, CPU/GPU/energy use, copy overhead, tooling, failure recovery, and packaging. Test the minimum proposed macOS/WebKit environment and representative Apple Silicon tiers.

Deliverable: measurements, captured test method, maintenance analysis, and renderer ADR.

## 3. Audio and timing

Validate the audio clock model, sample buffering, underflow/overflow recovery, pause/background behavior, speed changes, Bluetooth-device changes, and synchronization with video. Define measurable targets after baseline data rather than inventing unsupported numbers.

## 4. Input

Validate keyboard and GameController-framework paths, hot-plugging, multiple devices, remapping, focus loss, full-screen shortcuts, analog-to-digital thresholds, and input latency. Ensure application shortcuts cannot silently consume required game inputs.

## 5. Rewind benchmark

Compare snapshot strategies across representative GB/GBC games and stress fixtures. Measure:

- capture and restore time distribution;
- bytes per second of retained history and peak memory;
- compression cost and UI preview latency;
- audio/video recovery after preview, cancel, and confirm;
- determinism/state integrity across repeated traversal;
- behavior when the resource budget is exhausted.

The behavior test must prove that timeline browsing is non-destructive, cancel restores the exact anchor, and confirmation alone branches active play.

## 6. Storage and packaging

Validate security-scoped file access if required, ROM relocation behavior, atomic replacement, crash recovery, schema migration, app sandbox implications, code signing, notarization, universal-versus-arm64 packaging assumptions, and update strategy.

## Decision record template

Each validation result should include context, options, test environment, method, raw evidence location, result, decision, consequences, unresolved risks, and a review trigger.

## Exit criteria

Phase 0B completes only when the core boundary, renderer, timing model, data strategy, macOS minimum, and packaging constraints have evidence-backed decisions sufficient to scaffold the production application.
