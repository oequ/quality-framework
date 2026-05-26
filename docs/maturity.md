# Maturity model

Quality Framework uses a **weighted score** (0–1000) and three **maturity levels**. Levels are for communication—always pair a badge with a published self-assessment.

**Rubric version:** Quality Framework v1.1

## Category weights

| Category | Weight | Max points |
|----------|--------|------------|
| Architecture & boundaries | 20% | 200 |
| Security & privacy | 20% | 200 |
| Angular platform | 15% | 150 |
| SaaS domain | 15% | 150 |
| Testing & CI | 10% | 100 |
| UX & design system | 10% | 100 |
| Performance & accessibility | 5% | 50 |
| Documentation & OSS hygiene | 5% | 50 |
| **Total** | **100%** | **1000** |

## Criterion weights within a category

| Level | Weight | Meaning |
|-------|--------|---------|
| **Must** | 1.0 | Expected for a credible OSS starter |
| **Should** | 0.5 | Expected for a production fork |
| **Could** | 0.2 | Exemplary / differentiator |

**Category score** = (weighted points earned ÷ weighted points possible) × category max.

See [scoring.md](./scoring.md) for a worked example.

## Partial Pass and demo exceptions

| Rule | Detail |
|------|--------|
| **Partial ≠ Pass for gates** | L1/L2 **Must gates** require full **Pass**. Partial scores points only in the 0–1000 total. |
| **Document demo limits** | e.g. JWT in `localStorage`, relaxed CSP meta tag, mock-only billing — label in `docs/QUALITY.md` demo vs production table. |
| **Do not badge above gates** | Score > 600 with failed Architecture/Security/Angular Must = not L1. |

## Maturity levels

### L1 — Starter-ready

| | |
|---|---|
| **Score** | > 600 |
| **Audience** | Early adopters, forks, demos |
| **Requirements** | 100% **Pass** on all **Must** criteria in **Architecture**, **Security**, and **Angular**; demo runs with mock adapters; `AGENTS.md` or equivalent; honest gaps documented |

**Badge label:** `L1 Starter-ready`

Suitable for publishing an OSS UI starter. Does not imply enterprise security review.

### L2 — Production-ready fork

| | |
|---|---|
| **Score** | > 800 |
| **Audience** | Teams building commercial B2B products |
| **Requirements** | All L1 requirements, plus: Playwright E2E on critical paths; `@nx/enforce-module-boundaries` in CI (real constraints); production adapter available; WCAG 2.2 AA on primary flows; CSP and token storage appropriate for deployment |

**Additional L2 gates (v1.1):**

| Domain | Gate |
|--------|------|
| Angular | **NG1 + NG2 Pass** (zoneless) |
| Architecture | **A1 Pass** under v1.1 definition (abstract-class ports or documented equivalent) |
| TypeScript | **TS8** runtime config path documented for production deploy |

**Badge label:** `L2 Production-ready`

### L3 — Exemplary

| | |
|---|---|
| **Score** | > 950 |
| **Audience** | Reference architecture in the community |
| **Requirements** | OpenSSF Scorecard ≥ 8.5; ADRs for major decisions; Lighthouse at top tier on demo; broad **Should** coverage including zoneless, contract-tested adapters (A13/T11), Signal Forms (NG13) where applicable |

**Badge label:** `L3 Exemplary`

## What not to claim

- **L2** with mock-only auth and no boundary lint
- **L2** with zone.js still in production polyfills (NG1/NG2 fail)
- **L3** without public evidence (CI links, self-assessment, Scorecard)
- Any level without specifying **rubric version** (e.g. Quality Framework v1.1)

## Reference: typical strong starter (illustrative)

A ports-and-adapters Angular 21 monorepo with Playwright, mock adapters, and partial security may land around **650–780** if zoneless and full CSP are not yet done—often **L1 by score** but not **L2** until NG1/NG2 and production security path are Pass.

## Related

- [scoring.md](./scoring.md)
- [evolution.md](./evolution.md)
- [rubric/README.md](./rubric/README.md)
- [README — Maturity badges](../README.md#maturity-badges)
