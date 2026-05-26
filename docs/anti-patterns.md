# Anti-patterns (2026)

Legacy practices that **lower** your Quality Framework score. Do not introduce them in new code or PRs.

## 1. NgModules for new features

Grouping via `NgModule` instead of standalone components and Nx libraries. Use **standalone** + feature libs.

## 2. zone.js as default (without a plan)

Relying on Zone.js for change detection when targeting modern Angular performance. If you must keep zones, document why and set a migration milestone—do not claim full **NG1/NG2** pass.

## 3. Global store for simple CRUD

NgRx/Redux caching every HTTP list (invoices, members) when `resource()` + port methods suffice. Global signal stores are fine for **UI chrome** (theme, sidebar), not for every API response.

## 4. Leaky components

Injecting `HttpClient`, Supabase, Firebase, or Stripe directly in feature components. Inject **ports only**; SDKs live in adapters.

## 5. Class-based guards

`implements CanActivate` classes instead of `canActivateFn` functional guards.

## 6. Legacy Tailwind v3-only toolchain

Maintaining `tailwind.config.js` + PostCSS-only pipeline when on Tailwind v4—use CSS-first config and `@tailwindcss/vite` where applicable.

## 7. Checklist washing

PR templates with lint/test/docs checkboxes **not** backed by CI. Every architectural rule worth stating should be **machine-enforced** (especially import boundaries).

## 8. False maturity badges

README claims **L2 Production-ready** without published self-assessment, production auth, or boundary enforcement.

## 9. UI-only authorization

Hiding admin buttons without documenting that **server/RLS/API** must enforce permissions. Always document S9.

## 10. Vendor DTOs in templates

Binding templates to `SupabaseUser`, Stripe types, etc. Map to domain types in adapters first.

## 11. InjectionToken inside `libs/ports` (v1.1)

Importing `InjectionToken` from `@angular/core` in the ports layer. Prefer **abstract classes** as port tokens (see A1).

## 12. Conditional mock + prod adapter in one config

`useClass: isProd ? ProdAdapter : MockAdapter` with **both** adapters statically imported — bundles both SDKs. Use environment file replacement or separate provider files.

## 13. `effect()` for derived UI state

Using `effect()` to sync parent input → local state. Prefer `computed()` or `linkedSignal()` (NG6).

## 14. TypeScript `enum` for roles and status

Runtime enum emit and poor JSON ergonomics. Use string unions and `as const` objects (TS6).

## 15. Build-time-only config for production claims

`environment.prod.ts` file replacement without runtime `config.json` — blocks immutable Docker promote (TS8 L2).

---

Violations should be caught in code review and, where possible, ESLint/Nx rules. See [rubric/](./rubric/README.md) for positive criteria.
