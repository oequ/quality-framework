# Gemini Deep Research — Quality Framework prompts

Copy-paste prompts for [Gemini Deep Research](https://gemini.google.com/) to validate and evolve [Quality Framework](../standard.md) against **2026 industry expectations**.

## How to use

1. Open Gemini → **Deep Research**.
2. Copy the full body of one prompt file (everything below the `---` line).
3. Run research. Expect 5–15 minutes per domain.
4. Save the raw export under `docs/research/` as `.txt` (gitignored) or reviewed `.md`.
5. Add or update a **summary** (`NN-domain-summary.md`) per [research README](../README.md).
6. Run `00-synthesis-2026-expectations.md` **after** at least Architecture, Security, Angular, and SaaS domain reports exist.

## Prompt index

| File | Domain | Rubric | Weight |
|------|--------|--------|--------|
| [01-architecture-and-boundaries.md](./01-architecture-and-boundaries.md) | Ports & adapters, Nx boundaries | A1–A13 | 20% |
| [02-angular-platform-2026.md](./02-angular-platform-2026.md) | Angular 21+, signals, zoneless | NG1–NG13 | 15% |
| [03-typescript-and-code-quality.md](./03-typescript-and-code-quality.md) | Strict TS, ESLint, conventions | TS1–TS11 | (cross-cutting) |
| [04-testing-and-ci.md](./04-testing-and-ci.md) | E2E, Vitest, supply chain | T1–T11 | 10% |
| [05-security-and-privacy.md](./05-security-and-privacy.md) | CSP, auth storage, XSS | S1–S10 | 20% |
| [06-performance-and-accessibility.md](./06-performance-and-accessibility.md) | WCAG 2.2, CWV, a11y | P1–P10 | 5% |
| [07-ux-and-design-system.md](./07-ux-and-design-system.md) | Loading/empty/error, Tailwind v4 | U1–U10 | 10% |
| [08-documentation-and-oss.md](./08-documentation-and-oss.md) | AGENTS.md, ADRs, Scorecard | D1–D8 | 5% |
| [09-saas-domain-b2b.md](./09-saas-domain-b2b.md) | Tenancy, billing, RBAC | SaaS1–SaaS7 | 15% |
| [00-synthesis-2026-expectations.md](./00-synthesis-2026-expectations.md) | Cross-domain synthesis (run after 01–09) | All | — |

## Recommended order

```text
Security → Architecture → Angular → SaaS domain → Testing/CI
→ UX → Performance/a11y → TypeScript → Documentation/OSS → Synthesis
```

Security and Architecture first — they gate L1 credibility for B2B buyers.

## What to do with results

- Compare findings to a reference app’s self-assessment ([SELF_ASSESSMENT template](../../../templates/SELF_ASSESSMENT.md.template)).
- Propose rubric changes with cited sources; follow [evolution.md](../../evolution.md).
- Update criterion wording only via minor/major release and [CHANGELOG.md](../../../CHANGELOG.md).
- Do **not** inflate scores based on research alone — evidence must exist in the codebase under review.

## Maturity levels (reference)

| Level | Score | Audience |
|-------|-------|----------|
| L1 Starter-ready | > 600 | OSS adopters, demos, early forks |
| L2 Production-ready | > 800 | Commercial B2B teams |
| L3 Exemplary | > 950 | Reference architecture |

Additional L1 gate: 100% Must in Architecture, Security, and Angular.
