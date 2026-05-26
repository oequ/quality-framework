# Deep Research — Architecture & boundaries (A1–A12)

Weight: 20% of total score. L1 gate: all Must criteria must pass.

---

## Role

You are a software architect specializing in **hexagonal architecture (ports & adapters)**, **Nx monorepos**, and **frontend platform engineering** for B2B SaaS products.

## Context

We evaluate OSS Angular SaaS starters using **Quality Framework v1.0**. Architecture category criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| A1 | Framework-free ports (`libs/ports` has no `@angular/*` or `rxjs`) | Must |
| A2 | Nx `@nx/enforce-module-boundaries` in CI | Must |
| A3 | Ports consumed via `InjectionToken` only | Must |
| A4 | Isolated mock adapters library | Must |
| A5 | Shell does not depend on feature internals | Must |
| A6 | Acyclic dependencies (inward toward ports) | Must |
| A7 | Public API barrels (`index.ts`) | Should |
| A8 | Typed errors (`Result<T,E>` / `PortError`) | Should |
| A9 | DTO mapping in adapters only | Should |
| A10 | Domain vs UI state separation | Could |
| A11 | Feature-sliced libraries (`features-auth`, `features-org`) | Must |
| A12 | Design system boundary (`libs/ui`) | Must |

Our starter uses: Nx 22, Angular 21, `libs/ports`, `libs/adapters-mock`, `libs/data-access-supabase`, `libs/shell`, `libs/features-*`, Spartan UI sublibs.

**Known tension:** ports currently import `InjectionToken` from `@angular/core` and `Observable` from `rxjs` — fails strict A1 but is common in Angular hexagonal setups.

## Research questions

### 1. 2026 industry baseline

What do **recognized authorities** (Nx docs, Angular architects, Thoughtworks Technology Radar, Martin Fowler / hexagonal architecture community, Enterprise Angular patterns) consider **minimum credible architecture** for a B2B SaaS frontend monorepo in 2026?

- Is ports-and-adapters still differentiated or table-stakes?
- Is feature-sliced design (FSD) vs feature libraries (Nx tags) the expected pattern?
- What boundary enforcement tools are standard (Nx tags, ESLint, dependency-cruiser, ArchUnit equivalent)?

### 2. Framework-free ports debate

Research the **A1 criterion** specifically:

- Can Angular DI tokens live outside `libs/ports` while keeping interfaces framework-free?
- Patterns: split `ports-core` (pure TS) + `ports-angular` (tokens), vs tokens in adapters, vs community acceptance of Angular in ports layer
- What do Supabase/Firebase/Stripe starter templates do?
- **Recommendation for 2026:** keep strict A1, relax to Partial, or redefine A1?

### 3. Mock vs production adapter swap

Evaluate **A3, A4, A6** against 2024–2026 best practice:

- Single `app.config.ts` provider function pattern
- Contract testing between ports and adapters
- How demo/GitHub Pages deployments avoid leaking production SDKs

### 4. Error model and DTO mapping (A8, A9)

What error-handling patterns are standard in 2026 TypeScript frontends?

- `Result<T,E>` vs exceptions vs typed HTTP errors
- Where mapping belongs (adapter vs API client vs BFF)
- References: Railway-oriented programming in TS, Effect-TS adoption in app code (not just libs)

### 5. Buyer expectations

When a **B2B SaaS buyer** clones a starter, what architecture signals build trust vs raise red flags in the first code review?

- README architecture diagram
- Dependency graph screenshot
- "No Supabase in features" rule
- ADRs for major decisions

### 6. L1 / L2 / L3 mapping (2026)

For each criterion A1–A12, classify:

| ID | 2026 L1 (starter) | 2026 L2 (production fork) | 2026 L3 (exemplary) | Evidence / source |
|----|-------------------|---------------------------|---------------------|-------------------|

### 7. Anti-patterns

List **architecture anti-patterns** commonly found in SaaS starters that buyers regret after 6 months. Cite post-mortems, GitHub issues, or engineering blog posts.

## Output format

1. Executive summary (2026 architecture bar for SaaS starters)
2. Answers to each research question with citations
3. A1 framework-free ports — recommended rubric wording for v1.1
4. L1/L2/L3 mapping table (A1–A12)
5. Top 5 actionable improvements for a ports-and-adapters Angular monorepo
6. Anti-patterns list
7. Bibliography (URLs, publication dates)

## Source priorities

- Nx enforced module boundaries documentation (current)
- Angular.dev architecture guides
- Hexagonal / clean architecture primary sources and 2024–2026 adaptations for SPAs
- Thoughtworks Technology Radar (latest)
- Real OSS repos: ngx-admin alternatives, Supabase starters, AnalogJS, enterprise Angular examples
- Conference talks / articles from NgConf, Angular Connect (2024–2026)

## Constraints

- Focus on **browser SPA + optional SSR**, not mobile-native.
- Distinguish **open-source starter** expectations from **internal enterprise platform** standards.
- Mark uncertain claims; prefer primary sources over Medium reposts.
