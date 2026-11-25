# Design Workflow

## Official design file

[RetroBoy Figma file](https://www.figma.com/design/JzlpeeGKzHBfKAxJfSy3n7/Untitled?node-id=0-1&t=zEvDg9ehdh0V58UX-1)

At Phase 0A the file is intentionally blank. It is the official collaborative design surface, not yet a specification.

## Approval rule

Agents and contributors may inspect the file for context when access is available. They must not create, edit, delete, reorganize, rename, or publish design content without explicit owner approval for that design task.

## Proposed flow

1. Start from an approved product requirement and identify the user outcome, states, and constraints.
2. Audit existing tokens, components, and patterns in Storybook and Figma.
3. Explore the smallest coherent flow, including empty, loading, error, keyboard, controller, and reduced-motion behavior.
4. Review the proposal with the owner before treating it as approved direction.
5. Record approved tokens/components in Figma and mirror them in code with stable names.
6. Implement through owned components, then compare behavior and visuals against the approved design.
7. Feed implementation discoveries back into both the design file and documentation through an approved change.

## Figma MCP and Codex

Figma MCP/Codex may be used to inspect context, generate approved structures, and reconcile design with code. Automation does not waive review. Generated output must use the project foundation, remain editable, include meaningful names, and be checked for accessibility and interaction completeness.

## Source-of-truth boundaries

- Product behavior and scope: product requirements and accepted decisions.
- Visual/interaction intent: approved Figma design plus design principles.
- Implemented component behavior: repository code and tests.
- Reusable component examples: Storybook.

When these diverge, create a visible reconciliation task; do not silently overwrite one source with another.

## Handoff checklist

- User outcome and acceptance criteria are linked.
- All relevant states and responsive window constraints are represented.
- Keyboard/controller behavior, focus order, announcements, and motion are specified.
- Tokens and reused/new components are identified.
- Assets have origin, license, and export guidance.
- Unresolved questions are explicit.
