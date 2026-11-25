# Privacy

RetroBoy is designed as a local, single-user application.

## Commitments

- No user account is required.
- No telemetry, analytics, advertising identifier, tracking pixel, or crash-report upload is included.
- No ROM, save, state, screenshot, cheat, cover, play history, input, file path, or configuration data is sent to RetroBoy maintainers.
- Core play remains usable offline.

## Local data

The application is expected to store library metadata, preferences, controller mappings, battery saves, save states, rewind buffers during play, user-provided covers/bezels/shaders, cheats, and diagnostic logs when explicitly enabled. Exact locations, retention, export, and deletion behavior must be documented before V1.

Rewind history should be ephemeral by default unless the user explicitly saves a state. Temporary data must be bounded and cleaned up after normal and abnormal termination where practical.

## File access

RetroBoy should request access only to files or folders needed for user-initiated import, play, customization, backup, or export. It must not scan unrelated locations. The managed-copy versus reference-in-place behavior remains a product decision and must be transparent to the user.

## Diagnostics

Default logs must avoid ROM data, save contents, cheats, full user paths, and other sensitive content. Any future diagnostic bundle must be previewable and explicitly exported by the user; automatic upload is out of scope.

## Network behavior

V1 has no approved network-dependent feature. A future feature that accesses the network requires a documented purpose, endpoint/data inventory, consent and settings behavior, retention policy, threat review, and update to this document before implementation.

## User control

Before release, users must be able to understand where RetroBoy data lives, export durable progress, remove individual games without accidental save loss, reset customizations, and delete all application-owned data through documented steps.

## Changes to this policy

Privacy-affecting changes require explicit product review. They must not be hidden inside dependency, crash-reporting, metadata, cover-art, update, or cloud features.
