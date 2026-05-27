# Implementation mapping

Where to apply top **Must** criteria in a typical Nx + Angular + ports monorepo (e.g. `apps/demo`, `libs/ports`, `libs/adapters-mock`, `libs/features-*`, `libs/shell`, `libs/ui`).

## 1. Architecture & Nx boundaries

**Where:** Root ESLint config (`eslint.config.mjs`).

**Action:** Configure `@nx/enforce-module-boundaries` with **real** `depConstraints` (no wildcard `*` → `*`). Example layers:

- `type:ports` — leaf; ports only
- `type:adapters` — may import `type:ports`, `type:adapters`
- `type:feature` — may import `type:ports`, `type:ui`, `type:shell`, `type:feature`; **not** `type:adapters`
- `type:app` — may wire adapters in `app.config` only

**A1 (v1.1):** Define ports as **abstract classes** in `libs/ports` (no `@angular/core`). Register `{ provide: OrgPort, useClass: SupabaseOrgAdapter }`.

**Mock/prod:** Use separate `environment.*.ts` or provider files so demo builds never statically import production SDKs.

**Docs:** Mirror rules in root `AGENTS.md` so AI tools do not suggest illegal imports.

## 2. Angular signals & async data

**Where:** `apps/*/src/app/app.config.ts`, feature components.

**Actions:**

- Prefer `input()` / `output()` over decorators in new code.
- Load data via `resource()` calling port methods:

```typescript
private readonly org = inject(ORG_PORT);

readonly members = resource({
  params: () => ({ orgId: this.organizationId(), refresh: this.refresh() }),
  loader: async ({ params }) => {
    const result = await this.org.getMembers(params.orgId);
    if (!result.ok) throw new Error(result.error.message);
    return result.data;
  },
});
```

**Zoneless (L2 Must):** Add `provideZonelessChangeDetection()` and remove `zone.js` from build config before claiming L2.

**Contract tests (A13/T11):** Shared Vitest suite imported by both `adapters-mock` and `data-access-*` test targets.

## 3. Security & HTTP

**Where:** Server headers (hosting), `app.config.ts`, `libs/shell` interceptors, production adapters.

**Actions:**

- **Demo (L1):** Document meta CSP and `localStorage` session as non-production in `docs/QUALITY.md`.
- **Production (L2):** HTTP `Content-Security-Policy` with nonces (`ngCspNonce` / `CSP_NONCE`); no `unsafe-inline` scripts.
- Cookie/BFF or `@supabase/ssr` path — not raw JWT in `localStorage` (S5).
- Central auth interceptor with **single-flight** refresh on 401 (S7); CSRF when using cookies (S6).
- Ban unreviewed `bypassSecurityTrustHtml`; DOMPurify for rich HTML (S3).
- ESLint security plugins in CI (S11).
- Document: **route guards = UX**; API/RLS enforces authZ (S9).

## 4. Design system & Tailwind v4

**Where:** `apps/demo/src/styles.css`, `libs/ui`, `angular.json` / Vite config.

**Actions:**

- `@import "tailwindcss"` and `@tailwindcss/vite` (v4 pattern).
- Feature components consume `libs/ui` primitives (dialog, select, table).
- Enforce min touch targets and `focus-visible` in shared components.

## 5. Testing strategy (v1.2)

**Where:** `libs/ports`, `libs/adapters-*`, `apps/*-e2e`, `.github/workflows/`.

**Testing trophy (target mix):**

| Layer | Tool | What to test |
|-------|------|----------------|
| Ports/adapters | Vitest, no TestBed | Domain rules, mappers, contract suite (T4, T8, T11) |
| Components | Vitest + TestBed | UI with `overrideComponent` + mock adapters (T5) |
| E2E | Playwright | Critical paths on **mock adapters** for PR CI (T1 L2) |

**Playwright practices:**

- `data-testid` selectors (not `ng-reflect-*`).
- `storageState` for auth; `--shard` for parallel CI.
- Tag live-backend suites (`@web`); keep fork PRs mock-only.

**Supply chain (T7, T12):** Dependabot/Renovate with 3-day cooldown; pin GHA to commit SHAs.

## 6. Accessibility & performance (v1.2)

**Where:** `libs/shell`, `libs/ui`, `apps/*-e2e`, global styles.

**Actions:**

- `@axe-core/playwright` on auth, settings, billing, members in CI (P1 L2).
- `scroll-padding-top` for sticky headers (P11); 24×24px targets on icon buttons (P2).
- Dialog focus trap + Esc + focus restore (P4) via Spartan/CDK.
- Toast `aria-live` polite vs assertive (P7).
- `provideZonelessChangeDetection()` for INP on dense admin UIs (links NG1/NG2).
- Lighthouse CI on **marketing/landing** only (T9) — not the sole admin metric.

## 7. AI context & CI

**Where:** Repository root, `.github/workflows/`.

**AGENTS.md** (minimal example):

```markdown
# AGENTS.md

## Commands
- `npx nx serve demo` — dev server
- `npx nx run-many -t lint test e2e` — verify before PR

## Architecture
- Ports & adapters. NEVER import adapters from feature libraries.
- Inject ORG_PORT, AUTH_PORT, BILLING_PORT — never Supabase/HttpClient in components.

## Angular
- Standalone components; signal inputs; @if/@for; resource() for port data.
```

**CI pipeline (minimal):**

1. `nx format:check`
2. `nx run-many -t lint` (include security ESLint)
3. `nx run-many -t test` — enforce ports/adapters coverage on L2 (T8)
4. `nx build demo`
5. `nx e2e demo-e2e` (mock adapters)
6. axe-playwright on primary flows (L2+)

Optional: OpenSSF Scorecard, Lighthouse CI on public deploy, nightly `@web` E2E against staging (L3).

## 8. SaaS features (v1.3)

| Feature | Port | Typical UI location |
|---------|------|---------------------|
| Org switcher | `OrgPort` | `libs/shell` — invalidate caches on switch |
| Onboarding | `OrgPort` / `AuthPort` | `libs/features-org` — no blank dashboard (SaaS5) |
| Members | `OrgPort` | Invite tokens, seat reservation at invite time (SaaS6) |
| Billing | `BillingPort` | Checkout, portal, past_due banners (SaaS3–SaaS4) |
| Auth | `AuthPort` | `libs/features-auth` |

Swap `provideDemoAdapters()` vs production providers only in `app.config.ts`.

**Tenancy (SaaS2):** Document active-org vs `/org/:id` in README; L2 prefers route-scoped org with guards.

**Compliance (SaaS12):** Wire export/delete flows to backend; document L1 support-email fallback in QUALITY.md if not automated.

## 9. Documentation & README (v1.3)

- **AGENTS.md:** commands, Nx tags, forbidden adapter imports, permission boundaries (D1).
- **README:** live demo link, stack matrix, honest limitations, Scorecard badge (D9).
- **docs/QUALITY.md:** published self-assessment with evidence links (D10).
- **docs/adr/:** minimum ADRs for ports, auth, billing (D2).

## Related

- [roadmap.md](./roadmap.md) — phased adoption
- [rubric/](./rubric/README.md) — full criteria list
