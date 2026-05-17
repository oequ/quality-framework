# Contributing to Quality Framework

Thank you for helping improve an open standard for Angular B2B SaaS quality.

## What belongs in this repo

- Rubric criteria (verifiable, with stable IDs)
- Maturity model and scoring rules
- Templates (`AGENTS.md`, self-assessment)
- Bibliography and anti-patterns

## What does not belong here

- Application source code (belongs in your app/starter repo)
- Project-specific CI configs (document patterns in `docs/implementation.md` instead)

## Proposing rubric changes

1. Open an issue using the rubric feedback template (if available) or a plain issue describing:
   - Criterion ID (new or existing)
   - Must / Should / Could level
   - Verification method (automated vs manual)
   - Why the change matters in 2025–2026
2. For substantive changes, open a PR updating the relevant `docs/rubric/*.md` file.
3. Bump [CHANGELOG.md](./CHANGELOG.md):
   - **Patch** — clarifications, typos, examples
   - **Minor** — new Should/Could criteria, new domains
   - **Major** — renaming IDs, changing Must → Should, scoring weights

## Editorial rules

- **Language:** US English
- **Honesty:** Mark aspirational targets (e.g. full zoneless, strict CSP) clearly; many production apps are on a migration path
- **Stable IDs:** Never reuse an ID for a different meaning; deprecate instead
- **Sources:** Add links to [docs/bibliography.md](./docs/bibliography.md) when citing external standards

## Code of conduct

Be constructive. This standard is meant to help teams ship maintainable SaaS UIs, not to gatekeep.
