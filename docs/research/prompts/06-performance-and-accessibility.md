# Deep Research — Performance & accessibility (P1–P10)

Weight: 5% of total score. L2 requires WCAG 2.2 AA on primary flows.

---

## Role

You are a web performance and accessibility specialist focused on **enterprise admin UIs**, **WCAG 2.2**, and **Core Web Vitals** for authenticated applications.

## Context

Quality Framework v1.0 Performance & a11y criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| P1 | WCAG 2.2 AA on primary flows | Must |
| P2 | Target size 24×24px minimum | Must |
| P3 | Visible focus indicators (≥3:1 contrast) | Must |
| P4 | Dialog focus trap + Escape to close | Must |
| P5 | Skip to content link | Should |
| P6 | Redundant entry avoidance (WCAG 2.2) | Should |
| P7 | `aria-live` for toasts | Must |
| P8 | Virtual scroll for large lists | Should |
| P9 | Lazy loading images | Should |
| P10 | Drag-and-drop keyboard alternatives | Should |

Stack: Angular 21, Spartan/CDK dialogs, Sonner toasts, data tables for members/emails, Chart.js metrics, Tailwind v4.

## Research questions

### 1. 2026 accessibility bar for B2B SaaS

Is **WCAG 2.2 Level AA** table-stakes for B2B products in 2026?

- Legal drivers: European Accessibility Act (EAA) effective dates and scope
- US Section 508 / ADA litigation trends for SaaS
- VPAT / ACR documentation — when enterprise buyers require it
- Difference between **marketing site** and **authenticated app** a11y expectations

### 2. WCAG 2.2 new success criteria impact (P2, P6, P10)

Explain practical implementation for admin UIs:

- 2.5.8 Target Size (Minimum)
- 3.3.7 Redundant Entry
- 2.5.7 Dragging Movements alternatives
- Focus appearance (2.4.11 / 2.4.12) — focus indicator requirements

Which are **Must** for L2 in 2026 vs aspirational?

### 3. Angular + headless UI accessibility (P3, P4, P7)

- Spartan-ng / Radix / CDK — a11y maturity comparison 2026
- Dialog focus management — testing checklist
- Toast announcements — Sonner vs Angular Material vs custom live regions
- Known Angular a11y gaps with signals/control flow

### 4. Performance for admin apps (not marketing sites)

Core Web Vitals expectations for **logged-in dashboards**:

- Do buyers benchmark Lighthouse on app shell or public landing?
- Acceptable LCP/INP/CLS for heavy data tables
- Angular zoneless impact on INP (tie to NG1/NG2 research)
- Virtual scroll (CDK) — when required vs pagination sufficient

### 5. Automated a11y testing (P1)

2026 tooling landscape:

- axe-core in CI vs Pa11y vs Playwright `@axe-core/playwright`
- Should rubric require automated a11y gate for L2?
- Manual audit frequency and cost benchmarks

### 6. Inclusive design patterns for SaaS admin

- Keyboard navigation for dense tables and command palettes
- Screen reader experience for org switcher and billing status
- Color contrast in dark mode — design token requirements

### 7. L1 / L2 / L3 mapping

| ID | 2026 L1 (starter demo) | 2026 L2 (production) | 2026 L3 |
|----|------------------------|----------------------|---------|

Can L1 claim Partial on P1 with documented audit plan?

### 8. User expectations research

Find **user reviews, Reddit, HN, G2** complaints about B2B SaaS admin UX related to:

- Slow dashboards
- Inaccessible settings
- Poor keyboard support

What makes users call a product "enterprise-grade" vs "hacky"?

## Output format

1. Executive summary — a11y/perf bar for B2B SaaS starters (2026)
2. WCAG 2.2 AA checklist mapped to typical SaaS screens (auth, settings, billing, members)
3. Automated testing recommendation (tools + CI integration)
4. Performance benchmarks (bundle size, CWV ranges for admin apps)
5. L1/L2/L3 mapping (P1–P10)
6. Proposed rubric v1.1 changes (e.g., axe in CI as Should for L2)
7. Bibliography (W3C, Deque, web.dev, EAA official sources)

## Source priorities

- w3.org WAI WCAG 2.2 specification
- web.dev Core Web Vitals documentation (current thresholds)
- European Accessibility Act official guidance
- Angular accessibility guide
- Playwright accessibility testing docs
- Real VPAT examples from major SaaS vendors (if public)

## Constraints

- Admin UIs may legitimately score lower Lighthouse than marketing pages — explain why.
- Distinguish **legal compliance** from **good practice**.
