# TypeScript & code quality

Static analysis, formatting, and conventions for maintainable monorepos.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **TS1** | **Strict TypeScript.** Root `strict: true` with `noImplicitAny` and `strictNullChecks`. **L2 expectation:** also `noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`, and `verbatimModuleSyntax` (or documented exceptions in adapter libs only). | Must | `tsc` | Strong contracts between ports and UI. |
| **TS2** | **ESLint flat config (v9+).** Modern ESLint config format. Prefer `parserOptions.projectService: true` for type-aware rules in monorepos. | Must | CI lint | Supports latest plugins without OOM on wide globs. |
| **TS3** | **Angular ESLint.** `@angular-eslint` recommended rules enabled; include signal rules (`no-uncalled-signals`, `prefer-inject`) where applicable. | Must | CI lint | Templates and components checked. |
| **TS4** | **Prettier or equivalent.** Consistent formatting enforced (Prettier, or Biome for TS with Prettier for Angular HTML if needed). | Must | CI / git hooks | Run format check separate from ESLint for performance. |
| **TS5** | **Conventional commits.** Commitlint or documented convention; optional `nx release` / release-please for changelog automation. | Should | Git hooks / policy | Helps semver for starters. |
| **TS6** | **No magic strings for roles/status.** String literal unions or `as const` objects—not TypeScript `enum` (runtime emit). | Should | Code review | e.g. `owner` \| `admin` \| `member`. |
| **TS7** | **Readonly DTOs.** Domain/port types use `readonly` where appropriate. | Should | ESLint / TypeScript | Prevents accidental mutation in UI. |
| **TS8** | **Configuration externalized.** No hardcoded API URLs or keys in source. **L1:** build-time or generated settings OK if documented. **L2:** runtime config injection (e.g. `config.json` + app initializer) for immutable deploy artifacts. | Must | Architecture review | Demo vs prod adapter wiring. |
| **TS9** | **Structured logging.** No raw `console.log` in feature code; route errors and significant events through a logging port or adapter (e.g. Sentry) in production paths. | Should | ESLint / review | Demos may use console; document exception. |
| **TS10** | **Path aliases.** TS paths (`@org/ports`, etc.) for imports; supports boundary rules. | Must | ESLint | Required for Nx tag enforcement. |
| **TS11** | **Branded domain IDs.** Cross-tenant identifiers (`OrgId`, `UserId`, etc.) use nominal/branded types at validation boundaries (e.g. Zod `.brand()`). | Should | TypeScript / review | Prevents argument-swapping bugs between string IDs. |

[← Rubric index](./README.md)
