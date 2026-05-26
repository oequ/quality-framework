# Framework evolution (v1.0 → v1.1+)

How Quality Framework stays current, how we use research, and how maintainers should change the rubric without checklist washing.

## Purpose

Quality Framework is a **living standard**, not a frozen PDF. It evolves when:

1. **Platform reality shifts** (Angular zoneless default, Signal Forms, ESLint projectService).
2. **Buyer expectations shift** (B2B SaaS procurement, EU accessibility law, supply-chain audits).
3. **Evidence accumulates** (deep research, production post-mortems, reference implementations).

Version **1.1** (May 2026) incorporates findings from three Gemini Deep Research reports in [research/](./research/README.md).

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
| Clarify criterion, add criterion, L2 gate detail | **Minor 1.1** | Redefine A1 for abstract-class ports |
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

### Remaining domains (planned research)

| Domain | Status (May 2026) |
|--------|-------------------|
| Architecture | Done — [summary](./research/01-architecture-summary.md) |
| Angular | Done — [summary](./research/02-angular-summary.md) |
| TypeScript | Done — [summary](./research/03-typescript-summary.md) |
| Security | Planned |
| Testing & CI | Planned |
| SaaS domain | Planned |
| UX & design system | Planned |
| Performance & a11y | Planned |
| Documentation & OSS | Planned |

After Security + SaaS research, run a **synthesis** pass and consider **v1.2**.

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

## How adopters should upgrade

1. Pin rubric version in `docs/QUALITY.md`: `Quality Framework v1.1`.
2. Re-score affected categories (Architecture, Angular, TypeScript, Testing).
3. Update README badge only if **gates** still pass after redefinition (e.g. A1 may move from Fail → Pass if you adopt abstract-class ports).
4. Do not inflate scores — document gaps honestly.

## Long-term directions (v2.0 candidates)

Not committed; track via issues:

| Theme | Rationale |
|-------|-----------|
| **FSD layer tags** | Research favors Feature-Sliced Design + Nx; optional `type:entity`, `type:widget` constraints |
| **Security tier matrix** | Separate “demo CSP” vs “production CSP” criteria (S1a/S1b) |
| **Automated a11y gate** | axe in CI as Should for L2 |
| **Buyer persona appendix** | Procurement checklist derived from synthesis research |
| **Scoring weight review** | Security 20% may rise if buyer surveys confirm |

## Contributing rubric changes

See [CONTRIBUTING.md](../CONTRIBUTING.md). Prefer:

- Evidence link (doc, research summary, CVE, Angular RFC)
- Impact on L1 / L2 / L3
- Migration note for existing self-assessments

[← Documentation index](./README.md)
