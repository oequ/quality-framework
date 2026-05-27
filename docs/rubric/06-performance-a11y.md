# Performance & accessibility

WCAG 2.2 Level AA, admin UI performance (INP), and procurement (VPAT). See [research summary](../research/06-performance-a11y-summary.md).

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **P1** | **WCAG 2.2 AA on primary flows.** Auth, settings, billing, members meet AA. **L1:** Partial conformance allowed with published remediation roadmap. **L2:** automated `@axe-core/playwright` (or equivalent) on those flows in CI. | Must | axe / manual / CI | **L2 gate:** axe CI Pass on primary flows. EAA / VPAT for enterprise sales. |
| **P2** | **Target size (24×24px).** Interactive targets ≥ 24×24 CSS px (WCAG 2.5.8). | Must | axe / design review | Expand hit area with padding on icon buttons. |
| **P3** | **Visible focus.** Keyboard focus indicators ≥ 3:1 contrast. | Must | Tab test / axe | `focus-visible` in design system. |
| **P4** | **Dialog focus trap.** Modals trap focus, close on Escape, restore focus to trigger. | Must | Tab test | Spartan-ng / CDK / Angular ARIA patterns. |
| **P5** | **Skip to content.** Skip link to `<main>` for keyboard users. | Should | Tab test | Shell layout. |
| **P6** | **Redundant entry (WCAG 2.2).** Avoid re-asking data in multi-step flows; autofill where appropriate. | Should | UX test | Billing/onboarding wizards. |
| **P7** | **`aria-live` for toasts.** Errors `role="alert"` / `aria-live="assertive"`; success `polite`. | Must | axe / manual | Sonner/ngx-sonner configuration. |
| **P8** | **Large list performance.** Pagination, virtual scroll (CDK), or equivalent when lists routinely exceed ~100 rows. | Should | Performance test | Avoid DOM-heavy grids that hurt INP. |
| **P9** | **Lazy images.** Avatars/logos use `loading="lazy"` where appropriate. | Should | Lighthouse | Marketing LCP; less critical in admin shells. |
| **P10** | **Drag-and-drop alternatives.** DnD has keyboard/button alternative (WCAG 2.5.7). | Should | UX test | Kanban/column reorder if present. |
| **P11** | **Focus not obscured (WCAG 2.4.11).** Focused controls not hidden by sticky headers, drawers, or overlays — use `scroll-padding` etc. | Must | Tab test / axe | Dense admin layouts; **L2 gate** with P1. |

[← Rubric index](./README.md)
