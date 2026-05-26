# Deep Research — Documentation & OSS hygiene (D1–D8)

Weight: 5% of total score. AGENTS.md is L1-relevant.

---

## Role

You are an open-source program manager and developer relations engineer specializing in **credible OSS starters** and **AI-assisted development workflows**.

## Context

Quality Framework v1.0 Documentation & OSS criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| D1 | AGENTS.md (machine-readable AI context) | Must |
| D2 | ADRs (Architecture Decision Records) | Should |
| D3 | OpenSSF Scorecard | Could |
| D4 | CONTRIBUTING.md + SECURITY.md | Must |
| D5 | Semver + changelog | Should |
| D6 | CODEOWNERS | Could |
| D7 | PR template with CI checklist | Must |
| D8 | Architecture diagrams (Mermaid/C4) | Should |

## Research questions

### 1. 2026 OSS starter credibility signals

What documentation artifacts do **developers and buyers** expect within 5 minutes of landing on a GitHub repo?

- README structure best practices (2025–2026 examples)
- Badges that help vs hurt credibility
- Live demo URL, stack pins, honest limitations section
- Comparison with "awesome list" entry requirements

### 2. AGENTS.md and AI coding era (D1)

Deep dive on **AGENTS.md / CLAUDE.md / .cursor/rules** as quality signals:

- Who publishes AGENTS.md standards (OpenAI, Cursor, community)?
- What sections correlate with successful AI-assisted forks?
- Should rubric expand D1 with required sections (commands, boundaries, do-not)?
- Enterprise concerns: IP, security, AI-generated code liability

### 3. Architecture documentation (D2, D8)

- ADR adoption in frontend repos — rare or growing?
- Mermaid vs C4 vs diagrams.net — what enterprises prefer
- Minimum ADR count for L2/L3
- Ports-and-adapters diagram standards

### 4. Security and contribution hygiene (D4, D7)

- SECURITY.md — coordinated disclosure templates (GitHub standard)
- CONTRIBUTING.md — DCO vs CLA vs none
- PR templates that actually get used — examples from high-trust repos
- Issue templates for bugs vs security

### 5. Release engineering (D5)

- Semver for application starters (0.x forever?)
- CHANGELOG formats — Keep a Changelog still standard?
- GitHub Releases vs changelog file
- Buyer expectation for migration guides between starter versions

### 6. OpenSSF and supply chain (D3)

- Scorecard score interpretation — what is achievable for a small starter?
- Score ≥8.5 for L3 — realistic timeline and cost
- Other badges: OpenSSF Best Practices, SLSA level

### 7. Governance (D6)

- CODEOWNERS for community starters — when needed?
- Maintainer burnout and bus factor documentation

### 8. L1 / L2 / L3 mapping

| ID | 2026 L1 | 2026 L2 | 2026 L3 |
|----|---------|---------|---------|

Should D1 AGENTS.md be **Must** for all levels or only L1+?

### 9. Marketing vs engineering documentation

How should a **commercial OSS starter** (MIT, upsell to support) balance:

- Honest gaps (demo vs production)
- Quality Framework self-assessment publication
- Landing page vs repo docs consistency

## Output format

1. Executive summary — documentation bar for trustworthy SaaS starter (2026)
2. README template outline (section headings + 1-line purpose each)
3. AGENTS.md recommended schema (required sections)
4. Minimum OSS hygiene file set (L1 vs L2 vs L3)
5. L1/L2/L3 mapping (D1–D8)
6. OpenSSF Scorecard quick-win checklist for frontend monorepo
7. Bibliography (OpenSSF, GitHub docs, Write the Docs, CNCF project maturity models)

## Source priorities

- security.opensff.org (Scorecard, Best Practices badge)
- docs.github.com (SECURITY.md, community health)
- AGENTS.md community spec (if exists) and Cursor/Copilot documentation guidance
- Architecture Decision Records (adr.github.io)
- CNCF maturity model / Apache project graduation criteria (adapted for small OSS)

## Constraints

- Starter is MIT-licensed single-repo, not a foundation-scale project.
- Avoid documentation criteria that create maintenance burden without buyer value.
