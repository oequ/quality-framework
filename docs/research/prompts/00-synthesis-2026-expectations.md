# Synthesis prompt — 2026 B2B SaaS starter expectations

Run this **after** completing all nine domain-specific research summaries (01–09).

---

## Role

You are a principal engineer and product strategist specializing in **Angular B2B SaaS control-plane applications** (multi-tenant admin UIs: auth, org settings, billing, members, API keys, metrics).

## Context

**Quality Framework v1.3** is a weighted rubric (0–1000) for evaluating OSS Angular SaaS starters. Maturity levels:

- **L1 Starter-ready** (>600): credible OSS fork; mock adapters OK; honest gaps in `docs/QUALITY.md`
- **L2 Production-ready** (>800): score plus **all L2 gates** (see [maturity.md](../../maturity.md))
- **L3 Exemplary** (>950): reference architecture, Scorecard ≥8.5, staging E2E, broad Should coverage

**L2 gates (v1.3):** NG1+NG2, A1, TS8, S1+S2+S5, T1+T8, P1+P11, SaaS5, U4+U11, D3+D6+D10.

## Input attachments

Paste or attach these summaries when running Deep Research:

| # | Summary |
|---|---------|
| 01 | [01-architecture-summary.md](../01-architecture-summary.md) |
| 02 | [02-angular-summary.md](../02-angular-summary.md) |
| 03 | [03-typescript-summary.md](../03-typescript-summary.md) |
| 04 | [04-testing-ci-summary.md](../04-testing-ci-summary.md) |
| 05 | [05-security-summary.md](../05-security-summary.md) |
| 06 | [06-performance-a11y-summary.md](../06-performance-a11y-summary.md) |
| 07 | [07-ux-design-system-summary.md](../07-ux-design-system-summary.md) |
| 08 | [08-documentation-oss-summary.md](../08-documentation-oss-summary.md) |
| 09 | [09-saas-domain-summary.md](../09-saas-domain-summary.md) |

Store raw export as `docs/research/00-synthesis-2026.txt` (gitignored). Publish distilled output as **`docs/research/00-synthesis-2026-summary.md`**.

## Research objective

Synthesize a **2026 buyer and developer expectation map**. Answer:

- What is table-stakes vs differentiator in 2026?
- Is v1.3 **calibrated** or **overloaded** (especially L2 gates)?
- What belongs in **v1.4 docs** vs **v2.0 RFC** (weights, ID splits)?

## Required analysis

### 1. Buyer persona expectations (2026)

For each persona, list **must-have**, **expected**, and **delight** signals (GitHub-first, first 15 minutes):

- Solo founder / indie hacker
- Startup eng lead (5–20 engineers)
- Enterprise architect / procurement
- Agency building white-label SaaS

### 2. Category heat map

| Category | L1 table-stakes | L2 commercial bar | L3 differentiator | Common false claims |
|----------|-----------------|-------------------|-------------------|---------------------|

Categories: Architecture, Security, Angular, TypeScript, SaaS domain, Testing/CI, UX, Performance/a11y, Documentation/OSS.

### 3. Rubric gap analysis (vs v1.3)

- **Too lenient** — should be Must or L2 gate
- **Too strict** — downgrade or document demo tier
- **Missing** — defer to v2.0 with proposed ID
- **Gate overload** — recommend core L2 subset vs full L2

### 4. Competitive landscape

5–10 prominent B2B SaaS starters (Angular/React/Vue, 2024–2026): advertised features vs review complaints.

### 5. Technology trajectory (2026–2027)

Zoneless, Signal Forms, Supabase vs custom backend, AGENTS.md, EAA/VPAT, supply chain.

### 6. Recommendations

Split into:

- **v1.4 quick wins** (docs only, no ID changes)
- **v2.0 RFC candidates** (weights, S1a/S1b, FSD tags)

## Output format

1. Executive summary (≤300 words)
2. Buyer expectation matrix
3. Category heat map
4. Rubric v1.3 gap analysis
5. Competitive landscape table
6. 2026–2027 trajectory
7. v1.4 vs v2.0 recommendations (numbered)
8. Bibliography

## Source quality rules

- Prefer sources **2024–2026**.
- Distinguish **demo** vs **production** requirements.
- Do not treat marketing pages as engineering evidence.
