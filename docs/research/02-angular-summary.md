# Research summary — Angular platform (May 2026)

Source: [Angular Platform Architecture and Migration Patterns in 2026.txt](./Angular%20Platform%20Architecture%20and%20Migration%20Patterns%20in%202026.txt)

## Executive summary

Angular **21+** in 2026: **zoneless by default** for new workspaces, **signals-only** component API, **`resource()` / `httpResource()`** for async data, **Signal Forms** emerging for L3. Legacy NgModules, decorator I/O, and `*ngIf` are disqualifiers for “modern” labels.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.1) |
|-------|----------------|----------------------|
| Zoneless (NG1, NG2) | Default in new CLI; major perf gains | **L2 gate: Must** (remain Should for L1 scoring) |
| Signal I/O (NG4) | Decorators deprecated | Stay Must |
| subscribe → signals (NG6) | `toSignal` + `computed`; `linkedSignal` for dependent mutable state | Clarify NG6 |
| Resource API (NG5) | Production standard | Stay Should; L3 path to Must |
| Typed forms (NG7) | `FormGroup<T>` = L1/L2 floor | Stay Must |
| Signal Forms | Stable trajectory v21–22 | **Add NG13** (Could) |
| injectAsync (NG11) | Lazy service loading for L3 | Note under NG11 |
| ESLint | `no-uncalled-signals`, `prefer-inject` | implementation.md |
| AI | Angular MCP + AGENTS.md | D1 alignment |

## L1 / L2 / L3 (research view)

| ID | L1 | L2 | L3 |
|----|----|----|-----|
| NG1–NG2 | Should (zone.js may exist in legacy) | **Must** zoneless | Must |
| NG5 | Manual loading OK | resource() Should | httpResource Must |
| NG7 | FormGroup&lt;T&gt; | FormGroup&lt;T&gt; | Signal Forms |
| NG11 | loadComponent | loadComponent | + injectAsync |

## Anti-patterns called out

- NgModules / SharedModule imports in new code.
- `*ngIf` / `*ngFor` without migration plan.
- `@for` without `track`.
- `effect()` for derived state (use `computed` / `linkedSignal`).
- `markForCheck` in new code.
- Mutating plain fields in async callbacks under zoneless.

## Top actions for adopters

1. Add `provideZonelessChangeDetection()`; remove zone.js.
2. Enforce `@angular-eslint` signal rules in CI.
3. Migrate data loading to `resource()` calling ports.
4. Replace remaining feature-layer `subscribe` with `toSignal`.
5. Plan Signal Forms for new screens (L3).

[← Research index](./README.md)
