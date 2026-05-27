# RFC — Quality Framework v2.0 candidates

**Status:** Proposed — not scheduled. Minor releases (v1.x) must not implement breaking changes without an approved RFC.

Synthesis source: [00-synthesis-2026-summary.md](../research/00-synthesis-2026-summary.md).

## Candidate changes

| RFC | Summary | Rationale | Breaking? |
|-----|---------|-----------|-----------|
| **RFC-001** | Category weight review | Raise Performance & a11y above 5% if EAA procurement evidence strengthens | Yes (scores) |
| **RFC-002** | S1a / S1b split | Separate criterion IDs for demo meta CSP vs production HTTP CSP | Yes (IDs) |
| **RFC-003** | SaaS2 L2 gate | Require `/org/:id` (or equivalent) for L2 badge | Yes (gates) |
| **RFC-004** | Core L2 vs full L2 badge | Optional second badge for subset of gates | Yes (maturity model) |
| **RFC-005** | FSD Nx tags | Optional `type:entity`, `type:widget` in implementation guide | Maybe |
| **RFC-006** | Normative procurement appendix | Promote [procurement-appendix.md](../procurement-appendix.md) to maintained buyer kit | No |

## Process

1. Open GitHub issue with `rubric-feedback` label referencing RFC id.
2. Link evidence (research summary, buyer feedback, reference repo).
3. If approved for v2.0: migration guide, CHANGELOG major section, announce score recalculation.

## Declined / merged elsewhere

| Idea | Resolution |
|------|------------|
| T11 = dependency cooldown | **T12** in v1.2 |
| axe as optional | **P1 L2 gate** in v1.2 |
| AGENTS.md L3-only | **D1 Must** since v1.0 |

[← Evolution](../evolution.md)
