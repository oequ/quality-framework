# Research summary — TypeScript & code quality (May 2026)

Source: [TypeScript & Code Quality in Enterprise Monorepos.txt](./TypeScript%20%26%20Code%20Quality%20in%20Enterprise%20Monorepos.txt)

## Executive summary

**strict: true** is baseline only. L2+ expects **noUncheckedIndexedAccess**, **exactOptionalPropertyTypes**, **verbatimModuleSyntax**, ESLint **projectService**, runtime configuration, and **branded IDs** for tenant-scoped primitives.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.1) |
|-------|----------------|----------------------|
| TS1 strict | + advanced flags for L2 | Expand TS1 description |
| TS enums | Anti-pattern; use unions + `as const` | TS6 guidance |
| Branded types | `OrgId`, `UserId` via Zod `.brand()` | **Add TS11** (Should) |
| TS8 config | `environment.ts` swap = anti-pattern for L2 | L1 vs L2 split in TS8 |
| TS9 logging | Logger port → Sentry/OTel, not console | Clarify TS9 |
| TS5 | commitlint + nx release / release-please | Stay Should |
| Biome | Alternative to Prettier for .ts | TS4 note |
| Vitest | `@org/source` customConditions | TS10 / implementation |

## L1 / L2 / L3 (research view)

| ID | L1 | L2 | L3 |
|----|----|----|-----|
| TS1 | strict + strictNullChecks | + noUncheckedIndexedAccess, exactOptionalPropertyTypes | + verbatimModuleSyntax everywhere |
| TS8 | Generated/build-time config OK if documented | Runtime `config.json` + app initializer | Immutable Docker promote |
| TS9 | ESLint no-console | Structured logging adapter | Full observability port + traces |
| TS11 | — | Branded IDs at boundaries | Zod + nominal types in domain |

## Top actions for adopters

1. Enable extended strict flags in root `tsconfig` (L2).
2. ESLint flat config with `projectService: true`.
3. Ban TypeScript `enum` for roles/status.
4. Introduce branded `OrgId` / `UserId` at adapter boundary.
5. Plan runtime config for production deploys.

[← Research index](./README.md)
