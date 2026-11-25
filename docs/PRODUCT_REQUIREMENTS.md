# Product Requirements

Status labels: **Committed** is required for V1; **Validation** needs Phase 0B evidence; **Pending** needs an owner decision.

## Scope

| Area | Requirement | Status |
| --- | --- | --- |
| Platform | Native-feeling macOS application for Apple Silicon | Committed |
| OS support | Minimum macOS version | Pending |
| Systems | Game Boy and Game Boy Color | Committed |
| Core | Pinned, vendored SameBoy C revision | Committed |
| Distribution | Free and open source | Proposed; license pending |
| Privacy | No accounts and no telemetry | Committed |

## Functional requirements

### Library and import

- Import local GB/GBC ROM files selected by the user; never download ROMs.
- Identify duplicates and preserve the source file unless the user chooses managed-copy behavior in a future explicit decision.
- Present a searchable, keyboard-navigable library with recent play context.
- Allow user-supplied covers and metadata overrides. Any automatic metadata or artwork service requires a separate privacy, licensing, and dependency decision.
- Provide clear handling for moved, missing, invalid, or unsupported files.

### Play session

- Launch supported games with stable video, audio, keyboard input, and common game controllers.
- Support pause/resume, full screen, input remapping, volume, and per-game settings.
- Preserve aspect ratio and expose intentional scaling/filter choices.
- Separate emulator pause from application background behavior and document both.

### Saves and states

- Persist cartridge/battery saves automatically using atomic writes and recoverable backups.
- Support explicit save states with preview, timestamp, game identity, compatibility metadata, and clear overwrite/delete confirmation.
- Detect incompatible or corrupt state data and fail without damaging known-good data.
- Provide user-visible backup/export and restore paths before V1 release.

### Rewind

- Capture bounded in-memory history with a configurable resource policy.
- Pausing into rewind opens a visual timeline inspired by Nintendo Switch Online behavior, but RetroBoy must implement its own interaction and visuals.
- Moving through the timeline is **non-destructive**: selection previews a candidate state without changing the active timeline until the user confirms.
- Cancel returns exactly to the pre-rewind state. Confirm resumes from the chosen point and creates a clear new active timeline; retention of the abandoned future is a Phase 0B product/technical decision.
- Benchmark interaction behavior, snapshot cadence, memory, compression, audio recovery, preview latency, and state integrity before implementation is accepted.

### Cheats, shaders, and bezels

- Support per-game cheats with enable/disable state and clear invalid-code feedback; exact code formats are to be validated against core capabilities.
- Ship a small accessible shader set and allow custom shaders only through a documented, sandboxed local format.
- Support built-in and user-provided bezels without obscuring essential controls or corrupting aspect ratio.
- Custom assets must fail safely and be removable without affecting saves.

## Non-functional requirements

- Deterministic emulation behavior for the same core revision, configuration, and input stream where the core permits it.
- No silent loss or overwrite of ROMs, saves, states, metadata, or custom assets.
- Responsive library interactions and stable frame pacing under representative loads.
- Full keyboard operation for application chrome; accessible names, focus order, contrast, scalable text where applicable, and reduced-motion support.
- Network access must be absent by default and introduced only for a documented user-facing feature.
- User data formats and locations must be documented before V1.

## Acceptance baseline

V1 is not complete until representative compatibility, performance, latency, save-integrity, rewind, accessibility, packaging, notarization, clean-install, upgrade, and recovery tests pass on the minimum supported Apple Silicon configuration.

## Explicitly out of scope

Intel Mac support, Windows/Linux releases, iOS, online multiplayer, cloud synchronization, user accounts, achievements, additional consoles, bundled ROMs/firmware, and automatic online cover scraping.
