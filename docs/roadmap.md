# 90-day adoption roadmap

Phased plan to move an Angular B2B SaaS monorepo toward **L2 Production-ready** using Quality Framework v1.0.

## Phase 1 — Weeks 1–4 (boundaries & AI readiness)

| Week | Focus | Deliverables |
|------|--------|--------------|
| 1 | Documentation | Root `AGENTS.md`; `docs/QUALITY.md` self-assessment; link to quality-framework v1.0 |
| 2 | Static analysis | ESLint flat config; `@nx/enforce-module-boundaries`; CI lint on every PR |
| 3 | Angular modernization | New code: signal I/O, `@if`/`@for`; no new NgModules |
| 4 | Async data | Migrate key screens to `resource()` + port loaders; reduce `subscribe` in templates |

## Phase 2 — Weeks 5–8 (automation, security, testing)

| Week | Focus | Deliverables |
|------|--------|--------------|
| 5 | CI/CD | Parallel jobs: lint, test, build; optional Nx remote cache |
| 6 | E2E | Playwright: auth, workspace switch, billing/members smoke on mock adapters |
| 7 | Security | CSP plan for production; CSRF config; document demo auth limitations |
| 8 | Accessibility | axe in CI or manual audit; fix focus/target size on primary flows |

## Phase 3 — Weeks 9–12 (community & polish)

| Week | Focus | Deliverables |
|------|--------|--------------|
| 9 | OSS signals | OpenSSF Scorecard workflow; README badge with honest L1/L2 |
| 10 | Production adapter | Wire real backend adapter (e.g. Supabase) without feature changes |
| 11 | UX polish | Skeletons, empty states, toast a11y, responsive tables |
| 12 | Release | Semver tag; changelog; announce with self-assessment score |

## Prioritization tips

- **Do first:** A1–A3, A11, T1, D1, D4, SaaS1, SaaS3, SaaS6 — architecture and trust.
- **Do before claiming L2:** A2, S1, S5 (production path), T6, full E2E, WCAG pass on core flows.
- **Defer Could items:** T9, D3, P8 until Must/Should are green.

## Measuring progress

Re-run [scoring.md](./scoring.md) monthly. Publish score delta in `docs/QUALITY.md`.

[← Implementation mapping](./implementation.md)
