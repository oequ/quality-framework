# Maturity model

Quality Framework uses a **weighted score** (0–1000) and three **maturity levels**. Levels are for communication—always pair a badge with a published self-assessment.

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

## Maturity levels

### L1 — Starter-ready

| | |
|---|---|
| **Score** | > 600 |
| **Audience** | Early adopters, forks, demos |
| **Requirements** | 100% of **Must** criteria in Architecture, Security, and Angular domains; demo runs with mock adapters; `AGENTS.md` or equivalent AI context; honest gaps documented |

**Badge label:** `L1 Starter-ready`

Suitable for publishing an OSS UI starter. Does not imply enterprise security review.

### L2 — Production-ready fork

| | |
|---|---|
| **Score** | > 800 |
| **Audience** | Teams building commercial B2B products |
| **Requirements** | All L1 requirements, plus: Playwright (or equivalent) E2E on critical paths; `@nx/enforce-module-boundaries` (or equivalent) in CI; production adapter available (e.g. Supabase); WCAG 2.2 AA audit on primary flows; CSP and token storage appropriate for deployment |

**Badge label:** `L2 Production-ready`

### L3 — Exemplary

| | |
|---|---|
| **Score** | > 950 |
| **Audience** | Reference architecture in the community |
| **Requirements** | OpenSSF Scorecard ≥ 8.5; ADRs for major decisions; Lighthouse performance/accessibility at top tier on demo; broad **Should** coverage including zoneless or documented migration completion |

**Badge label:** `L3 Exemplary`

## What not to claim

- **L2** with mock-only auth and no boundary lint
- **L3** without public evidence (CI links, self-assessment, Scorecard)
- Any level without specifying **rubric version** (e.g. Quality Framework v1.0)

## Reference: typical strong starter (illustrative)

A ports-and-adapters Angular 21 monorepo with Playwright, mock adapters, and partial security may land around **650–750** if zoneless and full CSP are not yet done—**L1**, not L2. Use [templates/SELF_ASSESSMENT.md.template](../templates/SELF_ASSESSMENT.md.template) for your project.

## Related

- [scoring.md](./scoring.md)
- [rubric/README.md](./rubric/README.md)
- [README — Maturity badges](../README.md#maturity-badges)
