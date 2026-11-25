# UI Foundation

## Chosen foundation

- **Base UI** supplies accessible, unstyled interaction primitives where it meets the need.
- **shadcn-style components** are copied into and owned by the repository; they are a starting point, not the visual identity.
- **Tailwind CSS** expresses design tokens and component styling with a constrained configuration.
- **Storybook** is the component workshop, behavior catalog, and accessibility review surface.

The project will not install overlapping UI kits speculatively. Sonner, Vaul, command palettes, NumberFlow, animation libraries, and gallery components remain candidates only when a concrete interaction requires them.

## Token layers

Tokens should be semantic and shared between application and Storybook:

- color: surfaces, text, border, accent, status, overlay, focus;
- typography: display, title, body, label, numeric/monospace;
- space and size: a compact but breathable scale, hit targets, radii;
- motion: duration and easing roles with a reduced-motion mode;
- elevation and materials: restrained layers appropriate to macOS;
- game presentation: canvas background, bezel, safe area, and pixel scale.

Raw palette values must not be used directly in product components when a semantic token applies.

## Initial component inventory

1. App frame, sidebar, toolbar, content header, and inspector/panel.
2. Game card, library grid/list, empty state, search, filters, and context menu.
3. Button, icon button, toggle, checkbox, radio, select, slider, text field, tabs, tooltip, popover, dialog, menu, toast, and progress.
4. Player surface, transport overlay, input hint, status indicator, and full-screen controls.
5. Save slot, rewind timeline/frame, cheat row, shader preview, bezel picker, and destructive confirmation.

## Accessibility baseline

- Prefer semantic HTML and proven primitives; add ARIA only when semantics require it.
- Every operation must be keyboard reachable with visible focus.
- Do not use color alone to encode state.
- Maintain practical target sizes and readable contrast.
- Respect reduced motion and avoid motion that interferes with play.
- Announce asynchronous results without stealing focus.
- Test dialogs, menus, composite widgets, timeline navigation, and game controls with realistic input modes.

## Storybook expectations

Each component should document variants, states, loading/empty/error cases, long text, keyboard behavior, reduced motion, light/dark appearance if supported, and accessibility checks. Product flows remain in the app; Storybook is not a substitute for integration tests.
