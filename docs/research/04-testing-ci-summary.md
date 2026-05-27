# Research summary — Testing & CI (May 2026)

Source: [High-Performance Continuous Integration and Testing Architecture for B2B SaaS Angular Monorepos.txt](./High-Performance%20Continuous%20Integration%20and%20Testing%20Architecture%20for%20B2B%20SaaS%20Angular%20Monorepos.txt)

## Executive summary

2026 B2B SaaS CI favors a **testing trophy**: ~50% framework-free port tests, ~35% mocked UI (TestBed + mock adapters), ~15% Playwright on critical paths. **Playwright** is the E2E standard; **Vitest** replaces Karma on Angular 21. PR pipelines target **&lt; 10 minutes** via Nx affected + sharding.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.2) |
|-------|----------------|----------------------|
| T1 E2E scope | L2: mock adapters only on PR; L3: staging smoke with prod adapters | Clarify T1 + L2/L3 gates |
| E2E matrix | Tenant isolation, auth switch, RBAC, billing (tagged `@web` for live backend) | Document in implementation.md |
| T8 coverage | ≥80% on **ports/adapters only** — not vanity global UI % | Clarify T8 |
| T6 budgets | Initial JS error &gt; 250KB (zoneless ~155KB typical) | Clarify T6 |
| T7 supply chain | Dependabot cooldown 3d, pin GHA to SHA, OSV-Scanner | Expand T7 |
| T9 Lighthouse | Marketing/landing only; admin validated via axe (P1) | Clarify T9 vs P1 |
| Contract tests | OpenAPI spec-first for most; Pact for microservices | Align T11 with A13 |
| Anti-patterns | E2E-only “ice cream cone”, `ng-reflect-*` selectors, shared DB flakes | anti-patterns.md |

## L1 / L2 / L3 (research view)

| ID | L1 | L2 | L3 |
|----|----|----|-----|
| T1 | Mock E2E: login + navigation | Mock adapters: auth, tenant isolation, billing | Staging E2E with prod adapters |
| T4 | Ports isolated from TestBed | Enforced via Nx boundaries | Same + contract tests |
| T7 | Dependabot/Renovate | Cooldown + pinned actions | OSV-Scanner / Scorecard block |
| T8 | 50% global (optional) | ≥80% ports/adapters | ≥90% domain layer |
| T9 | Manual Lighthouse | Lighthouse CI on marketing paths | CWV on PR for public surfaces |

## Proposed IDs (v1.2 — not in raw report numbering)

Raw report proposed **T11 = dependency cooldown**; v1.1 already uses **T11 = adapter contract tests**. v1.2 assigns:

- **T12** — dependency release cooldown (Should)
- **T13** — ephemeral PR preview environments (Could)
- **T14** — visual regression on design system (Could)

## Top actions for adopters

1. Playwright with `storageState`, sharding, `data-testid` (not `ng-reflect-*`).
2. Vitest for ports; TestBed + `overrideComponent` for UI with mock adapters.
3. Enforce port/adapters coverage gate; drop global 80% vanity targets.
4. Fork-safe CI: mock DB on public PRs; `@web` suite optional / nightly for Supabase.
5. README badges: Scorecard, coverage on ports, Playwright traces on failures.

[← Research index](./README.md)
