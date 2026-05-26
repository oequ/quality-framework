# Research reports

Deep-research outputs used to evolve Quality Framework **v1.1** (May 2026). Raw reports are long-form; start with the **summaries** for rubric impact.

## Reports

| Report | Raw file | Summary | Rubric impact |
|--------|----------|---------|---------------|
| Architecture & boundaries | [Architecture & Boundaries….txt](./Architecture%20%26%20Boundaries%20for%20Enterprise%20Frontend%20SaaS%20Platforms.txt) | [01-architecture-summary.md](./01-architecture-summary.md) | A1, A13, anti-patterns |
| Angular platform 2026 | [Angular Platform….txt](./Angular%20Platform%20Architecture%20and%20Migration%20Patterns%20in%202026.txt) | [02-angular-summary.md](./02-angular-summary.md) | NG1–NG2 L2 gate, NG6, NG13 |
| TypeScript & code quality | [TypeScript & Code Quality….txt](./TypeScript%20%26%20Code%20Quality%20in%20Enterprise%20Monorepos.txt) | [03-typescript-summary.md](./03-typescript-summary.md) | TS1, TS8–TS11 |

## How to add research

1. Store raw export as `docs/research/<topic>.txt` or `.md`.
2. Add a **summary** (`NN-domain-summary.md`) with: executive summary, L1/L2/L3 table, proposed rubric changes, bibliography URLs.
3. Link from [evolution.md](../evolution.md) and [CHANGELOG.md](../../CHANGELOG.md).
4. Open issues for each proposed criterion change before the next minor release.

## Prompt templates

Reusable Gemini Deep Research prompts: [prompts/](./prompts/README.md) (one file per rubric domain + synthesis).

[← Documentation index](../README.md)
