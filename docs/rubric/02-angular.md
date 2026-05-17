# Angular platform (2025–2026)

Modern Angular: standalone components, signals, built-in control flow, functional guards. Some items are **aspirational** for teams still migrating.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **NG1** | **Zoneless runtime.** No `zone.js` in `angular.json` / polyfills. | Should | Config inspection | Target for 2026 performance; document if not yet adopted. |
| **NG2** | **Zoneless bootstrap.** `provideZonelessChangeDetection()` in app config (when on Angular versions that support it). | Should | TypeScript | Pair with NG1; skip if still on zone.js intentionally. |
| **NG3** | **Standalone-only.** No new NgModules; components/directives/pipes are standalone. | Must | ESLint | Group via Nx libs, not NgModules. |
| **NG4** | **Signal inputs/outputs.** Use `input()`, `input.required()`, `output()`, `model()`—not `@Input` / `@Output`. | Must | ESLint / review | New code should not add decorator I/O. |
| **NG5** | **Resource API for async data.** Prefer `resource()` / `httpResource()` over manual `subscribe` in components. | Should | Manual / ESLint | Port methods return Promises compatible with `resource` loaders. |
| **NG6** | **Derived state via `computed()`.** Avoid updating local fields inside subscriptions. | Must | Code review | Especially with port-backed `resource()`. |
| **NG7** | **Typed reactive forms.** Strictly typed `FormGroup` / controls (or signal forms when stable). | Must | TypeScript | Settings, billing, invite forms. |
| **NG8** | **Functional guards.** `canActivateFn` / functional interceptors—not class-based guards. | Must | TypeScript | Combine with `inject()` for ports. |
| **NG9** | **Built-in control flow.** `@if`, `@for`, `@switch`—not `*ngIf` / `*ngFor` in new templates. | Must | ESLint | Better type checking and compile perf. |
| **NG10** | **`track` in `@for`.** Unique `track` expression on all lists. | Must | Compiler | Critical for members tables and long lists. |
| **NG11** | **Lazy routes.** Feature routes use `loadComponent` / `loadChildren`. | Must | Bundler analysis | Keeps initial bundle smaller. |
| **NG12** | **No `markForCheck`.** No `ChangeDetectorRef.markForCheck()` in new code (stricter when zoneless). | Should | ESLint | Signals + OnPush should make this unnecessary. |

[← Rubric index](./README.md)
