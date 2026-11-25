# RetroBoy

RetroBoy is the codename for a focused, native-feeling Game Boy and Game Boy Color emulator for macOS on Apple Silicon.

The project is currently in **Phase 0 — Foundation and validation**. There is no application code yet. The first release is intentionally scoped to macOS and will prioritize a polished library, faithful play, reliable saves, and a rewind experience inspired by Nintendo Switch Online without destructive timeline jumps.

## Product direction

- **V1 platform:** macOS on Apple Silicon; the minimum macOS version is still to be decided.
- **Systems:** Nintendo Game Boy and Game Boy Color.
- **Application shell:** React, TypeScript, Vite, and Tauri 2/Rust.
- **Emulation core:** a pinned, vendored SameBoy C revision, integrated behind a narrow Rust boundary.
- **UI:** Base UI primitives, shadcn-style owned components, Tailwind CSS, and Storybook.
- **Design workflow:** the official Figma file plus Figma MCP/Codex, with human approval before design changes.
- **Privacy:** no accounts and no telemetry.
- **Distribution:** free and open source under the MIT License.

See [Product Vision](docs/PRODUCT_VISION.md), [Product Requirements](docs/PRODUCT_REQUIREMENTS.md), [Architecture](docs/ARCHITECTURE.md), and the [Roadmap](ROADMAP.md) for the current source of truth.

## Status

Phase 0A establishes documentation and project conventions only. It deliberately does not install dependencies, scaffold the application, or vendor SameBoy.

## Legal note

RetroBoy will not ship copyrighted ROMs, firmware, cover art, or other third-party game assets. Users are responsible for using content they are legally entitled to use. See [Privacy](docs/PRIVACY.md) and [Third-party notices](docs/THIRD_PARTY_NOTICES.md).

## Contributing

The project is not yet ready for feature contributions. Design and technical proposals are welcome as focused issues once issue templates and governance are established. Read [CONTRIBUTING.md](CONTRIBUTING.md) and [AGENTS.md](AGENTS.md) before making changes.

## License

RetroBoy is licensed under the [MIT License](LICENSE). Third-party components and assets remain subject to their respective licenses and notices.
