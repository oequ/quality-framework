# Architecture & boundaries

Hexagonal **ports & adapters** in an Nx monorepo: framework-agnostic contracts, swappable infrastructure, feature-sliced libraries.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **A1** | **Framework-free port contracts.** `libs/ports` has no imports from `@angular/*` or UI frameworks. Port abstractions are pure TypeScript—prefer **abstract classes** as DI tokens (not `InjectionToken` from `@angular/core`). `rxjs` `Observable` in port contracts is allowed for stream semantics; document if used. | Must | ESLint restricted imports / review | Interfaces alone are erased at runtime; abstract classes work as Angular DI tokens without `@angular/core`. |
| **A2** | **Nx module boundaries.** `@nx/enforce-module-boundaries` configured with real `depConstraints` (not wildcard) and run in CI. | Must | Automated (CI: lint) | e.g. `type:feature` cannot import `type:adapter`; only `type:port`. |
| **A3** | **Injection tokens.** Ports consumed only via DI token (abstract class or `InjectionToken` defined outside `libs/ports`). | Must | Automated (TS/ESLint) | Swap implementations in `app.config` / environment providers without changing components. |
| **A4** | **Mock adapters isolated.** Dedicated `libs/adapters-mock` (or similar) for demo/local run. | Must | Manual (code review) | UI runs without production backend. |
| **A5** | **Shell isolation.** `libs/shell` (layout, nav) does not depend on feature internals. | Must | Nx dependency graph | Shell aggregates routes and chrome only. |
| **A6** | **Acyclic dependencies.** Dependency flow points inward toward domain/ports. | Must | ESLint / Nx graph | No feature ↔ adapter cycles. |
| **A7** | **Public API barrels.** Library `index.ts` exports only intentional surface. | Should | TypeScript / review | Prevents deep imports of private helpers. |
| **A8** | **Typed errors.** Adapters return `Result<T, E>` or typed error unions—not bare `any` throws. | Should | TypeScript | UI maps errors to messages without `catch (e: any)`. |
| **A9** | **DTO mapping in adapters.** External API shapes mapped to domain models in adapters only. | Should | Manual (code review) | Components use `Organization`, not vendor DTO types. |
| **A10** | **Domain vs state separation.** Business invariants not mixed into UI state stores. | Could | Architecture review | Seat limits, roles validated in domain or ports layer. |
| **A11** | **Feature-sliced libraries.** Code grouped by domain (`features-auth`, `features-org`), not by technical type only. | Must | Nx workspace layout | Each feature lib owns its routes/components for that domain. FSD layers (`entity`, `widget`) are L3 optional. |
| **A12** | **Design system boundary.** Features use primitives from `libs/ui` / design system; shared patterns not re-styled ad hoc. | Must | Manual (code review) | Consistent Spartan/Helm (or your DS) usage. |
| **A13** | **Adapter contract tests.** Shared behavioral test suite runs against mock and production adapter implementations for the same port. | Should | CI | Proves mock/prod parity; fast CI on in-memory adapters. |

## A1 migration note (v1.1)

If your ports currently use `InjectionToken` from `@angular/core`:

1. Convert port interfaces to **abstract classes** with method signatures.
2. Provide adapters with `extends` / `implements` the abstract class.
3. Register `{ provide: AuthPort, useClass: SupabaseAuthAdapter }` (example).

See [research/01-architecture-summary.md](../research/01-architecture-summary.md).

[← Rubric index](./README.md)
