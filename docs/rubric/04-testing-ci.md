# Testing & CI

Verification trophy, pipeline hygiene, and supply-chain basics. See [research summary](../research/04-testing-ci-summary.md).

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **T1** | **E2E critical paths.** Playwright for login, org/tenant switch, billing/members smoke. **L1:** mock-only, basic navigation. **L2:** mock adapters — auth, tenant isolation, RBAC (no live billing DB on every PR). **L3:** staging smoke with production adapters. | Must | CI | Tag live-backend suites (e.g. `@web`); fork-safe mock CI for OSS. |
| **T2** | **Vitest (or modern unit runner).** Default over Karma; zoneless-friendly. | Should | Config | L2 gate: Vitest configured for port and feature tests. |
| **T3** | **Remote CI cache.** Nx Cloud or equivalent for monorepo PR speed. | Should | CI config | Valuable at scale. |
| **T4** | **Framework-free port tests.** Port logic testable without Angular TestBed. | Must | Architecture review | Target ~50% of test effort on ports/adapters. |
| **T5** | **UI tests use mock ports.** `TestBed.overrideComponent` / mock adapter providers — not live HTTP per screen. | Should | Code review | Avoid domain rules only in component tests. |
| **T6** | **Bundle budgets.** `angular.json` budgets enforced in CI (e.g. initial error ≤ 250KB gzipped). | Must | CI build | Zoneless apps often ~155KB; tighten warnings over time. |
| **T7** | **Dependency automation & audit.** Dependabot/Renovate; lockfile pinned; optional OSV-Scanner / Scorecard on L3. | Must | GitHub | Pin GitHub Actions to full SHAs; see T12 for cooldown. |
| **T8** | **Coverage on ports/adapters.** Meaningful threshold (e.g. ≥80%) on `libs/ports` and `libs/adapters-*` — not vanity global UI %. | Should | Vitest coverage | L2 gate: ports/adapters coverage enforced. |
| **T9** | **Lighthouse CI (public surfaces).** CWV on marketing/landing deploy — not the sole metric for authenticated admin UI (use P1 axe there). | Should | CI | Pair with P1 for app shells. |
| **T10** | **Parallel CI jobs.** Lint, test, build, e2e as separate parallel steps; Nx affected on PRs. | Must | CI config | Target PR feedback &lt; 10 minutes. |
| **T11** | **Adapter contract tests.** Same behavioral tests against mock and production adapters (see A13). | Should | CI | Fast lane mock; optional nightly/staging lane. |
| **T12** | **Dependency release cooldown.** Renovate/Dependabot waits 3–5 days before merging new releases (reduces supply-chain zero-days). | Should | Bot config | Complements T7. |
| **T13** | **Ephemeral PR previews.** Deploy preview of app shell per PR (optional DB seed). | Could | CI / hosting | Buyer due diligence; not required for L1. |
| **T14** | **Visual regression.** Snapshot tests for design-system primitives — not full admin dashboards. | Could | CI | High false-positive rate on data tables. |

[← Rubric index](./README.md)
