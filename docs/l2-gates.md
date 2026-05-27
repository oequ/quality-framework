# L2 Production-ready gates (checklist)

**Rubric version:** Quality Framework v1.3+

Claiming **L2 Production-ready** requires **all** of the following, **in addition to**:

- Score **> 800** / 1000 (see [scoring.md](./scoring.md))
- **L1** requirements: 100% **Pass** on all **Must** in Architecture, Security, and Angular
- Published [self-assessment](../templates/SELF_ASSESSMENT.md.template) as `docs/QUALITY.md`

**Partial Pass does not satisfy any gate.** Demo-tier Partial (e.g. S5, P1) is allowed for **L1** only when documented.

## Full L2 gate checklist

| # | Domain | Gate | Typical evidence |
|---|--------|------|------------------|
| 1 | Angular | **NG1 + NG2 Pass** — zoneless (`provideZonelessChangeDetection`, no `zone.js` in production) | `app.config.ts`, `angular.json` polyfills |
| 2 | Architecture | **A1 Pass** — abstract-class ports (or documented equivalent); no `@angular/core` in `libs/ports` | Port files, ESLint boundaries |
| 3 | TypeScript | **TS8 Pass** — runtime config path documented for production deploy | `docs/QUALITY.md`, config loader |
| 4 | Security | **S1 Pass** — HTTP CSP for production (not meta-only demo) | Deploy headers, docs |
| 5 | Security | **S2 Pass** — CSP nonces with Angular (`CSP_NONCE` / `ngCspNonce`) | Server + bootstrap config |
| 6 | Security | **S5 Pass** — no demo `localStorage` JWT without cookie/BFF migration in repo | Auth adapter, SECURITY notes |
| 7 | Testing | **T1 Pass** — Playwright on mock adapters: auth + **tenant isolation** | CI workflow, E2E specs |
| 8 | Testing | **T8 Pass** — ≥80% coverage on **ports/adapters** (not vanity global UI %) | Vitest coverage config |
| 9 | Performance & a11y | **P1 Pass** — axe (or equivalent) in **CI** on primary flows | CI job: login, settings, billing, members |
| 10 | Performance & a11y | **P11 Pass** — focus not obscured (sticky headers / `scroll-padding`) | Manual or axe rules |
| 11 | SaaS | **SaaS5 Pass** — onboarding for users without workspace | Routes, empty-state flows |
| 12 | UX | **U11 Pass** — dark mode without FOUC | Theme tokens, `.dark` / `data-theme` |
| 13 | UX | **U4 Pass** — skeletons on primary list/dashboard views | Components + UX review |
| 14 | Documentation | **D3 Pass** — OpenSSF Scorecard **≥ 6.5** published | README badge, workflow |
| 15 | Documentation | **D6 Pass** — `CODEOWNERS` for critical paths | `.github/CODEOWNERS` |
| 16 | Documentation | **D10 Pass** — published `docs/QUALITY.md` with evidence links | File in repo |

## Core L2 vs full L2 (narrative)

Research ([synthesis](./research/00-synthesis-2026-summary.md)) notes that **full L2** is a high bar—appropriate for teams shipping commercial B2B, not for every OSS demo.

| Tier | Intent | Gates |
|------|--------|-------|
| **Core production path** | Minimum to avoid misleading “production” claims | 4–6, 7, 9, 11, 16 (security path, E2E, axe, onboarding, QUALITY.md) |
| **Full L2 (badge)** | Quality Framework official L2 | **All 16** above |

The framework awards the **L2 badge** only for **full L2**. Use **L1 Starter-ready** with an honest demo vs production table if core gates fail.

## Common “score high, not L2” gaps

| Gap | Fix direction |
|-----|----------------|
| Zone.js still in production | NG1/NG2 migration |
| Meta CSP + localStorage auth | S1/S2/S5 production path |
| No axe in CI | Add `@axe-core/playwright` on 4 flows |
| Blank post-signup dashboard | SaaS5 onboarding |
| QUALITY.md missing or v1.0 | Re-score on v1.3+ template |

## Related

- [maturity.md](./maturity.md) — levels and weights
- [migration/v1.0-to-v1.3.md](./migration/v1.0-to-v1.3.md) — rubric upgrades
- [procurement-appendix.md](./procurement-appendix.md) — buyer mapping (informative)

[← Documentation index](./README.md)
