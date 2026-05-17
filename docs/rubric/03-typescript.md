# TypeScript & code quality

Static analysis, formatting, and conventions for maintainable monorepos.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **TS1** | **Strict TypeScript.** `strict`, `noImplicitAny`, `strictNullChecks` enabled. | Must | `tsc` | Strong contracts between ports and UI. |
| **TS2** | **ESLint flat config (v9+).** Modern ESLint config format. | Must | CI lint | Supports latest plugins. |
| **TS3** | **Angular ESLint.** `@angular-eslint` recommended rules enabled. | Must | CI lint | Templates and components checked. |
| **TS4** | **Prettier (or equivalent).** Consistent formatting enforced. | Must | CI / git hooks | Reduces style debate in OSS. |
| **TS5** | **Conventional commits.** Commitlint or documented convention for changelog generation. | Should | Git hooks / policy | Helps semver for starters. |
| **TS6** | **No magic strings for roles/status.** Named constants or unions for roles, billing status, etc. | Should | Code review | e.g. `owner` \| `admin` \| `member`. |
| **TS7** | **Readonly DTOs.** Domain/port types use `readonly` where appropriate. | Should | ESLint / TypeScript | Prevents accidental mutation in UI. |
| **TS8** | **Environment-based config.** API URLs and keys from environment—not hardcoded in adapters. | Must | Architecture review | Demo vs prod adapter wiring. |
| **TS9** | **No raw `console.log` in app code.** Errors via logging port or structured logger (production). | Should | ESLint | Demos may relax; document exception. |
| **TS10** | **Path aliases.** TS paths (`@org/ports`, etc.) for imports; supports boundary rules. | Must | ESLint | Required for Nx tag enforcement. |

[← Rubric index](./README.md)
