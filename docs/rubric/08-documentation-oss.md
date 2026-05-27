# Documentation & OSS hygiene

Trust signals for open source, enterprise procurement, and AI-assisted development. See [research summary](../research/08-documentation-oss-summary.md).

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **D1** | **AGENTS.md.** Machine-readable guide: commands, architecture map, import rules, **allowed/forbidden** actions for agents (&lt;150 lines recommended). | Must | File exists | Critical for Cursor/Copilot/Claude in 2026. |
| **D2** | **ADRs.** Architecture Decision Records for major choices (ports, stack, tenancy). **L2:** 3+ ADRs in `docs/adr/`. | Should | `docs/adr/` | Signals intentional design. |
| **D3** | **OpenSSF Scorecard.** Workflow on default branch; publish score. **L2:** score ≥ 6.5. **L3:** ≥ 8.5. | Should | Scorecard Action | **L2 gate:** published score ≥ 6.5. |
| **D4** | **CONTRIBUTING + SECURITY.** Contribution guide + coordinated disclosure (private reporting path). | Must | File exists | Separate security issues from public bugs. |
| **D5** | **Semver + changelog.** Versioned releases; Keep a Changelog or GitHub Releases + local `CHANGELOG.md`. Avoid perpetual `0.x` without rationale. | Should | Tags / CHANGELOG | Fork consumers need upgrade notes. |
| **D6** | **CODEOWNERS.** Owners for `libs/ports` and critical paths. | Should | File exists | **L2 gate:** CODEOWNERS present. |
| **D7** | **PR template.** Checklist aligned with CI jobs (lint, test, build)—not unchecked vanity boxes. | Must | File exists | Link to workflow names. |
| **D8** | **Architecture diagrams.** Mermaid/C4 for UI → ports → adapters flow. | Should | Docs review | Onboarding for contributors. |
| **D9** | **README credibility.** Live demo URL (or explicit why not), stack version matrix, **honest limitations** section. | Should | README review | Five-minute buyer test. |
| **D10** | **Published self-assessment.** `docs/QUALITY.md` (from template) with rubric version, scores, evidence links. | Should | File exists | **L2 gate:** public QUALITY.md with demo vs production table. |

[← Rubric index](./README.md)
