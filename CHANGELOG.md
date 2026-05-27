# Changelog

All notable changes to Quality Framework documentation are documented here.

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [1.3.0] - 2026-05-27

### Added

- Research summaries: [SaaS domain](./docs/research/09-saas-domain-summary.md), [UX](./docs/research/07-ux-design-system-summary.md), [Documentation & OSS](./docs/research/08-documentation-oss-summary.md)
- **SaaS8–SaaS12** — audit log, API keys, metering, SSO, export/deletion
- **U11–U13** — dark mode, i18n, optimistic UI
- **D9–D10** — README credibility, published QUALITY.md self-assessment
- L2 gates: **SaaS5**, **U4**, **U11**, **D3** (Scorecard ≥ 6.5), **D6**, **D10**

### Changed

- **SaaS5** — promoted from Should to **Must**
- **SaaS2, SaaS6** — tenant routing tiers, token invites with seat reservation
- **D1, D3** — AGENTS.md schema; Scorecard Should with L2 score threshold
- [docs/maturity.md](./docs/maturity.md), [docs/implementation.md](./docs/implementation.md) — v1.3 guidance

### Notes

- All nine rubric domains now have research summaries; run synthesis before v2.0
- Re-score SaaS, UX, and Documentation when upgrading from v1.2

## [1.2.0] - 2026-05-27

### Added

- Research summaries: [Testing & CI](./docs/research/04-testing-ci-summary.md), [Security](./docs/research/05-security-summary.md), [Performance & a11y](./docs/research/06-performance-a11y-summary.md)
- **T12** — dependency release cooldown (Should)
- **T13** — ephemeral PR preview environments (Could)
- **T14** — visual regression on design system (Could)
- **S11** — SAST security ESLint plugins in CI (Should)
- **P11** — WCAG 2.4.11 Focus Not Obscured (Must)
- L2 gates: **S1, S2, S5** (production security path); **P1** (axe CI on primary flows); **P11**; **T1** mock-adapter E2E depth; **T8** ports/adapters coverage

### Changed

- **T1** — L2 mock-adapter E2E on PR; L3 staging smoke with production adapters
- **S1, S5** — explicit demo-tier vs production-tier notes (aligns with ASVS / research)
- **P1** — L1 Partial conformance with roadmap; L2 requires automated axe gate
- **T7, T8, T9** — supply-chain hardening, ports-only coverage, Lighthouse on public surfaces only
- [docs/maturity.md](./docs/maturity.md), [docs/implementation.md](./docs/implementation.md), [docs/anti-patterns.md](./docs/anti-patterns.md) — v1.2 guidance

### Notes

- **T11** remains adapter contract tests (unchanged from v1.1); raw testing research proposed a different T11 — see [04-testing-ci-summary.md](./docs/research/04-testing-ci-summary.md)
- Re-score Security, Testing, and Performance categories when upgrading from v1.1

## [1.1.0] - 2026-05-26

### Added

- [docs/evolution.md](./docs/evolution.md) — how the framework evolves; research program; v2.0 candidates
- [docs/research/](./docs/research/) — deep research reports and summaries (Architecture, Angular, TypeScript)
- **A13** — adapter contract tests (Should)
- **T11** — adapter contract tests in CI (Should)
- **NG13** — Signal Forms (Could)
- **TS11** — branded domain IDs (Should)
- L2 explicit gates for zoneless (NG1, NG2), A1 v1.1, TS8 runtime config
- Partial Pass rules in [maturity.md](./docs/maturity.md)

### Changed

- **A1** — redefined: framework-free port **contracts**; abstract classes as DI tokens; RxJS Observable allowed for streams with documentation
- **NG1, NG2** — documented as **Must for L2** (remain Should for L1 scoring weight)
- **NG6** — includes `linkedSignal()`; `toSignal()` preferred over subscribe for form state
- **TS1** — documents L2 strict flags (`noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`, `verbatimModuleSyntax`)
- **TS8** — L1 vs L2 split (build-time vs runtime configuration)
- **TS9** — structured logging port/abstraction, not only banning `console.log`
- [docs/standard.md](./docs/standard.md) — non-negotiables aligned with v1.1
- [docs/anti-patterns.md](./docs/anti-patterns.md) — conditional mock/prod imports, InjectionToken in ports, effect() misuse
- [docs/implementation.md](./docs/implementation.md) — abstract-class ports, environment-specific providers

### Notes

- Criterion **IDs unchanged** — existing self-assessments remain valid; re-score A1 and new criteria
- Security, SaaS, UX research planned for v1.2

## [1.0.0] - 2026-05-17

### Added

- Initial public release of Quality Framework v1.0
- [docs/standard.md](./docs/standard.md) — hybrid quality model (rubric + maturity + CI + AGENTS.md)
- [docs/maturity.md](./docs/maturity.md) — L1 / L2 / L3 levels and category weights
- [docs/scoring.md](./docs/scoring.md) — 0–1000 scoring guide
- [docs/rubric/](./docs/rubric/) — nine domain rubrics (100+ criteria)
- [docs/implementation.md](./docs/implementation.md) — Nx monorepo mapping
- [docs/roadmap.md](./docs/roadmap.md) — 90-day adoption plan
- [docs/anti-patterns.md](./docs/anti-patterns.md) — legacy practices to avoid
- [docs/bibliography.md](./docs/bibliography.md) — curated sources
- [templates/](./templates/) — AGENTS.md, self-assessment, PR template
- MIT license

### Notes

- Zoneless criteria (NG1, NG2) published as **Should** to reflect common migration state
- Tenant routing (SaaS2) allows active-org model as alternative to `/org/:id` routes

[1.3.0]: https://github.com/oequ/quality-framework/releases/tag/v1.3.0
[1.2.0]: https://github.com/oequ/quality-framework/releases/tag/v1.2.0
[1.1.0]: https://github.com/oequ/quality-framework/releases/tag/v1.1.0
[1.0.0]: https://github.com/oequ/quality-framework/releases/tag/v1.0.0
