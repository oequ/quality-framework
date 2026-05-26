# Angular platform (2025–2026)

Modern Angular: standalone components, signals, built-in control flow, functional guards.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **NG1** | **Zoneless runtime.** No `zone.js` in `angular.json` / polyfills. | Should (L1) · **Must for L2** | Config inspection | Target for 2026 performance; document if not yet adopted. |
| **NG2** | **Zoneless bootstrap.** `provideZonelessChangeDetection()` in app config. | Should (L1) · **Must for L2** | TypeScript | Pair with NG1. |
| **NG3** | **Standalone-only.** No new NgModules; components/directives/pipes are standalone. | Must | ESLint | Group via Nx libs, not NgModules. |
| **NG4** | **Signal inputs/outputs.** Use `input()`, `input.required()`, `output()`, `model()`—not `@Input` / `@Output`. | Must | ESLint / review | New code should not add decorator I/O. |
| **NG5** | **Resource API for async data.** Prefer `resource()` / `httpResource()` over manual `subscribe` in components. | Should | Manual / ESLint | Port methods return Promises or Observables compatible with `resource` loaders. |
| **NG6** | **Derived state via signals.** Use `computed()` and `linkedSignal()` for dependent state—avoid updating fields inside subscriptions. | Must | Code review | `toSignal()` for form streams; `.subscribe()` only for imperative side effects. |
| **NG7** | **Typed reactive forms.** `FormGroup<T>` / typed controls for settings, billing, invite forms. | Must | TypeScript | Signal Forms (NG13) are the L3 evolution. |
| **NG8** | **Functional guards.** `canActivateFn` / functional interceptors—not class-based guards. | Must | TypeScript | Combine with `inject()` for ports. |
| **NG9** | **Built-in control flow.** `@if`, `@for`, `@switch`—not `*ngIf` / `*ngFor` in new templates. | Must | ESLint | Better type checking and compile perf. |
| **NG10** | **`track` in `@for`.** Unique `track` expression on all lists. | Must | Compiler | Critical for members tables and long lists. |
| **NG11** | **Lazy routes.** Feature routes use `loadComponent` / `loadChildren`. | Must | Bundler analysis | L3: lazy heavy services via `injectAsync()`. |
| **NG12** | **No `markForCheck`.** No `ChangeDetectorRef.markForCheck()` in new code. | Must | ESLint | Signals + zoneless make this unnecessary. |
| **NG13** | **Signal Forms (optional).** New data-entry flows may use `@angular/forms/signals` when stable in your Angular version. | Could | Code review | L3 differentiator; NG7 remains L1/L2 baseline. |

## L2 gate reminder

Claiming **L2 Production-ready** requires **NG1 and NG2 Pass** (zoneless), in addition to score and other domain gates. See [maturity.md](../maturity.md).

[← Rubric index](./README.md)
