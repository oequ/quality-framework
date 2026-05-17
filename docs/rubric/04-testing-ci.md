# Testing & CI

Verification pyramid, pipeline hygiene, and supply-chain basics.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **T1** | **E2E critical paths.** Playwright (or equivalent) for login, org switch, billing/members smoke. | Must | CI | Runs against mock adapters in demo app. |
| **T2** | **Vitest (or modern unit runner).** Prefer Vitest over Karma for new unit tests. | Should | Config | Fast port/utility tests without TestBed. |
| **T3** | **Remote CI cache.** Nx Cloud or equivalent for monorepo PR speed. | Should | CI config | Optional for small repos; valuable at scale. |
| **T4** | **Framework-free port tests.** Port logic/types testable without Angular TestBed. | Must | Architecture review | Pure functions and adapter unit tests. |
| **T5** | **UI tests use mock ports.** Component tests inject mock adapters, not `HttpTestingController` for every screen. | Should | Code review | Aligns with ports architecture. |
| **T6** | **Bundle budgets.** `angular.json` (or build) budgets enforced in CI. | Must | CI build | Prevents accidental heavy imports. |
| **T7** | **Dependabot / Renovate.** Automated dependency PRs; audit in CI or policy. | Must | GitHub | Supply-chain hygiene. |
| **T8** | **Coverage thresholds.** Meaningful coverage on ports/adapters/mappers (e.g. >80%). | Should | Vitest coverage | UI coverage optional. |
| **T9** | **Lighthouse CI.** CWV and a11y budgets on demo deploy. | Could | CI | Proves performance/a11y investment. |
| **T10** | **Parallel CI jobs.** Lint, test, build, e2e as separate parallel steps. | Must | CI config | Faster feedback on PRs. |

[← Rubric index](./README.md)
