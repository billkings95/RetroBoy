# SameBoy Candidate Revision Review

- **Reviewed:** 2026-11-25
- **Upstream:** <https://github.com/LIJI32/SameBoy>
- **Candidate release:** `v1.0.5`
- **Candidate commit:** `ea667ad79aa28409f034b1fd6da7304e1844750d`
- **Status:** Candidate for the integration spike; not yet accepted for production

## Why this candidate

At review time, `v1.0.5` is the latest non-prerelease SameBoy release and its annotated tag resolves to the same commit as the upstream `master` head. A released revision gives the spike a reproducible baseline and documented change set while still testing the current public core API.

This selection is provisional. The spike must still demonstrate a reproducible Apple Silicon build, a maintainable Rust/C boundary, correct state and battery round trips, and acceptable licensing/notice handling before an ADR may accept it.

## API surface observed

The public headers at the candidate revision expose the capabilities needed for the first spike:

- allocated or caller-managed `GB_gameboy_t` lifecycle through `GB_alloc`, `GB_init`, `GB_free`, and `GB_dealloc`;
- buffered ROM loading through `GB_load_rom_from_buffer`;
- frame stepping through `GB_run_frame`;
- pixel output through `GB_get_pixels_output`;
- callback-oriented input/audio integration in the public `Core/gb.h` surface;
- battery size, save, load, and dirty-state APIs using buffers;
- save-state size, serialization, validation, and restoration using buffers.

The public structure is intentionally opaque outside internal builds, but the header remains broad. RetroBoy should therefore expose only its own small C adapter and keep SameBoy types out of safe Rust and future application layers.

## License finding

At this revision, SameBoy states that repository content outside the `iOS` and `HexFiend` directories is licensed under the Expat License, with copyright `2015–2026 Lior Halphon`. The Expat terms are substantively the MIT permission-and-warranty text and require preservation of the copyright and permission notice in copies or substantial portions.

The `iOS` directory has an additional digital-marketplace distribution condition. The RetroBoy spike intends to use only the platform-independent core and must not copy from `iOS` or `HexFiend`. If future work needs either directory, licensing must be reviewed again before any use.

### Preliminary compatibility conclusion

Using the Expat-licensed core in an MIT-licensed RetroBoy distribution appears compatible provided that:

- SameBoy's copyright and permission notice are preserved;
- the selected source revision and any RetroBoy modifications are identified;
- the distributed source and binary notice inventory includes the SameBoy notice;
- no code from differently treated directories is included without a separate review.

This is a project licensing assessment, not legal advice. The final vendoring and release contents must be checked against the exact pinned tree.

## Pin and update proposal for the spike

- Fetch and verify the full commit SHA, never a moving branch.
- Record the associated release tag separately; the commit SHA remains authoritative.
- Keep upstream source unmodified where possible and isolate required patches as named files with rationale.
- Review upstream releases manually; do not automatically advance the pin.
- Re-run correctness, save/state, performance, license, and notice checks for every candidate update.
- Do not convert this candidate into the production pin until the proposed ADR is accepted.

## Evidence sources

- [SameBoy release v1.0.5](https://github.com/LIJI32/SameBoy/releases/tag/v1.0.5)
- [Candidate commit](https://github.com/LIJI32/SameBoy/commit/ea667ad79aa28409f034b1fd6da7304e1844750d)
- [Upstream LICENSE at v1.0.5](https://github.com/LIJI32/SameBoy/blob/v1.0.5/LICENSE)
- [Public core header at v1.0.5](https://github.com/LIJI32/SameBoy/blob/v1.0.5/Core/gb.h)
- [Save-state header at v1.0.5](https://github.com/LIJI32/SameBoy/blob/v1.0.5/Core/save_state.h)

## Remaining gates

- Inspect build inputs and compile the minimum required core on an Apple Silicon Mac.
- Select a redistributable GB/GBC fixture with recorded provenance.
- Map the exact audio and input callback contracts used by the adapter.
- Verify compiler flags and optional core feature macros.
- Run lifecycle, determinism, battery, state, leak, and baseline performance tests.
- Produce the proposed integration ADR.
