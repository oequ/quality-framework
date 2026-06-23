# Deep Research — UX & design system (U1–U10)

Weight: 10% of total score.

---

## Role

You are a product design engineer specializing in **design systems**, **B2B admin UX**, and **Tailwind CSS** ecosystems for SaaS control planes.

## Context

Quality Framework v1.0 UX & design system criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| U1 | Tailwind v4 native setup | Must |
| U2 | Accessible headless primitives (Spartan/brain, Radix-like) | Must |
| U3 | Loading states on async actions | Must |
| U4 | Skeleton screens (not spinners only) | Should |
| U5 | Empty states with CTA | Must |
| U6 | Error recovery (message + retry) | Must |
| U7 | Destructive action confirmation | Must |
| U8 | Responsive tables (mobile/tablet) | Must |
| U9 | Design tokens (CSS variables / theme) | Must |
| U10 | Demo realism (product-grade, not wireframe) | Should |

Example reference stack: Tailwind v4, headless UI primitives (brain + helm pattern), oklch CSS variables, mock data with realistic org names, skeleton components, toast notifications.

## Research questions

### 1. 2026 B2B admin UX expectations

What UX patterns do users expect from **modern B2B SaaS** (Linear, Notion, Stripe Dashboard, Vercel, Retool) in 2026?

- Information density vs consumer simplicity
- Settings IA patterns (tabs vs sidebar vs command palette)
- Dark mode — required for L2?
- AI copilot UI affordances — emerging Must?

### 2. Design system architecture (U1, U2, U9)

- Tailwind v4 adoption status (2026) — v3 legacy tolerance?
- Headless component libraries: shadcn/ui influence on Angular (Spartan-ng)
- Design tokens — OKLCH, CSS `@property`, theme switching best practice
- Monorepo UI library structure — per-component packages vs single `libs/ui`

### 3. Async UX patterns (U3, U4, U6)

Research **loading / empty / error** state standards:

- Skeleton vs shimmer vs progress — when each is expected
- Angular `resource()` integration with UI patterns
- Optimistic updates for invites/billing — L2 expectation?
- Error copy and retry — i18n requirements

### 4. Destructive flows (U7)

Best practices for delete workspace, remove member, cancel subscription:

- Confirmation dialog patterns (type-to-confirm, checkbox)
- Undo vs confirm — 2026 trends
- Audit trail UI hints

### 5. Data tables in admin UIs (U8)

- Responsive strategies: horizontal scroll vs card collapse vs column hiding
- Mobile admin usage — statistics on B2B users on tablet/phone
- Filtering, sorting, bulk actions — table-stakes for members/billing?

### 6. Demo quality as sales asset (U10)

How important is **live demo quality** for OSS starter conversion?

- GitHub Pages demo vs Storybook vs video
- Realistic mock data vs lorem ipsum — impact on trust
- Screenshot-driven README expectations

### 7. Internationalization

Should UX rubric reference **i18n** (not currently weighted)?

- English-only starter acceptance in 2026 global market
- Transloco/ngx-translate vs Angular built-in i18n

### 8. L1 / L2 / L3 mapping

| ID | 2026 L1 | 2026 L2 | 2026 L3 |
|----|---------|---------|---------|

### 9. Competitive benchmark

Compare UX maturity of 3–5 SaaS starters/boilerplates (Angular or cross-stack):

- What they ship out of the box
- Common UX gaps users complain about

## Output format

1. Executive summary — UX bar for credible SaaS starter (2026)
2. Pattern library checklist (loading/empty/error/destructive/responsive)
3. Design system stack recommendation (Tailwind v4 + headless)
4. Demo realism guidelines (data, screenshots, live URL)
5. L1/L2/L3 mapping (U1–U10)
6. Suggested new UX criteria for v1.1 (dark mode, i18n, optimistic UI)
7. Bibliography (Tailwind docs, Radix/Spartan, Nielsen Norman B2B reports, SaaS UX case studies)

## Source priorities

- tailwindcss.com v4 documentation
- Spartan-ng / Angular Material / PrimeNG comparisons (2025–2026)
- Stripe Press / Stripe design blog (dashboard patterns)
- Baymard Institute (if applicable to admin)
- Mobbin / SaaS landing page galleries for visual trends

## Constraints

- Focus on **admin/control-plane**, not consumer mobile apps.
- Avoid purely aesthetic trends without usability evidence.
