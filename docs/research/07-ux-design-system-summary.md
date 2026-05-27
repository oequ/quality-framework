# Research summary — UX & design system (May 2026)

Source: [Modern B2B Admin UX and Design System Architecture.txt](./Modern%20B2B%20Admin%20UX%20and%20Design%20System%20Architecture.txt)

## Executive summary

2026 admin UX bar: **skeleton + shimmer** (not page spinners), **Spartan/CDK headless** primitives, **Tailwind v4 + OKLCH tokens**, **resource()**-driven loading/error, **type-to-confirm** destructive flows, realistic demo data. **Dark mode** is an L2 expectation for long admin sessions.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.3) |
|-------|----------------|----------------------|
| U4 skeletons | Default for tables/dashboards; shimmer not static gray | Clarify U4; L2 expects skeletons on main views |
| U6 errors | Inline retry via `resource.reload()` — not full page refresh | Clarify U6 |
| U9 tokens | OKLCH + `@theme` for perceptual contrast in light/dark | Clarify U9 |
| U11 (new) | System + manual dark mode without FOUC | Add U11 Should; **L2 gate** |
| U12 (new) | Runtime i18n (e.g. Transloco) for zoneless apps | Add U12 Could |
| U13 (new) | Optimistic UI for frequent writes | Add U13 Could |
| Settings IA | Sidebar + horizontal tabs + command palette | implementation.md note |

## L1 / L2 / L3 (research view)

| ID | L1 | L2 | L3 |
|----|----|----|-----|
| U4 | Spinners in content | Skeletons on primary views | Dimension-matched shimmer skeletons |
| U7 | `confirm()` | Modal confirm | Type-to-confirm for org delete |
| U9 | CSS variables | `@theme` tokens | OKLCH semantic palette |
| U10 | Generic placeholders | Structured mock data | Realistic names, avatars, billing scenarios |
| U11 | Light only | Dark + light, no flash | OKLCH dark palette + system preference |

## Top actions for adopters

1. Tailwind v4 `@import "tailwindcss"` + Spartan brain/helm in `libs/ui`.
2. Bind loading/empty/error to `resource()` signals (U3, U5, U6).
3. Enable dark mode via `.dark` or `data-theme` on root (U11).
4. Replace lorem ipsum demo data (U10).
5. Sticky columns + mobile card/table patterns for members/billing tables (U8).

[← Research index](./README.md)
