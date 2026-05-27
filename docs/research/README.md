# Research reports

Deep-research outputs used to evolve Quality Framework. Raw `.txt` exports are gitignored; start with **summaries** for rubric impact.

## Synthesis (start here for big picture)

| Report | Summary |
|--------|---------|
| Cross-domain 2026 expectations | [00-synthesis-2026-summary.md](./00-synthesis-2026-summary.md) |

## Domain reports

| Report | Raw file | Summary | Rubric impact |
|--------|----------|---------|---------------|
| Architecture & boundaries | [Architecture & Boundaries….txt](./Architecture%20%26%20Boundaries%20for%20Enterprise%20Frontend%20SaaS%20Platforms.txt) | [01-architecture-summary.md](./01-architecture-summary.md) | A1, A13 |
| Angular platform 2026 | [Angular Platform….txt](./Angular%20Platform%20Architecture%20and%20Migration%20Patterns%20in%202026.txt) | [02-angular-summary.md](./02-angular-summary.md) | NG1–NG2 L2 gate, NG6, NG13 |
| TypeScript & code quality | [TypeScript & Code Quality….txt](./TypeScript%20%26%20Code%20Quality%20in%20Enterprise%20Monorepos.txt) | [03-typescript-summary.md](./03-typescript-summary.md) | TS1, TS8–TS11 |
| Testing & CI | [High-Performance CI….txt](./High-Performance%20Continuous%20Integration%20and%20Testing%20Architecture%20for%20B2B%20SaaS%20Angular%20Monorepos.txt) | [04-testing-ci-summary.md](./04-testing-ci-summary.md) | T1 tiers, T12–T14 |
| Security & privacy | [Modern Frontend Security.txt](./Technical%20Assessment%20and%20Architectural%20Blueprint%20Modern%20Frontend%20Security.txt) | [05-security-summary.md](./05-security-summary.md) | S1/S5 tiers, S11 |
| Performance & a11y | [WCAG 2.2 & CWV….txt](./Implementing%20WCAG%202.2%20AA%20and%20Core%20Web%20Vitals%20in%20Angular%2021%20SaaS%20Admin%20Applications.txt) | [06-performance-a11y-summary.md](./06-performance-a11y-summary.md) | P1 axe CI, P11 |
| SaaS domain | [Multi-Tenancy, Billing….txt](./A%20Technical%20Blueprint%20for%20Multi-Tenancy%2C%20Billing%20Abstractions%2C%20and%20Fine-Grained%20Authorization%20in%202026.txt) | [09-saas-domain-summary.md](./09-saas-domain-summary.md) | SaaS5 Must, SaaS8–12 |
| UX & design system | [Modern B2B Admin UX….txt](./Modern%20B2B%20Admin%20UX%20and%20Design%20System%20Architecture.txt) | [07-ux-design-system-summary.md](./07-ux-design-system-summary.md) | U11, U12–U13 |
| Documentation & OSS | [AI-Assisted Architecture….txt](./A%20Comprehensive%20Framework%20for%20AI-Assisted%20Architecture%2C%20Security%2C%20and%20Governance%20Compliance.txt) | [08-documentation-oss-summary.md](./08-documentation-oss-summary.md) | D9–D10, D3 L2 gate |

## How to add research

1. Store raw export as `docs/research/<topic>.txt` (gitignored).
2. Add a **summary** (`NN-domain-summary.md`) with: executive summary, L1/L2/L3 table, proposed rubric changes, bibliography URLs.
3. Link from [evolution.md](../evolution.md) and [CHANGELOG.md](../../CHANGELOG.md).
4. Open issues for each proposed criterion change before the next minor release.

## Prompt templates

Reusable Gemini Deep Research prompts: [prompts/](./prompts/README.md) (one file per rubric domain + synthesis).

[← Documentation index](../README.md)
