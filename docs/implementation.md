# Implementation mapping

Where to apply top **Must** criteria in a typical Nx + Angular + ports monorepo (e.g. `apps/demo`, `libs/ports`, `libs/adapters-mock`, `libs/features-*`, `libs/shell`, `libs/ui`).

## 1. Architecture & Nx boundaries

**Where:** Root ESLint config (`eslint.config.mjs` or `.eslintrc.json`).

**Action:** Configure `@nx/enforce-module-boundaries` `depConstraints`, for example:

- `type:port` — may import only `type:util` (if any)
- `type:adapter` / `type:adapter-mock` — may import `type:port`
- `type:feature` — may import `type:port`, `type:ui`, `type:shell` (as designed); **not** `type:adapter`
- `type:ui` — presentation only; no adapters or features

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

**Zoneless (Should):** When adopting, add `provideZonelessChangeDetection()` and remove `zone.js` from build config.

## 3. Security & HTTP

**Where:** Server headers (hosting), `app.config.ts`, `libs/shell` interceptors, production adapters.

**Actions:**

- CSP headers on production deploy; document demo relaxations.
- Central auth/CSRF interceptor for HTTP adapters.
- Ban `bypassSecurityTrustHtml` via ESLint.
- Document in README: **route guards = UX**; API/RLS enforces authZ.

## 4. Design system & Tailwind v4

**Where:** `apps/demo/src/styles.css`, `libs/ui`, `angular.json` / Vite config.

**Actions:**

- `@import "tailwindcss"` and `@tailwindcss/vite` (v4 pattern).
- Feature components consume `libs/ui` primitives (dialog, select, table).
- Enforce min touch targets and `focus-visible` in shared components.

## 5. AI context & CI

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
2. `nx run-many -t lint`
3. `nx run-many -t test` (where configured)
4. `nx build demo`
5. `nx e2e demo-e2e` (or project name)

Optional: OpenSSF Scorecard workflow, Lighthouse CI on Pages deploy.

## 6. SaaS features

| Feature | Port | Typical UI location |
|---------|------|---------------------|
| Org switcher | `OrgPort` | `libs/shell` |
| Members | `OrgPort` | `libs/features-org` |
| Billing | `BillingPort` | `libs/features-org` |
| Auth | `AuthPort` | `libs/features-auth` |

Swap `provideDemoAdapters()` vs production providers only in `app.config.ts`.

## Related

- [roadmap.md](./roadmap.md) — phased adoption
- [rubric/](./rubric/README.md) — full criteria list
