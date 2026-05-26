# Deep Research — Testing & CI (T1–T10)

Weight: 10% of total score. L2 requires E2E on critical paths.

---

## Role

You are a staff engineer specializing in **CI/CD**, **test strategy**, and **supply-chain security** for JavaScript monorepos shipping B2B SaaS products.

## Context

Quality Framework v1.0 Testing & CI criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| T1 | E2E critical paths (Playwright or equivalent) | Must |
| T2 | Vitest (or modern unit runner) | Should |
| T3 | Remote CI cache (Nx Cloud or equivalent) | Should |
| T4 | Framework-free port tests (no TestBed) | Must |
| T5 | UI tests inject mock ports | Should |
| T6 | Bundle budgets enforced in CI | Must |
| T7 | Dependabot / Renovate | Must |
| T8 | Coverage thresholds on ports/adapters (>80%) | Should |
| T9 | Lighthouse CI | Could |
| T10 | Parallel CI jobs (lint, test, build, e2e) | Must |

Our stack: GitHub Actions, Nx 22, Vitest for ports, Playwright for demo + web (@web tag with Supabase), Dependabot configured, parallel jobs.

## Research questions

### 1. 2026 testing pyramid for B2B SaaS frontends

What is the **consensus test strategy** for admin/control-plane UIs?

- E2E scope: which flows are non-negotiable (auth, tenancy switch, billing, RBAC)?
- Unit vs integration vs E2E cost/benefit in 2026
- Visual regression — table-stakes or optional?
- Contract testing between frontend ports and backend (Pact, OpenAPI)

### 2. Playwright as standard (T1)

- Playwright vs Cypress market share and enterprise adoption (2025–2026 data)
- Best practices: tagging (@web), auth storage state, parallel sharding
- Running Supabase-dependent E2E in CI — patterns and flakiness mitigation
- Minimum E2E count for **credible L1** vs **L2**

### 3. Unit testing in Angular 21+ (T2, T4, T5)

- Vitest + AnalogJS vs Jest — 2026 recommendation
- Testing signal components without TestBed — maturity
- Ports-and-adapters testing: pure functions vs adapter integration tests
- Should component tests be required for L2?

### 4. CI performance and caching (T3, T10)

- Nx Cloud vs GitHub Actions cache vs self-hosted runners — cost/performance 2026
- Affected-only CI — expected for starters?
- Typical PR feedback time targets buyers expect (<10 min?)

### 5. Supply chain (T7)

- Dependabot vs Renovate — OpenSSF recommendation
- npm audit / OSV-Scanner / Socket.dev — should rubric add explicit vulnerability scanning Must?
- Pinning vs ranges for starter templates

### 6. Quality gates (T6, T8, T9)

- Bundle budget numbers for Angular 21 admin apps (initial JS KB ranges)
- Coverage thresholds — meaningful vs vanity metrics
- Lighthouse CI adoption — when does it matter for B2B (marketing site vs app shell)?

### 7. Buyer expectations

What **CI badges and README signals** do technical buyers look for?

- "CI passing" badge insufficient?
- Expectation of public CI logs, E2E videos, preview deployments

### 8. L1 / L2 / L3 mapping

| ID | 2026 L1 | 2026 L2 | 2026 L3 |
|----|---------|---------|---------|

Should T1 E2E move from Must-with-mock-only to Must-with-production-adapter-smoke for L2?

## Output format

1. Executive summary — minimum CI/test bar for SaaS starters (2026)
2. Recommended E2E checklist (flows × priority)
3. CI pipeline blueprint (jobs, parallelism, caching)
4. L1/L2/L3 mapping (T1–T10)
5. Proposed new criteria for rubric v1.1 (supply chain, preview deploys)
6. Anti-patterns (E2E-only, no unit tests on domain logic, flaky Supabase CI)
7. Bibliography

## Source priorities

- Playwright documentation and State of Testing surveys
- Nx CI recipes (current)
- OpenSSF Scorecard, SLSA, npm security advisories
- GitHub Actions performance benchmarks
- Engineering blogs from Vercel, Supabase, Stripe on testing B2B apps

## Constraints

- GitHub Actions as primary CI unless data strongly favors alternatives.
- Separate **OSS starter** CI from **enterprise compliance** CI (SOC2 pipelines).
