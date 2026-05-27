# Research summary — Documentation & OSS hygiene (May 2026)

Source: [A Comprehensive Framework for AI-Assisted Architecture, Security, and Governance Compliance.txt](./A%20Comprehensive%20Framework%20for%20AI-Assisted%20Architecture%2C%20Security%2C%20and%20Governance%20Compliance.txt)

## Executive summary

2026 OSS starters must serve **dual audience**: human buyers (5-minute README credibility) and **AI agents** (AGENTS.md). Curated AGENTS.md reduces agent runtime ~29% vs unguided runs; auto-generated agent configs **hurt** (higher cost, lower success). Enterprise expects **Scorecard**, **SECURITY.md**, ADRs, and a published **Quality Framework self-assessment**.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.3) |
|-------|----------------|----------------------|
| D1 AGENTS.md | Must at all levels; &lt;150 lines; permission boundaries | Expand D1 schema |
| D3 Scorecard | L2: workflow + score ≥ 6.5; L3: ≥ 8.5 | D3 Should; **L2 gate** ≥ 6.5 |
| D2 ADRs | L2: 3–5 ADRs on ports/stack | Clarify D2 tiers |
| D6 CODEOWNERS | L2 for `libs/ports` | D6 Should for L2 |
| D9 (new) | README: demo URL, limitations, stack matrix | Add D9 Should |
| D10 (new) | Published `docs/QUALITY.md` with evidence links | Add D10 Should; L2 gate |
| Semver | Promote to 1.0.0 when stable; avoid perpetual 0.x | Clarify D5 |
| Issues | Separate public bug vs private security (PVR) | anti-patterns |

## L1 / L2 / L3 (research view)

| ID | L1 | L2 | L3 |
|----|----|----|-----|
| D1 | Build/test/architecture rules | Nested AGENTS + symlinks | CI agent dry-runs / guardrails |
| D3 | Scorecard workflow exists | Score ≥ 6.5 published | Score ≥ 8.5, pinned workflows |
| D7 | PR template | Template + CI links | Full gate checklist in PR |
| D8 | Optional diagram | Mermaid C4 in docs | Diagrams match deployment |

## Top actions for adopters

1. Root `AGENTS.md` with forbidden actions (no adapters in features).
2. README: live demo, honest limitations, Scorecard badge.
3. `docs/QUALITY.md` from framework template with CI links.
4. `docs/adr/` — minimum ADR for ports, auth, billing.
5. OpenSSF Scorecard Action on default branch.

[← Research index](./README.md)
