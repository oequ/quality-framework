# Deep Research — TypeScript & code quality (TS1–TS10)

Cross-cutting category (feeds Architecture, Angular, and CI scoring).

---

## Role

You are a TypeScript platform engineer focused on **large-scale monorepos**, static analysis, and **maintainability standards** for product engineering teams.

## Context

Quality Framework v1.0 TypeScript criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| TS1 | Strict TypeScript (`strict`, `noImplicitAny`, `strictNullChecks`) | Must |
| TS2 | ESLint flat config (v9+) | Must |
| TS3 | Angular ESLint (`@angular-eslint`) | Must |
| TS4 | Prettier (or equivalent formatter) | Must |
| TS5 | Conventional commits / commitlint | Should |
| TS6 | No magic strings for roles/status (named unions/constants) | Should |
| TS7 | Readonly DTOs in domain types | Should |
| TS8 | Environment-based config (no hardcoded secrets/URLs) | Must |
| TS9 | No raw `console.log` in production paths | Should |
| TS10 | Path aliases supporting boundary rules | Must |

## Research questions

### 1. 2026 TypeScript strictness baseline

What strictness level do **respected OSS monorepos** and **enterprise Angular shops** use in 2026?

- Is `strict: true` in root tsconfig table-stakes?
- Additional flags: `noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`, `verbatimModuleSyntax`
- Per-library vs root strict — Nx best practice
- Should TS1 be expanded in rubric v1.1?

### 2. Linting and formatting stack

Evaluate **TS2, TS3, TS4**:

- ESLint flat config — universal adoption?
- typescript-eslint typed linting — performance in monorepos
- Biome vs Prettier — should rubric allow alternatives?
- Angular ESLint rules that catch real bugs vs noise (2026 recommended sets)

### 3. Commit hygiene and semver (TS5)

Do B2B SaaS **buyers** care about conventional commits and changelogs when forking a starter?

- OpenSSF / reproducible builds alignment
- Changesets, release-please, nx release patterns

### 4. Domain modeling in TypeScript (TS6, TS7)

Best practices for **roles, billing status, plan IDs** in SaaS frontends:

- const objects vs string unions vs enums (erasable enums in TS 5.x)
- Readonly domain models — adoption in ports/adapters pattern
- Branded types for IDs (`OrgId`, `UserId`)

### 5. Configuration and secrets (TS8)

2026 expectations for **frontend configuration**:

- Angular `environment.ts` vs runtime config injection vs generated settings files
- Supabase anon key in client — accepted pattern and documentation requirements
- `.env` handling in monorepos, gitignore standards

### 6. Observability vs console (TS9)

Should starters include a **logging abstraction**?

- Structured logging in browser apps
- Sentry/Datadog/OpenTelemetry browser SDK as Should/Could criterion?

### 7. Path aliases and module resolution (TS10)

Nx + TypeScript paths in 2026:

- `@org/*` vs package-based imports
- Compatibility with Vitest, Playwright, IDE performance

### 8. L1 / L2 / L3 mapping

| ID | 2026 L1 | 2026 L2 | 2026 L3 |
|----|---------|---------|---------|

### 9. Automation maturity

What can be **fully CI-enforced** vs manual review in 2026 for each TS criterion?

## Output format

1. Executive summary — TypeScript/code quality bar for SaaS starters (2026)
2. Recommended `tsconfig` baseline (copy-paste example)
3. Recommended ESLint preset composition
4. L1/L2/L3 mapping (TS1–TS10)
5. Proposed rubric v1.1 additions (e.g., `noUncheckedIndexedAccess`, logging port)
6. Bibliography

## Source priorities

- typescriptlang.org docs (current)
- typescript-eslint.io
- Nx TypeScript performance guides
- Google TypeScript style guide updates
- OpenSSF Best Practices badge criteria
- Popular monorepo examples (Nx repo, Angular repo patterns)

## Constraints

- Focus on **application code**, not publishing libraries to npm.
- Note differences for **strict in adapters** vs **strict in features** if relevant.
