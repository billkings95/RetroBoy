# Third-Party Notices

This file is the notice inventory for RetroBoy. RetroBoy's own code is available under the MIT License. Phase 0 records planned dependencies only; no dependency has been vendored or installed yet.

## Planned core dependency

### SameBoy

- Purpose: Game Boy and Game Boy Color emulation core.
- Integration: pinned and vendored C source behind a Rust FFI adapter.
- Upstream: <https://github.com/LIJI32/SameBoy>
- Candidate revision for the Phase 0B spike: `v1.0.5`, commit `ea667ad79aa28409f034b1fd6da7304e1844750d`; not yet accepted as the production pin.
- Candidate core license: Expat License, copyright 2015–2026 Lior Halphon. Preserve the upstream copyright and permission notice in source and distributed notices.
- Scope warning: the upstream `iOS` directory has an additional digital-marketplace condition, and `HexFiend` is excluded from the repository-wide Expat declaration. RetroBoy does not plan to use either directory; any future use requires a new review.
- Modifications: any RetroBoy patches must be documented and distributed as required by the upstream license.

## Planned application dependencies

The approved baseline categories are React, TypeScript, Vite, Tauri 2/Rust, Base UI, shadcn-style owned components, Tailwind CSS, and Storybook. Exact packages, versions, licenses, copyright notices, and transitive obligations will be generated and reviewed after scaffolding.

## Assets and test fixtures

Every bundled font, icon, shader, bezel, image, sound, test ROM, and fixture must include its origin, version or retrieval date, license, modifications, and required attribution. Do not add an asset whose redistribution rights are unclear.

RetroBoy will not bundle commercial ROMs, proprietary firmware, game cover art without permission, or trademarks presented in a way that implies endorsement.

## Release requirement

Before any public binary release:

1. Lock all production dependency revisions.
2. Run an automated license inventory and review it manually.
3. Include complete required notices and corresponding source/offer obligations.
4. Confirm compatibility with RetroBoy's MIT License and distribution model.
5. Make the notice inventory available in the repository and, where appropriate, inside the application or distribution bundle.

This document is not legal advice. Licensing uncertainties must be resolved before distribution.
