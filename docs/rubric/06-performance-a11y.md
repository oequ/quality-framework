# Performance & accessibility

WCAG 2.2 Level AA targets and rendering performance for admin UIs.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **P1** | **WCAG 2.2 AA target.** Primary flows meet AA (auth, settings, billing, members). | Must | axe / manual audit | Enterprise B2B expectation. |
| **P2** | **Target size (24×24px).** Interactive targets at least 24×24 CSS px (WCAG 2.2). | Must | axe / design review | Icon buttons in tables/menus. |
| **P3** | **Visible focus.** Keyboard focus indicators with ≥3:1 contrast. | Must | Tab test | `focus-visible` utilities in design system. |
| **P4** | **No focus traps.** Dialogs trap focus correctly and close on Escape. | Must | Tab test | CDK/Spartan dialog behavior. |
| **P5** | **Skip to content.** Skip link to `<main>` for keyboard users. | Should | Tab test | Shell layout responsibility. |
| **P6** | **Redundant entry (WCAG 2.2).** Avoid re-asking for same data; support autofill/drafts where relevant. | Should | UX test | Long billing/settings forms. |
| **P7** | **`aria-live` for toasts.** Success/error toasts announced to screen readers. | Must | axe / manual | Sonner/toast region configuration. |
| **P8** | **Virtual scroll for large lists.** CDK virtual scroll (or equivalent) for hundreds of rows. | Should | Performance test | Members/logs at scale. |
| **P9** | **Lazy images.** Avatars/logos use `loading="lazy"` where appropriate. | Should | Lighthouse | LCP improvement. |
| **P10** | **Drag-and-drop alternatives.** Any DnD has keyboard/click alternative (WCAG 2.2). | Should | UX test | Dashboard widgets if DnD exists. |

[← Rubric index](./README.md)
