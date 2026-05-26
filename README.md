# Quality Framework

An open quality standard for **Angular B2B SaaS** frontends (2025–2026): rubric, maturity levels, and adoption guides—not a flat checklist.

**Version:** 1.1.0 (see [CHANGELOG.md](./CHANGELOG.md))

## What this is

Quality Framework helps teams and OSS maintainers answer:

- What does “production-ready” mean for an Angular workspace / admin dashboard starter?
- How do we prove quality to users without **checklist washing**?
- What should be automated in CI vs documented for humans?

It targets apps built with **Angular 21+**, **Nx**, **ports & adapters**, design systems (e.g. Spartan + Tailwind v4), and SaaS domains: **multi-tenant workspaces**, **billing**, **members**, **RBAC**.

## Why not just a checklist?

Static Markdown checkboxes are easy to tick without matching reality. Quality Framework uses a **hybrid model**:

| Layer | Artifact | Purpose |
|-------|----------|---------|
| Philosophy | [docs/standard.md](./docs/standard.md) | Why rubric + gates + maturity |
| Criteria | [docs/rubric/](./docs/rubric/) | Verifiable Must / Should / Could |
| Scoring | [docs/maturity.md](./docs/maturity.md), [docs/scoring.md](./docs/scoring.md) | L1–L3 levels, weighted score |
| Automation | CI, ESLint, Scorecard (in *your* app repo) | Enforce what can be enforced |
| AI context | [templates/AGENTS.md.template](./templates/AGENTS.md.template) | Machine-readable repo rules |

## Quick start

1. Read [docs/standard.md](./docs/standard.md) (10 min).
2. Copy [templates/SELF_ASSESSMENT.md.template](./templates/SELF_ASSESSMENT.md.template) into your app repo as `docs/QUALITY.md`.
3. Score against [docs/rubric/](./docs/rubric/README.md).
4. Publish your level honestly (see [Maturity badges](#maturity-badges)).

## Documentation

| Doc | Description |
|-----|-------------|
| [docs/README.md](./docs/README.md) | Index |
| [docs/standard.md](./docs/standard.md) | Standard overview & non-negotiables |
| [docs/maturity.md](./docs/maturity.md) | L1 / L2 / L3 thresholds |
| [docs/scoring.md](./docs/scoring.md) | How to calculate the 0–1000 score |
| [docs/implementation.md](./docs/implementation.md) | Where to implement in an Nx monorepo |
| [docs/roadmap.md](./docs/roadmap.md) | 90-day adoption plan |
| [docs/evolution.md](./docs/evolution.md) | How the framework evolves (v1.1+) |
| [docs/research/](./docs/research/) | Deep research reports & summaries |
| [docs/anti-patterns.md](./docs/anti-patterns.md) | Legacy practices to avoid |
| [docs/bibliography.md](./docs/bibliography.md) | Sources |

## Reference implementations

These projects use ports & adapters and align with parts of the rubric. **Self-assessed levels are maintained by each repo**—do not infer compliance from this list alone.

| Project | Role | Quality notes |
|---------|------|----------------|
| [oequ/angular-saas-starter-ui](https://github.com/oequ/angular-saas-starter-ui) | Angular UI monorepo + demo | Ports, mock adapters, Playwright E2E |
| [oequ/saas-starter](https://github.com/oequ/saas-starter) | Full-stack (Supabase, RLS) | Backend + tenant isolation |

## Maturity badges

Optional README badge (replace level when you publish a self-assessment):

```markdown
[![Quality Framework: L1 Starter-ready](https://img.shields.io/badge/Quality_Framework-L1_Starter--ready-0ea5e9)](https://github.com/oequ/quality-framework#maturity-levels)
```

Only claim **L2** or **L3** after meeting the thresholds in [docs/maturity.md](./docs/maturity.md) and documenting evidence.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md). Rubric changes use stable criterion IDs (`A1`, `NG5`, `SaaS6`, …).

## License

MIT — [LICENSE](./LICENSE)
