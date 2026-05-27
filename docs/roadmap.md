# 90-day adoption roadmap

Phased plan to move an Angular B2B SaaS monorepo toward **L2 Production-ready** using Quality Framework v1.4.

## Phase 1 — Weeks 1–4 (boundaries & AI readiness)

| Week | Focus | Deliverables |
|------|--------|--------------|
| 1 | Documentation | Root `AGENTS.md`; `docs/QUALITY.md`; pin **v1.4**; read [l2-gates.md](./l2-gates.md) |
| 2 | Static analysis | ESLint flat config; real `depConstraints`; CI lint on every PR |
| 3 | Ports (A1) | Abstract-class ports; no `@angular/core` in `libs/ports` |
| 4 | Angular modernization | Signal I/O, `@if`/`@for`; `toSignal`; `resource()` for async data |

## Phase 2 — Weeks 5–8 (automation, security, testing)

| Week | Focus | Deliverables |
|------|--------|--------------|
| 5 | CI/CD | Parallel jobs: lint, test, build; optional Nx remote cache |
| 6 | E2E | Playwright: auth, workspace switch, billing/members smoke on mock adapters |
| 7 | Zoneless (L2 gate) | `provideZonelessChangeDetection()`; remove zone.js |
| 8 | Security | HTTP CSP + nonces (S1/S2); cookie/BFF path (S5); SAST in CI (S11); document demo tier |
| 9 | Accessibility | `@axe-core/playwright` on primary flows (P1); P11 scroll-padding; focus/target size |

## Phase 3 — Weeks 9–12 (community & polish)

| Week | Focus | Deliverables |
|------|--------|--------------|
| 10 | OSS signals | OpenSSF Scorecard workflow; README badge with honest L1/L2 |
| 11 | Production adapter | Wire real backend adapter (e.g. Supabase) without feature changes |
| 12 | Contract tests | A13/T11 shared suite on mock + prod adapters |
| 13 | UX polish | Skeletons, empty states, toast a11y, responsive tables |
| 14 | Release | Semver tag; changelog; announce with self-assessment score |

## Prioritization tips

- **Do first:** A1–A3, A11, T1, D1, D4, SaaS1, SaaS3, SaaS6 — architecture and trust.
- **Do before claiming L2:** A2, S1+S2+S5, T6, T8 port coverage, mock-adapter E2E (T1), axe CI (P1+P11), NG1+NG2.
- **Defer Could items:** T9, D3, P8 until Must/Should are green.

## Measuring progress

Re-run [scoring.md](./scoring.md) monthly. Publish score delta in `docs/QUALITY.md`.

[← Implementation mapping](./implementation.md)
