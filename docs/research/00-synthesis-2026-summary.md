# Research synthesis — 2026 B2B Angular SaaS starter expectations

Cross-domain synthesis of nine domain research summaries (May 2026). Baseline rubric: **Quality Framework v1.3**.

Sources: [01](./01-architecture-summary.md)–[09](./09-saas-domain-summary.md) summaries; distilled for v1.4 adopter docs and v2.0 RFC scoping.

## Executive summary

A credible **2026 Angular B2B SaaS starter** must prove four things in the first 15 minutes on GitHub: **(1)** ports-and-adapters architecture with enforced Nx boundaries, **(2)** honest demo vs production security (no fake “bank-grade” claims with `localStorage` JWT), **(3)** a working control plane (org switch, billing port, members, onboarding—not a blank dashboard), and **(4)** machine-readable maintainer context (`AGENTS.md`) plus a published self-assessment.

**L1** is achievable for a strong OSS demo with mock adapters and documented gaps. **L2** is intentionally demanding: v1.3 adds **17 explicit L2 gates** beyond score >800—most starters will score 650–780 yet remain **L1 by gates**. That calibration is **correct** (buyers reject security theater) but requires clear communication ([l2-gates.md](../l2-gates.md)).

**v1.4** should add adopter docs only. **v2.0** should consider category weight review (Performance & a11y at 5% vs EAA procurement emphasis), optional **core L2** gate subset, and procurement mapping—not more criterion IDs.

## Buyer expectation matrix

| Signal | Solo founder | Startup eng lead | Enterprise / procurement | Agency |
|--------|--------------|------------------|--------------------------|--------|
| **Must-have (15 min)** | Quick start, live demo, clear stack | `AGENTS.md`, CI green, boundary lint | SECURITY.md, limitations section, license | Forkable architecture, swap adapters |
| **Must-have (deep dive)** | Mock billing works | Playwright smoke, Vitest on ports | Scorecard, CSP/session path, RLS story | White-label theming, i18n path |
| **Expected** | Ports pattern explained | Zoneless or migration plan | QUALITY.md, ADRs, axe on primary flows | Realistic demo data |
| **Delight** | One-command deploy | Contract tests, Nx cache | VPAT roadmap, SSO story | Preview deploys per PR |
| **Instant reject** | No license / no README | SDK in components | JWT in localStorage claimed as L2 | “Production-ready” with no evidence |

## Category heat map

| Category | L1 table-stakes | L2 commercial bar | L3 differentiator | False claims to avoid |
|----------|-----------------|-------------------|-------------------|------------------------|
| **Architecture** | Ports lib, boundary lint, mock adapters | Abstract-class ports (A1), contract tests | FSD tags, full Result types | “Clean architecture” without lint |
| **Security** | S9 documented, S3 no casual bypass | HTTP CSP, nonces, cookie/BFF (S1/S2/S5) | Trusted Types, edge nonces | Meta CSP + localStorage as “secure” |
| **Angular** | Standalone, signals I/O, control flow | Zoneless (NG1/NG2) | Signal Forms, httpResource | NgModules in new code |
| **TypeScript** | `strict` | Extended flags, branded IDs (TS11) | verbatimModuleSyntax everywhere | Untyped forms |
| **SaaS domain** | Org switcher, BillingPort, members | Onboarding (SaaS5), invite tokens | SCIM, audit log export | UI-only RBAC as security |
| **Testing & CI** | Port tests, Playwright exists | Mock E2E tenant isolation; port coverage ≥80% | Staging E2E prod adapters | E2E-only pyramid |
| **UX** | Loading/empty/error on key flows | Dark mode, skeletons on main views | Optimistic UI, command palette | Page-level spinners only |
| **Performance & a11y** | Partial WCAG + roadmap | axe CI on auth/settings/billing/members | VPAT, manual audit | Lighthouse-only on admin app |
| **Documentation/OSS** | AGENTS.md, CONTRIBUTING, SECURITY | QUALITY.md, Scorecard ≥6.5, CODEOWNERS | Score ≥8.5, PGP disclosure | Vanity badges, empty PR checklists |

## Rubric v1.3 gap analysis

### Calibrated (keep)

- **Tiered security (S1/S5)** and **Partial Pass** rules — matches ASVS reality for demos.
- **T11 = adapter contract tests** (not dependency cooldown from raw testing report).
- **T1 L2 mock E2E / L3 staging** — protects PR velocity.
- **SaaS5 Must** — PLG activation is non-negotiable for “starter” label.
- **D1 + D10** — dual audience (human + AI) is 2026-specific and correct.

### Possibly too lenient (monitor; v2.0 only)

| Item | Note |
|------|------|
| **Performance & a11y weight (5%)** | EAA/VPAT pressure may warrant 8–10% in v2.0 |
| **SaaS12 Must** | Correct for GDPR narrative; many L1 repos will Partial—ensure maturity text is visible |
| **SaaS2 as Should** | Research prefers `/org/:id` for L2; gate not added in v1.3—consider L2 gate in v2.0 |

### Possibly too strict (document, do not downgrade in v1.4)

| Item | Mitigation (v1.4) |
|------|-------------------|
| **17 L2 gates** | [l2-gates.md](../l2-gates.md) with **core** vs **full** narrative |
| **Zoneless L2 gate** | Many codebases migrating—document timeline in QUALITY.md |
| **D3 ≥6.5 L2 gate** | Achievable with Scorecard Action; link quick wins |

### Missing (defer to v2.0 RFC)

- **S1a / S1b** separate IDs for demo vs production CSP
- **FSD Nx tags** (`type:entity`, `type:widget`)
- **Procurement appendix** as normative mapping (v1.4 ships informative draft)
- **Core L2 badge** (subset of gates)—only if community feedback demands it

## Competitive landscape (illustrative)

| Product / pattern | Stack | Advertised strength | Common complaints |
|-------------------|-------|---------------------|-------------------|
| **Makerkit / similar** | React + Supabase | Fast ship, billing | Lock-in, hard to test |
| **Supastarter** | Next + Postgres | Full stack | Monolithic data layer |
| **Spartan / Angular starters** | Angular + Tailwind v4 | Design quality | Varies on boundaries |
| **SaaS Pegasus** | Django | Mature billing | Not frontend-Angular |
| **OSS Angular monorepo starters** | Nx + Angular | Demo speed | localStorage auth, no QUALITY.md |

Angular starters win on **enterprise UI depth** when they ship **ports + honest QUALITY.md**; they lose when they copy Next.js auth patterns without BFF documentation.

## 2026–2027 trajectory

- **Zoneless** becomes default for new Angular workspaces; starters still on zone.js must publish migration dates.
- **Signal Forms + httpResource** move from Could/L3 toward L2 expectations by 2027.
- **Supabase + RLS** remains dominant OSS backend; BFF pattern grows for HttpOnly sessions.
- **AGENTS.md** (Agentic AI Foundation) becomes as expected as `package.json` for OSS libs.
- **EAA enforcement** increases VPAT requests; axe CI is minimum, not sufficient alone.
- **Supply chain**: OSV-Scanner, pinned GHA SHAs, Dependabot cooldown—table-stakes for L2 D3/T7.

## Recommendations

### v1.4 quick wins (this release)

1. Publish [00-synthesis-2026-summary.md](./00-synthesis-2026-summary.md) (this doc) and [l2-gates.md](../l2-gates.md).
2. Add [migration/v1.0-to-v1.3.md](../migration/v1.0-to-v1.3.md) for adopters on old assessments.
3. Ship informative [procurement-appendix.md](../procurement-appendix.md).
4. Normalize [maturity.md](../maturity.md) formatting; link L2 gates from README.
5. Add [rfc/README.md](../rfc/README.md) for v2.0 themes—no rubric ID changes.

### v2.0 RFC candidates (do not implement yet)

1. **Category weight review** — raise Performance & a11y if buyer survey confirms.
2. **S1a/S1b** — split demo vs production CSP criteria.
3. **SaaS2 L2 gate** — route-scoped tenancy.
4. **Core L2 vs full L2** — only if gate count blocks adoption without lowering bar.
5. **FSD optional tags** — L3 architecture path.

## Bibliography

- Domain summaries in this repository ([research index](./README.md))
- [OWASP ASVS 5.0](https://owasp.org/www-project-application-security-verification-standard/)
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [OpenSSF Scorecard](https://scorecard.dev/)
- [AGENTS.md](https://agents.md/)
- [Angular documentation](https://angular.dev/)
- [Nx module boundaries](https://nx.dev/docs/technologies/eslint/eslint-plugin/guides/enforce-module-boundaries)

[← Research index](./README.md)
