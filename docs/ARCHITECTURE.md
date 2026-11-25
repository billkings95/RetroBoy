# Architecture

This is the proposed architecture baseline. Phase 0B must validate the risky boundaries before production scaffolding.

## System shape

```text
React/TypeScript UI
  ├─ Library, settings, rewind timeline, overlays
  ├─ Owned UI components + Storybook
  └─ Typed commands/events
            │
Tauri 2 boundary
            │
Rust application services
  ├─ Session orchestration and state machine
  ├─ Library metadata and local persistence
  ├─ Save/state atomic I/O
  ├─ Input, audio, rendering adapters
  └─ Rewind coordinator and resource budgets
            │
Narrow C FFI adapter
            │
Pinned vendored SameBoy C core
```

## Boundaries

- **UI layer:** renders application state and sends user intent. It must not manipulate core memory, saves, or ROM files directly.
- **Tauri boundary:** exposes a small, typed, allowlisted command/event API. Avoid generic filesystem or shell access.
- **Rust domain layer:** owns session lifecycle, validation, persistence, error translation, resource limits, and platform adapters.
- **Core adapter:** is the only code that knows SameBoy C APIs. It translates frames, audio, input, save RAM, and serialized state through explicit ownership rules.
- **SameBoy:** remains upstream-derived code at a pinned revision with minimal, auditable patches.

## State ownership

Separate these domains:

1. **Library state:** ROM identity, user metadata, covers, last-played information, and settings.
2. **Durable game state:** battery saves, explicit save states, backups, and compatibility metadata.
3. **Ephemeral session state:** active core instance, inputs, audio/video buffers, and rewind snapshots.
4. **UI state:** navigation, dialogs, selections, and transient preview state.

No UI action should mutate durable game state until a domain command validates and commits it.

## Emulation execution

The core should run off the UI thread. The exact threading model, synchronization primitives, audio clock strategy, and buffer ownership require a prototype. Backpressure must be explicit; the UI must never become the timing source for emulation.

## Graphics decision gate

WebGL2 through the webview and a native rendering path are both candidates. Phase 0B must compare them with the same workload and shader goals across:

- frame pacing, presentation latency, tearing, and full-screen behavior;
- pixel-accurate scaling and color handling;
- built-in/custom shader feasibility and failure isolation;
- CPU/GPU/energy cost and data-copy overhead;
- Tauri/webview integration complexity, portability, debugging, and maintenance.

No production renderer should be selected before this evidence is recorded.

## Rewind model

The likely model combines periodic full snapshots with bounded deltas or compressed snapshots plus an input log. This is not settled. The UI requires two states: an immutable live-session anchor and a preview cursor. Only confirmation may branch the active timeline; cancel restores the anchor byte-for-byte.

## Persistence

- Use application-owned metadata keyed by a stable content identity, not only a mutable path.
- Write saves and metadata through temporary files plus atomic replacement where the platform permits.
- Keep a bounded recovery copy for high-value data.
- Version every durable schema and serialized wrapper owned by RetroBoy.
- Treat upstream save-state compatibility as revision-sensitive; record the core revision and configuration.

## Security and privacy

- Apply least-privilege Tauri capabilities and platform file access.
- Validate all paths, imported files, custom shaders, bezels, cheat text, and core-produced sizes.
- Do not execute content from a ROM library.
- Avoid network entitlements and endpoints unless a later approved feature requires them.
- Never log ROM contents, save contents, user paths, or cheat data by default.

## Dependency policy

React, TypeScript, Vite, Tauri 2/Rust, SameBoy, Base UI, shadcn-style components, Tailwind CSS, and Storybook are the approved baseline. Additional dependencies require demonstrated need, alternatives, license review, maintenance signal, security posture, and bundle/runtime impact.

## Decisions still required

- Minimum macOS version and related WebKit capabilities.
- WebGL2 versus native graphics pipeline.
- Audio and input backends.
- SameBoy revision, update policy, and patch strategy.
- Library database/file format and managed-copy policy.
- Rewind storage algorithm and abandoned-future behavior.
- Distribution channel.
