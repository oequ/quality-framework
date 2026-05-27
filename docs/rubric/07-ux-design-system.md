# UX & design system

Loading, empty, and error states; destructive actions; Tailwind v4 and accessible primitives. See [research summary](../research/07-ux-design-system-summary.md).

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **U1** | **Tailwind v4 native.** `@import "tailwindcss"` and Vite plugin—not legacy PostCSS-only setup. | Must | Config | CSS-first `@theme` configuration. |
| **U2** | **Accessible primitives.** Headless layer (e.g. `@spartan-ng/brain`, CDK, Angular ARIA) for dialogs, selects, menus. | Must | Code review | Do not hand-roll complex widgets. |
| **U3** | **Loading states.** Async actions show loading (`resource.isLoading()`, disabled buttons, inline spinners). | Must | UX test | Prefer contextual loaders over full-page blockers. |
| **U4** | **Skeleton screens.** Primary content areas use layout-matched skeletons with shimmer—not spinners-only. | Should | UX test | **L2 gate:** skeletons on dashboard/settings list views. |
| **U5** | **Empty states.** Tables/lists show helpful empty state + CTA when data is empty. | Must | UX test | Members, invoices, search.no results. |
| **U6** | **Error recovery.** User-friendly message + **inline retry** (`resource.reload()`); avoid full-page refresh as only recovery. | Must | UX test | Map port errors to copy in features. |
| **U7** | **Destructive confirmation.** Delete org, remove member, cancel subscription require modal; type-to-confirm for irreversible org delete (L3). | Must | UX test | B2B accident prevention. |
| **U8** | **Responsive tables.** Data tables work on tablet/mobile (scroll + sticky column, card stack, or drawer). | Must | Responsive test | Members, billing, audit views. |
| **U9** | **Design tokens.** Semantic colors/spacing via CSS variables / `@theme`—OKLCH recommended for light/dark parity. | Must | Review | No random hex in feature components. |
| **U10** | **Demo realism.** Demo uses realistic names, roles, and billing scenarios—not lorem ipsum. | Should | UI review | OSS first impression. |
| **U11** | **Dark mode.** Light + dark themes; system preference; no flash on toggle (FOUC). | Should | UX test | **L2 gate:** dark mode shippable. |
| **U12** | **i18n-ready.** Externalized strings; runtime locale switch (e.g. Transloco) without full reload. | Could | Config | RTL support for global B2B. |
| **U13** | **Optimistic UI.** Frequent writes (tags, roles) update UI before server ack with rollback on failure. | Could | UX test | Linear-style responsiveness. |

[← Rubric index](./README.md)
