# UX & design system

Loading, empty, and error states; destructive actions; Tailwind v4 and accessible primitives.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **U1** | **Tailwind v4 native.** `@import "tailwindcss"` and Vite plugin—not legacy PostCSS-only setup. | Must | Config | v4 CSS-first configuration. |
| **U2** | **Accessible primitives.** Use headless/brain layer (e.g. `@spartan-ng/brain`) for complex widgets—not hand-rolled selects/dialogs. | Must | Code review | Dialog, select, dropdown menus. |
| **U3** | **Loading states.** Async actions show loading (button disabled, skeleton, or `resource.isLoading()`). | Must | UX test | Invite, save settings, billing actions. |
| **U4** | **Skeleton screens.** Content areas use skeletons—not full-page spinners only. | Should | UX test | Dashboard and settings pages. |
| **U5** | **Empty states.** Tables/lists show helpful empty state + CTA when data is `[]`. | Must | UX test | Invoices, members search.no results. |
| **U6** | **Error recovery.** Network/API errors show message + retry (`resource.reload()` or equivalent). | Must | UX test | Port errors mapped to user-facing copy. |
| **U7** | **Destructive confirmation.** Delete workspace, remove member, cancel subscription require confirm dialog. | Must | UX test | B2B accident prevention. |
| **U8** | **Responsive tables.** Data tables work on tablet/mobile (scroll or card layout). | Must | Responsive test | Members, invoices. |
| **U9** | **Design tokens.** Colors/spacing via CSS variables/Tailwind theme—not random hex in components. | Must | ESLint / review | Theme switching readiness. |
| **U10** | **Demo realism.** Demo app looks product-grade, not wireframe. | Should | UI review | OSS first impression. |

[← Rubric index](./README.md)
