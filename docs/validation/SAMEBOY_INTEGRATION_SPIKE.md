# SameBoy Integration Spike

- **Phase:** 0B — Technical validation
- **Status:** Ready for implementation
- **Production code:** No; findings may be promoted only through an accepted ADR

## Question

Can a pinned SameBoy C revision be built reproducibly for macOS on Apple Silicon and controlled safely through a narrow Rust boundary that exposes the capabilities RetroBoy needs?

## In scope

- Select and pin one upstream SameBoy revision after reviewing its current source, API, release history, and license.
- Build only the core surface required by the experiment for `aarch64-apple-darwin`.
- Create a minimal Rust executable or test harness with a dedicated C adapter.
- Initialize and shut down the core repeatedly without leaks or undefined ownership.
- Load a legally redistributable GB/GBC test fixture.
- Advance deterministic frames with scripted input.
- Obtain video and audio buffers with explicit format, lifetime, and ownership.
- Read and restore battery save/RTC data where the fixture supports it.
- Serialize and restore emulator state, then compare observable state after replay.
- Capture build time, frame-step time, state size, save/state operation time, and peak memory baseline.
- Document upstream license obligations, required notices, source/modification obligations, and a proposed update/patch policy.

## Out of scope

- React, Tauri, application UI, Storybook, WebGL2, native presentation, real-time audio output, controller support, rewind UI, ROM library management, signing, notarization, and production packaging.
- Commercial or user-owned ROMs in the repository or automated tests.
- Generalizing the adapter before the required surface is known.

## Proposed experiment layout

```text
experiments/sameboy-integration/
  README.md                 # exact setup, commands, and recorded environment
  Cargo.toml
  build.rs                  # pinned native build inputs
  src/
    main.rs                 # experiment orchestration only
    core.rs                 # safe Rust-facing boundary
  native/
    retroboy_sameboy.h      # minimal stable C adapter
    retroboy_sameboy.c
  fixtures/
    README.md               # provenance and retrieval/build instructions
  results/
    README.md               # schema; raw local runs ignored if machine-specific
```

The exact files may change when the selected upstream revision is inspected. SameBoy source must not be copied into the repository until its revision, acquisition method, and notice obligations are recorded.

## Boundary rules

- The Rust layer must not depend directly on broad SameBoy headers.
- The C adapter owns translation of upstream callbacks and types into RetroBoy-specific fixed-width types.
- Every pointer, buffer, callback, and thread-affinity rule must have one documented owner and lifetime.
- No Rust panic may unwind across C, and no C error may become silent undefined behavior.
- Inputs and outputs must be bounded and validated before allocation or copying.
- Core callbacks must not access UI, filesystem, networking, or global application state.

## Required evidence

| Evidence | Minimum content |
| --- | --- |
| Environment | Mac model/chip, memory, macOS, Xcode/CLT, Rust and C compiler versions |
| Upstream pin | Repository URL, full commit SHA, retrieval date, relevant release/tag |
| Reproduction | Clean checkout commands and fixture acquisition/build steps |
| License review | License text at pin, notices, modification/source obligations, compatibility note |
| API map | Required RetroBoy capability to adapter function/callback |
| Ownership map | Allocation, deallocation, buffer lifetime, callbacks, thread confinement |
| Correctness | Frame/state fingerprints and save/state round trips with scripted input |
| Performance | Method, warm-up, sample count, distribution, peak memory, known noise |
| Limitations | Unsupported capabilities, upstream coupling, and untested assumptions |

## Success criteria

- A clean Apple Silicon environment can reproduce the build from the documented pin and commands.
- The harness performs at least 100 initialize/load/run/shutdown cycles without a crash; leak tooling shows no experiment-owned leak.
- Scripted input produces repeatable frame fingerprints under identical configuration.
- A serialize/advance/restore/replay cycle reproduces the same measured frame/state result.
- Save RAM and RTC ownership and persistence behavior are understood or explicitly recorded as unsupported by the selected fixture.
- All unsafe Rust and C entry points have documented safety invariants.
- Baseline measurements include method and uncertainty rather than an unsupported performance target.
- Licensing obligations are recorded sufficiently to decide whether and how to vendor the selected revision.
- A proposed ADR can recommend the boundary, pin/update policy, and next validation work.

## Failure criteria

- The needed core capabilities require broad or unstable upstream internals with no maintainable adapter.
- Ownership or threading cannot be made explicit at the boundary.
- State or save round trips cannot be made repeatable enough for later rewind validation.
- Reproducible Apple Silicon builds require unacceptable undocumented patches.
- License obligations cannot be satisfied by the intended MIT application distribution model.

Failure is a useful result: document it and evaluate another revision, integration mode, or core before expanding scope.

## Implementation gates

Before writing experiment code:

1. Inspect current SameBoy upstream documentation and license from primary sources.
2. Record the candidate full commit SHA and why it was selected.
3. Choose or build an explicitly redistributable fixture and record its provenance.
4. Capture the local macOS/Rust/C toolchain baseline.
5. Confirm the experiment can remain isolated from production dependencies.

## Deliverables

- Reproducible experiment and fixture instructions.
- Results summary with raw evidence references.
- SameBoy third-party notice update.
- Proposed `0001` ADR for the integration boundary and revision policy.
- Follow-up issues for graphics, audio/input, rewind, and any discovered blocker.
