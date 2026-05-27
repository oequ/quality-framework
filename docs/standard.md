# Quality Framework — Standard overview

**Version 1.3** · Angular B2B SaaS frontends (2025–2026)

## Executive summary

Between 2025 and 2026, how open-source starters and commercial B2B SaaS frontends demonstrate quality changed materially. A plain Markdown checklist (binary Must/Should ticks) is **necessary but not sufficient**: with AI-assisted development and continuous CI, static lists invite **checklist washing**—boxes checked without matching the codebase.

A credible standard in 2026 combines:

1. **Machine-readable project context** ([AGENTS.md](https://agents.md/) for AI assistants)
2. **Automated quality gates** (lint, boundaries, tests, supply-chain checks)
3. **A weighted maturity model** for architecture and security that static analysis alone cannot score

For Angular SaaS apps on **Angular 21+**, **Nx**, **ports & adapters**, and a shared design system, quality is defined by **strict module boundaries** as much as by features. Hexagonal-style ports keep domain contracts free of framework and vendor SDKs.

## What replaced “just a checklist”?

| Format | Role in 2026 |
|--------|----------------|
| Flat checklist | Onboarding aid; easy to game |
| **Rubric** (this framework) | Weighted criteria with verification methods |
| **Maturity levels** (L1–L3) | Communicate starter vs production-ready fork |
| **CI gates** | Enforce rules algorithms can verify |
| **AGENTS.md** | Steer AI codegen away from boundary violations |
| **OpenSSF Scorecard** | External signal for OSS trust |

Quality Framework is a **rubric + maturity model**, not a single PDF. Consumers copy templates into their app repos and wire automation locally.

## Recommended artifacts in *your* application repo

| Artifact | Location | Purpose |
|----------|----------|---------|
| `AGENTS.md` | Repository root | Build commands, Nx tags, import rules for AI tools |
| `docs/QUALITY.md` | From [SELF_ASSESSMENT template](../templates/SELF_ASSESSMENT.md.template) | Published self-assessment |
| Rubric reference | Link to this repo | Single source of criterion definitions |
| CI workflows | `.github/workflows/` | lint, test, build, e2e, optional Scorecard |
| ADRs | `docs/adr/` | Why ports, signals, stack choices |

This repository (`quality-framework`) holds the **canonical rubric**. Your app repo holds **evidence** and automation.

## Non-negotiables (directional)

These themes appear repeatedly across rubric domains. Exact IDs and levels are in [rubric/](./rubric/README.md).

1. **Framework-free port contracts** — `libs/ports` has no `@angular/*` imports; use **abstract classes** as DI tokens (v1.1). RxJS in port streams is OK if documented.
2. **Nx boundary enforcement** — Features do not import adapters; only ports (and UI primitives).
3. **Injection tokens for ports** — Swap mock vs production adapters in `app.config` only.
4. **Standalone-first Angular** — No new NgModules; signal `input()` / `output()`; built-in control flow.
5. **Async data via Resource API** — Prefer `resource()` / `httpResource()` over manual subscribe chains in UI.
6. **Security baseline (tiered)** — Demo may use meta CSP + labeled `localStorage`; **L2** requires HTTP CSP (S1), nonces (S2), and cookie/BFF session path (S5).
7. **WCAG 2.2 AA targets** — Focus visible, focus not obscured (P11), axe CI on primary flows for L2 (P1); VPAT for enterprise procurement.
8. **AGENTS.md** — Deterministic instructions for humans and AI in monorepos.
9. **SaaS domain boundaries** — Billing, members, tenancy via ports—not vendor SDKs in components.
10. **Demo realism** — Mock adapters for local run; production adapter swappable without editing features.

### Aspirational targets (label honestly)

Some criteria describe **2026 best practice** that teams adopt gradually:

- **Zoneless** (`provideZonelessChangeDetection`, no `zone.js`) — **Must for L2** (v1.1); many L1 starters still migrate.
- **Full CSP with nonces** — **L2 gates** S1+S2; demos document meta CSP explicitly.
- **axe in CI on primary flows** — **L2 gate** P1; marketing pages may use Lighthouse (T9).
- **Mock-only E2E on PR** — **L2** T1; staging smoke with prod adapters is **L3**.
- **Route-based tenant IDs** — alternative to active-org context + settings routes; pick one model and document it.

Mark these **Should** or document gaps in your self-assessment. Do not claim L2 while running a demo-only auth mock.

## Top gaps in typical Angular SaaS starters

1. **Leaky components** — Supabase/Firebase/Stripe SDK imported in feature components; ports become theater.
2. **No boundary lint** — Adapters reachable from UI; refactors break isolation silently.
3. **Security theater** — UI role guards treated as authorization; tokens in `localStorage` in demos.
4. **No supply-chain signal** — Missing Dependabot/Renovate, Scorecard, or audit in CI.
5. **Checklist-only governance** — CONTRIBUTING without automated enforcement.

A strong starter proves **adapter swap at DI** and documents **backend enforcement** for authZ.

## Checklist washing

Avoid:

- PR templates with unchecked boxes that CI does not verify
- README badges for L2/L3 without a published self-assessment
- Copy-pasting the rubric without `enforce-module-boundaries`

Prefer:

- Failing CI when a forbidden import appears
- Public `docs/QUALITY.md` with criterion IDs and evidence links
- Versioned rubric (`quality-framework` v1.x) pinned in your assessment

## Next steps

- [Maturity levels](./maturity.md)
- [Framework evolution](./evolution.md)
- [Research summaries](./research/README.md)
- [Rubric](./rubric/README.md)
- [Implementation mapping](./implementation.md)
- [90-day roadmap](./roadmap.md)
