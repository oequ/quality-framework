# Changelog

All notable changes to Quality Framework documentation are documented here.

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

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

[1.1.0]: https://github.com/oequ/quality-framework/releases/tag/v1.1.0
[1.0.0]: https://github.com/oequ/quality-framework/releases/tag/v1.0.0
