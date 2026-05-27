# Maturity model

Quality Framework uses a **weighted score** (0–1000) and three **maturity levels**. Levels are for communication—always pair a badge with a published self-assessment.

**Rubric version:** Quality Framework v1.4

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
| **Document demo limits** | JWT in `localStorage`, meta CSP, mock-only E2E, Partial WCAG — label in `docs/QUALITY.md` demo vs production table. |
| **Do not badge above gates** | Score > 600 with failed Architecture/Security/Angular Must = not L1. |
| **Security Partial (v1.2)** | **S5** Partial at L1 only with explicit demo/sandbox label + cookie/BFF migration docs. **S1** has no Partial for L2 claims. |
| **Accessibility Partial (v1.2)** | **P1** Partial at L1 only with published remediation roadmap. |

## Maturity levels

### L1 — Starter-ready

| | |
|---|---|
| **Score** | > 600 |
| **Audience** | Early adopters, forks, demos |
| **Requirements** | 100% **Pass** on all **Must** in **Architecture**, **Security**, and **Angular** (demo-tier Partial on S5/P1 allowed only as documented above); mock adapters; `AGENTS.md` or equivalent |

**Badge label:** `L1 Starter-ready`

Suitable for publishing an OSS UI starter. Does not imply enterprise security or EAA compliance.

### L2 — Production-ready fork

| | |
|---|---|
| **Score** | > 800 |
| **Audience** | Teams building commercial B2B products |
| **Requirements** | All L1 requirements, plus production-oriented testing, security, and accessibility paths |

**Additional L2 gates:** see the full checklist in [l2-gates.md](./l2-gates.md) (16 gates across Angular, Architecture, TypeScript, Security, Testing, Performance/a11y, SaaS, UX, Documentation).

**Badge label:** `L2 Production-ready`

### L3 — Exemplary

| | |
|---|---|
| **Score** | > 950 |
| **Audience** | Reference architecture in the community |
| **Requirements** | OpenSSF Scorecard ≥ 8.5; ADRs; broad **Should** coverage; **T1** staging smoke with production adapters; strict **S4** Trusted Types where feasible; independent a11y audit / VPAT |

**Badge label:** `L3 Exemplary`

## What not to claim

- **L2** with mock-only auth and no boundary lint
- **L2** with zone.js in production (NG1/NG2 fail)
- **L2** with meta-tag CSP only or JWT in localStorage without migration path
- **L2** without automated accessibility checks on primary flows
- **L3** without public evidence (CI links, self-assessment, Scorecard)
- **L2** without published `docs/QUALITY.md` or honest README limitations
- Any level without **rubric version** (e.g. Quality Framework v1.4)

## Reference: typical strong starter (illustrative)

A ports-and-adapters Angular 21 monorepo with Playwright, mock adapters, and demo-tier security may land **650–780** — often **L1 by score** but not **L2** until all [L2 gates](./l2-gates.md) Pass.

## Related

- [l2-gates.md](./l2-gates.md)
- [scoring.md](./scoring.md)
- [evolution.md](./evolution.md)
- [migration/v1.0-to-v1.3.md](./migration/v1.0-to-v1.3.md)
- [rubric/README.md](./rubric/README.md)
- [README — Maturity badges](../README.md#maturity-badges)
