# Documentation & OSS hygiene

Trust signals for open source and AI-assisted development.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **D1** | **AGENTS.md.** Machine-readable guide: build, test, architecture, import rules. | Must | File exists | Critical for Cursor/Copilot in 2026. |
| **D2** | **ADRs.** Architecture Decision Records for major choices (ports, stack). | Should | `docs/adr/` | Signals intentional design. |
| **D3** | **OpenSSF Scorecard.** Scorecard badge or workflow in README. | Could | Scorecard Action | Objective OSS security signal. |
| **D4** | **CONTRIBUTING + SECURITY.** Contribution and vulnerability reporting policies. | Must | File exists | Baseline OSS hygiene. |
| **D5** | **Semver + changelog.** Versioned releases with changelog or GitHub releases. | Should | Tags / CHANGELOG | Fork consumers need upgrade notes. |
| **D6** | **CODEOWNERS.** Owners for `libs/ports` and critical paths. | Could | File exists | Protects contract stability. |
| **D7** | **PR template.** Checklist aligned with CI (lint, test, docs). | Must | File exists | Reduce empty checkboxes—link CI jobs. |
| **D8** | **Architecture diagrams.** Mermaid/C4 for UI → ports → adapters flow. | Should | Docs review | Onboarding for contributors. |

[← Rubric index](./README.md)
