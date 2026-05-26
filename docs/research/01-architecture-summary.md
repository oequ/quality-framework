# Research summary — Architecture & boundaries (May 2026)

Source: [Architecture & Boundaries for Enterprise Frontend SaaS Platforms.txt](./Architecture%20%26%20Boundaries%20for%20Enterprise%20Frontend%20SaaS%20Platforms.txt)

## Executive summary

In 2026, **hexagonal architecture + enforced Nx boundaries** is table-stakes for B2B SaaS frontends—not a differentiator. **Feature-Sliced Design (FSD)** layered with Nx tags is the enterprise norm. The main technical debate is **how to keep ports framework-free** while using Angular DI.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.1) |
|-------|----------------|----------------------|
| Ports & adapters | Required for any starter beyond MVP | Keep A2–A6, A11 Must |
| A1 framework-free | **Abstract classes** as DI tokens avoid `@angular/core` in `libs/ports` | **Redefine A1** |
| RxJS in ports | Pragmatically acceptable for streams (WebSocket, realtime) | Allow in A1 with documentation |
| Mock/prod swap | **Never** static-import both adapters in one `app.config` | Document in implementation.md |
| Contract testing | Same suite on mock + prod adapters | **Add A13, T11** (Should) |
| Error model | `Result<T,E>` / typed errors trending L2+ | A8 Should — align with PortResult |
| Buyer red flags | SDK in features, god `shared`, fake conditional mocks | anti-patterns.md |

## L1 / L2 / L3 (research view)

| Level | Architecture bar |
|-------|------------------|
| **L1** | Feature libs + ports; boundaries in CI (error on violation); mock adapter lib; honest demo/prod split |
| **L2** | Abstract-class ports; isolated mocks; DTO mapping in adapters; strict barrels; contract tests starting |
| **L3** | FSD topology via Nx Conformance; full contract-tested adapters; Result/Effect at boundaries |

## Top 5 actions for adopters

1. Refactor ports to **abstract classes** (not `InjectionToken` in ports layer).
2. Enforce **real** `depConstraints` in CI (not wildcard).
3. Environment-specific provider files (tree-shake prod SDK out of demo builds).
4. Mapper layer in adapters only (anti-corruption).
5. Shared contract tests for mock vs production adapters.

## Proposed future (v1.2+)

- Optional FSD tags (`type:entity`, `type:widget`) documented as L3 path.
- Nx Conformance mentioned in implementation guide.

[← Research index](./README.md)
