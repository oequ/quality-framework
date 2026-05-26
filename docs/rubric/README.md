# Quality rubric

Verifiable criteria for Angular B2B SaaS frontends. Each row has a **stable ID** for self-assessments, issues, and PRs.

## Levels

| Level | Meaning |
|-------|---------|
| **Must** | Required for a credible OSS starter (L1 baseline) |
| **Should** | Expected when shipping a production fork (L2) |
| **Could** | Exemplary; differentiator for L3 |

## Verification types

| Method | Description |
|--------|-------------|
| Automated (CI) | Fails build or gate when violated |
| Automated (ESLint/TS) | Local and CI lint/typecheck |
| Manual (Code review) | Human review until automated rule exists |
| Manual (UX test) | Exploratory or checklist session |

## Domains

| File | Scope | IDs |
|------|--------|-----|
| [01-architecture.md](./01-architecture.md) | Ports, adapters, Nx boundaries | A1–A13 |
| [02-angular.md](./02-angular.md) | Angular 21+ platform | NG1–NG13 |
| [03-typescript.md](./03-typescript.md) | TypeScript, lint, formatting | TS1–TS11 |
| [04-testing-ci.md](./04-testing-ci.md) | Tests, CI, supply chain | T1–T11 |
| [05-security.md](./05-security.md) | CSP, auth, XSS |
| [06-performance-a11y.md](./06-performance-a11y.md) | WCAG 2.2, performance |
| [07-ux-design-system.md](./07-ux-design-system.md) | UI states, design tokens |
| [08-documentation-oss.md](./08-documentation-oss.md) | OSS hygiene, AGENTS.md |
| [09-saas-domain.md](./09-saas-domain.md) | Tenancy, billing, members |

## How to self-score

1. Copy [SELF_ASSESSMENT template](../../templates/SELF_ASSESSMENT.md.template) to your repo.
2. For each **Must** in Architecture, Security, Angular: mark Pass / Fail / Partial + evidence (file, CI job, link).
3. Calculate category scores per [maturity.md](../maturity.md) and [scoring.md](../scoring.md).
4. Publish level only if evidence is linked.

## Ports & adapters column

Many criteria include a **Ports note**—how the rule applies when using hexagonal boundaries (`libs/ports`, `libs/adapters-*`, `libs/features-*`).

## Versioning

This rubric is **Quality Framework v1.1**. Criterion IDs are stable; clarifications and new IDs ship in minor releases (see [evolution.md](../evolution.md) and [CONTRIBUTING.md](../../CONTRIBUTING.md)).
