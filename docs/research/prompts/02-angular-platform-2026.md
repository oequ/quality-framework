# Deep Research — Angular platform 2026 (NG1–NG12)

Weight: 15% of total score. L1 gate: all Must criteria must pass.

---

## Role

You are an Angular platform engineer and Google Developer Expert (or equivalent depth) tracking **Angular 19–21+** roadmap, signals, and migration patterns through **2026**.

## Context

Quality Framework v1.0 Angular criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| NG1 | No `zone.js` in polyfills | Should |
| NG2 | `provideZonelessChangeDetection()` | Should |
| NG3 | Standalone-only (no new NgModules) | Must |
| NG4 | Signal `input()` / `output()` — no decorators | Must |
| NG5 | `resource()` / `httpResource()` for async data | Should |
| NG6 | Derived state via `computed()`, not subscriptions | Must |
| NG7 | Typed reactive forms (`FormGroup<T>`) | Must |
| NG8 | Functional guards (`canActivateFn`) | Must |
| NG9 | Built-in control flow (`@if`, `@for`, `@switch`) | Must |
| NG10 | `track` in all `@for` loops | Must |
| NG11 | Lazy routes (`loadComponent`) | Must |
| NG12 | No `markForCheck()` in new code | Should |

Example reference stack: Angular 21, standalone bootstrap, signals widely adopted, zone.js may still be present, headless UI library, Nx monorepo.

## Research questions

### 1. 2026 Angular baseline for new B2B projects

What does the **Angular team** and major consultancies recommend as the default stack for greenfield apps in 2026?

- Zoneless: default, recommended, or optional?
- Signals vs RxJS: division of responsibility in production apps
- Resource API maturity — production-ready or still evolving?
- Signal forms status (developer preview vs stable)

Cite angular.dev, RFCs, changelog, and Angular v21+ release notes.

### 2. Zoneless adoption curve

Deep dive on **NG1, NG2, NG12**:

- Percentage of new Angular projects zoneless (surveys, npm trends, CLI defaults if any)
- Breaking changes teams hit (third-party libs, tests, CDK)
- Is "zoneless in 2026" a **Should** or becoming **Must** for L2?
- Performance evidence (LCP, TTI, bundle size)

### 3. Signal-first component API

Evaluate **NG4, NG6, NG5** against community practice:

- Migration completion timelines (@Input/@Output deprecation narrative)
- `toSignal()` / `linkedSignal()` / `effect()` best practices and pitfalls
- When `subscribe()` is still acceptable (imperative side effects, third-party widgets)
- `resource()` vs manual loading state — patterns in 2026 production code

### 4. Forms in 2026

Research **NG7**:

- Typed reactive forms — standard pattern examples
- Signal-based forms roadmap — should rubric add signal forms as Could?
- Comparison with React Hook Form / TanStack Form expectations from buyers crossing stacks

### 5. Routing and lazy loading

**NG11** in context of 2026:

- `loadComponent` vs route-level code splitting with Vite/esbuild
- Initial bundle budgets considered acceptable for admin SaaS UIs
- Preloading strategies for logged-in apps

### 6. Developer experience and AI coding assistants

How do **AGENTS.md / Cursor rules** interact with Angular conventions?

- Are signal-first rules enforceable via ESLint in 2026?
- What mistakes do AI assistants make on Angular starters (NgModule regression, missing track, untyped forms)?

### 7. Buyer / developer expectations

When evaluating an Angular starter in 2026, what makes developers say:

- "This is modern" vs "This is legacy"?
- Impact on hiring (junior dev onboarding)

### 8. L1 / L2 / L3 mapping

| ID | 2026 L1 | 2026 L2 | 2026 L3 | Notes |
|----|---------|---------|---------|-------|

Recommend whether NG1/NG2 should move from Should → Must for L2 gate.

## Output format

1. Executive summary — **minimum modern Angular bar in May 2026**
2. Zoneless section with adoption data and recommendation
3. Signals / Resource API / forms — state of the art
4. L1/L2/L3 table (NG1–NG12) with proposed rubric changes
5. ESLint/automation tools available in 2026 to enforce criteria
6. Common starter anti-patterns (still using NgModules, *ngFor, class guards)
7. Bibliography

## Source priorities

- angular.dev (official docs, current version)
- Angular GitHub blog, release notes v19–v21+
- NgConf / Angular Connect 2024–2026 talks
- nx.dev Angular plugin guidance
- State of JS / State of Angular surveys if available
- Production case studies (Shopify, Google internal if public, enterprise blogs)

## Constraints

- Do not conflate AngularJS with Angular.
- Separate **starter template** pragmatism from **Google internal** standards.
- Note SSR/hydration interactions with zoneless where relevant.
