# Architecture Decision Records

Architecture Decision Records (ADRs) capture consequential technical choices and the evidence behind them. They describe what was known when a decision was made; later changes should supersede rather than rewrite accepted history.

## Statuses

- **Proposed:** evidence is being gathered and no implementation may depend on the choice yet.
- **Accepted:** the decision is approved for implementation.
- **Superseded:** a later ADR replaces the decision.
- **Rejected:** the option was evaluated and deliberately not selected.

## Naming

Use `NNNN-short-kebab-case-title.md`, beginning with `0001`. Reserve a number when the document is created, not while it is only discussed.

## Process

1. Copy `0000-template.md` to the next numbered file.
2. State the decision driver and measurable criteria before running a prototype.
3. Link raw evidence or a reproducible command; do not rely on impressions alone.
4. Keep unresolved risks visible.
5. Obtain owner approval before changing a status to Accepted.
6. Update related product or architecture documentation after acceptance.

## Current records

No decision has been accepted yet. The first planned record will cover the SameBoy integration boundary and revision policy after the integration spike produces evidence.
