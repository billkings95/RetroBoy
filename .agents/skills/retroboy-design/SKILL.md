---
name: retroboy-design
description: Design or review RetroBoy product UI, flows, components, Storybook stories, or Figma work while preserving its approved product, accessibility, and design foundations.
---

# RetroBoy Design

Use this skill for any RetroBoy interface, interaction, component, Storybook, or Figma task.

## Read first

Read these files in order before proposing or changing product UI:

1. `docs/PRODUCT_VISION.md`
2. `docs/PRODUCT_REQUIREMENTS.md`
3. `docs/DESIGN_PRINCIPLES.md`
4. `docs/UI_FOUNDATION.md`
5. `docs/DESIGN_WORKFLOW.md`
6. The relevant implemented components and Storybook stories, when they exist.

## Approval boundary

The official Figma file is linked in `docs/DESIGN_WORKFLOW.md`. Inspection for context is allowed. Do not mutate Figma—create, edit, delete, move, rename, publish, or reorganize nodes, styles, variables, components, pages, or prototypes—without explicit owner approval for the current task.

## Method

1. Restate the user outcome, committed requirement, and surface being designed.
2. Inventory existing tokens, components, patterns, and platform conventions before adding new ones.
3. Map the complete state model: default, hover where relevant, focus, pressed, selected, disabled, loading, empty, success, error, offline if relevant, and interrupted/recovery states.
4. Specify keyboard, controller, pointer, focus, announcement, reduced-motion, and window-size behavior.
5. Prefer Base UI primitives and owned shadcn-style components. Add a dependency only when a concrete unmet interaction justifies it.
6. Keep the game dominant, advanced controls progressive, destructive operations recoverable, and customization reversible.
7. Use semantic tokens. Do not paste a generic kit aesthetic or copy Nintendo/SameBoy trade dress.
8. Review the proposal with the owner before treating it as approved direction or altering the official Figma file.
9. When implementation exists, reconcile Figma, code, tests, and Storybook; report divergences rather than silently overwriting a source.

## Deliverables

A design task should leave:

- linked requirement and concise rationale;
- flow/state inventory and interaction rules;
- accessibility behavior;
- reused and new tokens/components;
- responsive window and full-screen behavior where relevant;
- asset provenance/licensing notes;
- explicit open questions and approval status.

## Quality check

Reject output that is visually generic, interaction-incomplete, inaccessible, overly nostalgic, dependent on unexplained libraries, destructive without recovery, or inconsistent with macOS expectations and RetroBoy's local-first privacy posture.
