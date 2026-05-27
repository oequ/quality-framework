# Framework evolution (v1.0 → v1.4+)

How Quality Framework stays current, how we use research, and how maintainers should change the rubric without checklist washing.

## Purpose

Quality Framework is a **living standard**, not a frozen PDF. It evolves when:

1. **Platform reality shifts** (Angular zoneless default, Signal Forms, ESLint projectService).
2. **Buyer expectations shift** (B2B SaaS procurement, EU accessibility law, supply-chain audits).
3. **Evidence accumulates** (deep research, production post-mortems, reference implementations).

Versions **1.1–1.3** (May 2026) incorporated deep research across all nine rubric domains. **v1.4** closes the research loop with [synthesis](./research/00-synthesis-2026-summary.md) and adopter docs ([l2-gates.md](./l2-gates.md), [migration](./migration/v1.0-to-v1.3.md), [procurement appendix](./procurement-appendix.md)).

## Governance model

```text
Sources (OWASP, angular.dev, Nx, field research)
        ↓
Deep research / community feedback (GitHub issues)
        ↓
Rubric draft (stable IDs, Must/Should/Could)
        ↓
Reference implementation check (e.g. angular-saas-starter-ui)
        ↓
Minor release (1.x) — clarify criteria, add IDs, L2 gates
Major release (2.0) — reweight categories or break scoring
```

| Change type | Version bump | Example |
|-------------|--------------|---------|
| Typo, link fix | Patch 1.0.x | Fix broken URL |
| Clarify criterion, add criterion, L2 gate detail | **Minor 1.x** | v1.1: A1 ports; v1.2: S1/S5 tiers, P1 axe CI |
| Rename ID, remove criterion, change category weights | **Major 2.0** | Merge domains, change 1000-point weights |

**Criterion IDs are stable.** Meaning may be clarified in minor releases (with CHANGELOG). Removing or renaming an ID requires major version and migration notes.

## Research program

### Cadence

| Activity | Frequency | Output |
|----------|-----------|--------|
| Domain deep research | 1–2 domains / quarter | Report in `docs/research/` |
| Rubric sync | After each research batch | Minor release if warranted |
| Reference app re-score | Each minor release | Updated self-assessment in reference repos |
| Synthesis | After 3+ domain reports | Update [evolution.md](./evolution.md) priorities |

### Research → rubric pipeline

1. Run structured prompt from [docs/research/prompts/](./research/prompts/README.md).
2. Store raw report in `docs/research/`.
3. Extract: **table-stakes 2026**, **L1/L2/L3 mapping**, **proposed v1.x changes**, **anti-patterns**.
4. Open GitHub issue per proposed change (label `rubric-feedback`).
5. Merge doc changes + CHANGELOG in minor release.

### Research status (May 2026)

| Domain | Status |
|--------|--------|
| Architecture | [01 summary](./research/01-architecture-summary.md) |
| Angular | [02 summary](./research/02-angular-summary.md) |
| TypeScript | [03 summary](./research/03-typescript-summary.md) |
| Testing & CI | [04 summary](./research/04-testing-ci-summary.md) |
| Security | [05 summary](./research/05-security-summary.md) |
| Performance & a11y | [06 summary](./research/06-performance-a11y-summary.md) |
| UX & design system | [07 summary](./research/07-ux-design-system-summary.md) |
| Documentation & OSS | [08 summary](./research/08-documentation-oss-summary.md) |
| SaaS domain | [09 summary](./research/09-saas-domain-summary.md) |
| **Synthesis** | [00 summary](./research/00-synthesis-2026-summary.md) |

**Research program:** maintenance mode. New domain research only via approved [RFC](./rfc/README.md) or major community demand. Routine changes: GitHub issues (`rubric-feedback`), patch/minor doc fixes.

## v1.4 changes (summary)

- **[00-synthesis-2026-summary.md](./research/00-synthesis-2026-summary.md)** — buyer matrix, heat map, v1.3 gap analysis, v2.0 candidates.
- **[l2-gates.md](./l2-gates.md)** — 16-gate checklist; core vs full L2 narrative.
- **[migration/v1.0-to-v1.3.md](./migration/v1.0-to-v1.3.md)** — ID and gate changelog for adopters.
- **[procurement-appendix.md](./procurement-appendix.md)** — informative ASVS/VPAT/Scorecard mapping.
- **[rfc/README.md](./rfc/README.md)** — v2.0 RFC index.
- **No new rubric criterion IDs.**

## v1.1 changes (summary)

### Architecture

- **A1 redefined:** Port contracts are framework-free; use **abstract classes** as DI tokens instead of `InjectionToken` from `@angular/core`. RxJS `Observable` in ports is allowed for streams (document usage).
- **A13 added (Should):** Adapter contract tests — same suite against mock and production adapters.

### Angular

- **L2 gate:** NG1 + NG2 (zoneless) are **Must** for claiming L2 (remain Should for L1 score).
- **NG6:** Explicitly includes `linkedSignal()` for dependent mutable state.
- **NG13 added (Could):** Signal Forms (`@angular/forms/signals`) for new data-entry modules.

### TypeScript

- **TS1 expanded:** Documents `noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`, `verbatimModuleSyntax` as L2 expectations.
- **TS11 added (Should):** Branded/nominal types for cross-tenant IDs (`OrgId`, `UserId`) at validation boundaries.
- **TS8 clarified:** L1 allows build-time/generated config; **L2 requires runtime config injection** (immutable deploy artifacts).
- **TS9 clarified:** Structured logging via port/abstraction, not only “no console.log”.

### Testing

- **T11 added (Should):** Adapter contract tests (pairs with A13).

### Maturity & honesty

- **Partial Pass** rules documented in [maturity.md](./maturity.md) — demo exceptions (localStorage JWT, relaxed CSP) must be labeled; Partial does not count as Pass for L1 Must gates.
- **Score vs gates:** Total score > 600 does not replace 100% Must in Architecture, Security, Angular for L1 badge.

## v1.3 changes (summary)

### SaaS domain

- **SaaS5 → Must:** Guided onboarding for users without a workspace.
- **SaaS2 tiers:** Active-org OK for L1; `/org/:id` + guards for L2.
- **SaaS8–SaaS12 added:** Audit log, API keys, metering, SSO, export/deletion (SaaS12 Must with L1 Partial path).

### UX & design system

- **U11 added (Should):** Dark mode — **L2 gate**.
- **U12–U13 added (Could):** i18n (Transloco-style), optimistic UI.
- **U4/U6/U9 clarified:** Skeletons, inline retry, OKLCH tokens.

### Documentation & OSS

- **D9 added (Should):** README credibility (demo, limitations, stack matrix).
- **D10 added (Should):** Published `docs/QUALITY.md` — **L2 gate**.
- **D3 elevated:** Scorecard Should; L2 requires score ≥ 6.5.

## v1.2 changes (summary)

### Security

- **S1 / S5 tier notes:** Demo meta CSP and labeled `localStorage` vs L2 HTTP CSP and cookie/BFF path.
- **L2 gates:** S1, S2, S5 Pass required for L2 badge.
- **S11 added (Should):** SAST ESLint plugins in CI.

### Testing & CI

- **T1 tiers:** L2 mock-adapter E2E on PR; L3 staging with production adapters.
- **T12–T14 added:** Cooldown (Should), PR previews (Could), visual regression (Could).
- **T8 / T9 clarified:** Coverage on ports/adapters; Lighthouse on marketing, axe on app (P1).

### Performance & accessibility

- **P11 added (Must):** Focus Not Obscured (WCAG 2.4.11).
- **P1 L2 gate:** `@axe-core/playwright` (or equivalent) on primary flows in CI.
- **P1 L1 Partial:** Allowed with published remediation roadmap.

## How adopters should upgrade

1. Pin rubric version in `docs/QUALITY.md`: `Quality Framework v1.4`.
2. Use [l2-gates.md](./l2-gates.md) before claiming **L2**.
3. If migrating from v1.0 assessments, read [migration/v1.0-to-v1.3.md](./migration/v1.0-to-v1.3.md).
4. Do not claim **L2** until all gates Pass — score alone is insufficient.

## Long-term directions (v2.0)

Track in [rfc/README.md](./rfc/README.md). Themes include category weight review, S1a/S1b split, SaaS2 L2 gate, core L2 badge, FSD tags, normative procurement kit.

## Contributing rubric changes

See [CONTRIBUTING.md](../CONTRIBUTING.md). Prefer:

- Evidence link (doc, research summary, CVE, Angular RFC)
- Impact on L1 / L2 / L3
- Migration note for existing self-assessments

[← Documentation index](./README.md)
