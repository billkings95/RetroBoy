# Phase 0B Validation

This directory holds plans and durable summaries for disposable technical experiments. Experimental source code will live under `experiments/` when implementation begins; accepted production architecture must not depend on a spike merely because it works once.

## Rules

- Define success, failure, and measurements before implementation.
- Pin every external revision and record the complete test environment.
- Use only self-authored, public-domain, or explicitly redistributable fixtures.
- Keep raw results reproducible and free of private paths or user data.
- Treat experiment dependencies as local to the experiment until separately approved for production.
- End each experiment with a result summary and proposed ADR; owner approval is required to accept a decision.

## Sequence

1. SameBoy integration boundary and license validation.
2. Equivalent WebGL2 and native graphics presenters.
3. Audio clock and input prototypes.
4. Rewind storage and non-destructive behavior benchmark.
5. Storage, sandbox, signing, notarization, and packaging checks.

The active plan is [SameBoy Integration Spike](SAMEBOY_INTEGRATION_SPIKE.md). Its initial upstream review selected [SameBoy v1.0.5 as a candidate revision](SAMEBOY_CANDIDATE.md), pending experimental validation.
