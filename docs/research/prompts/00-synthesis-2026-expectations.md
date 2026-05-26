# Synthesis prompt — 2026 B2B SaaS starter expectations

Run this **after** completing domain-specific research reports.

---

## Role

You are a principal engineer and product strategist specializing in **Angular B2B SaaS control-plane applications** (multi-tenant admin UIs: auth, org settings, billing, members, API keys, metrics).

## Context

We maintain **Quality Framework v1.0** — a weighted rubric (0–1000) for evaluating OSS Angular SaaS starters. Maturity levels:

- **L1 Starter-ready** (>600): credible OSS fork, mock adapters OK, honest gaps documented
- **L2 Production-ready** (>800): commercial B2B deployment, E2E, production adapter, WCAG 2.2 AA, strict CSP
- **L3 Exemplary** (>950): reference architecture, OpenSSF Scorecard ≥8.5, broad Should coverage

We have (or will attach) deep-research reports for: Architecture, Security, Angular, TypeScript, Testing/CI, Performance/a11y, UX/design system, Documentation/OSS, and SaaS domain.

## Research objective

Synthesize a **2026 buyer and developer expectation map** for commercial B2B SaaS starters built with Angular. Answer: *What is table-stakes vs differentiator in May 2026? What will buyers reject immediately?*

## Required analysis

### 1. Buyer persona expectations (2026)

For each persona, list **must-have**, **expected**, and **delight** signals when evaluating a starter repo:

- Solo founder / indie hacker
- Startup eng lead (5–20 engineers)
- Enterprise architect / procurement
- Agency building white-label SaaS

Focus on **GitHub-first evaluation** (README, live demo, badges, docs) within the first 15 minutes.

### 2. Category heat map

Produce a table mapping each rubric category to:

| Category | 2026 table-stakes (L1 minimum credible) | L2 commercial bar | L3 differentiator | Common false claims to avoid |
|----------|----------------------------------------|-------------------|-------------------|------------------------------|

Categories: Architecture, Security, Angular, SaaS domain, Testing/CI, UX, Performance/a11y, Documentation/OSS.

### 3. Rubric gap analysis

Compare Quality Framework v1.0 criteria against your synthesis:

- Criteria that are **too lenient** for 2026 (should be Must, currently Should)
- Criteria that are **too strict** or outdated (should be downgraded or N/A)
- **Missing criteria** we should add in v1.1 (with suggested IDs and weights)

### 4. Competitive landscape

Research 5–10 prominent Angular/React/Vue B2B SaaS starters, boilerplates, or "ship faster" products (2024–2026). What do they advertise? What do user reviews complain about?

### 5. Technology trajectory (2026–2027)

Short horizon scan:

- Angular zoneless adoption curve
- Signal-first vs RxJS in new projects
- Supabase/Firebase vs custom backend for starters
- AI-assisted development (AGENTS.md, Cursor rules) as quality signal
- EU/US privacy and security expectations for B2B SaaS UI

### 6. Actionable rubric v1.1 draft

Propose **5–10 concrete changes** to Quality Framework v1.1 with:

- Criterion ID (new or existing)
- Rationale (1 sentence)
- Primary source (URL)
- Impact on L1/L2/L3 gates

## Output format

1. **Executive summary** (≤300 words) — what a serious 2026 starter must prove
2. **Buyer expectation matrix** (personas × signals)
3. **Category heat map** (table)
4. **Rubric v1.0 gap analysis** (bullet list with evidence)
5. **Competitive landscape** (comparison table)
6. **2026–2027 trajectory** (bullet list)
7. **Recommended rubric v1.1 changes** (numbered, with sources)
8. **Bibliography** — prioritize official docs, OWASP, W3C, Angular team, Nx, OpenSSF, Stripe/Supabase guides; mark speculation clearly

## Source quality rules

- Prefer sources published or updated **2024–2026**.
- Distinguish **SPA demo** vs **production deployment** requirements.
- Flag regional differences (EU GDPR, US SOC2-aware buyers) where relevant.
- Do not treat marketing pages as engineering evidence.

## Attachments (if available)

When running this prompt, paste summaries or links to domain research reports produced from prompts 01–09 in this folder.
