# Research summary — Performance & accessibility (May 2026)

Source: [Implementing WCAG 2.2 AA and Core Web Vitals in Angular 21 SaaS Admin Applications.txt](./Implementing%20WCAG%202.2%20AA%20and%20Core%20Web%20Vitals%20in%20Angular%2021%20SaaS%20Admin%20Applications.txt)

## Executive summary

**EAA (EU, June 2025)** and ADA litigation make **WCAG 2.2 AA** a B2B procurement gate (**VPAT 2.5**). Admin dashboards are judged on **INP ≤ 200ms** and keyboard/screen-reader flows — not marketing Lighthouse scores. **@axe-core/playwright** on primary flows is the L2 automation standard.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.2) |
|-------|----------------|----------------------|
| P1 WCAG | L1: Partial + documented roadmap; L2: axe on auth/settings/billing/members in CI | L2 gate P1 automated |
| P11 (new) | WCAG 2.4.11 Focus Not Obscured — sticky headers, scroll-padding | Add P11 Must |
| P8 lists | Virtual scroll or pagination for large grids (100+ rows) | Clarify P8 |
| Zoneless | Improves INP in dense admin UIs | Links to NG1/NG2 |
| Signals @if | Focus loss when conditional removes focused node — use effect/restore | anti-patterns.md |
| P7 toasts | `role="alert"` / `aria-live` polite vs assertive | Stay Must |
| Spartan/CDK | Headless primitives for dialogs, traps | implementation.md |

## L1 / L2 / L3 (research view)

| ID | L1 | L2 | L3 |
|----|----|----|-----|
| P1 | Partial conformance + remediation plan | axe CI on primary flows | Manual audit + VPAT |
| P11 | — | scroll-padding / focus not obscured | Validated in CI + manual |
| P4 | Basic dialogs | Spartan/CDK focus trap + Esc | Programmatic trap tests |
| P8 | Pagination ok | Virtual scroll or pagination at scale | CDK virtual scroll |

## Top actions for adopters

1. Add axe-playwright job on login, settings, billing, members routes.
2. `scroll-padding-top` for sticky shell headers (P11).
3. 24×24px hit targets on icon buttons (P2).
4. `provideZonelessChangeDetection()` for INP on data-heavy screens.
5. Publish accessibility statement + VPAT roadmap for EU buyers.

[← Research index](./README.md)
