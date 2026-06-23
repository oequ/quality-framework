# Scoring guide

How to turn rubric results into a **0–1000** score and a maturity level (L1–L3).

## Formula

For each **category** (see [maturity.md](./maturity.md)):

1. List all criteria in that category from [rubric/](./rubric/README.md).
2. Assign points per criterion:
   - **Must** — weight `1.0`
   - **Should** — weight `0.5`
   - **Could** — weight `0.2`
3. Score each criterion:
   - **Pass** = full weight
   - **Partial** = half weight (document why)
   - **Fail** = 0
   - **N/A** = exclude from denominator (document why)
4. **Category %** = earned ÷ possible
5. **Category points** = category % × category max (e.g. Architecture max 200)

**Total score** = sum of category points (max 1000).

Optional [Quality Profiles](./profiles/README.md) are scored separately from the base 0-1000 total. Profile criteria may be Pass / Partial / Fail / N/A, but they do not add points to the core score.

## Worked example (illustrative)

Architecture category (max 200). Suppose 8 Must × 1.0 + 4 Should × 0.5 = 10.0 possible weight units.

| ID | Level | Result | Earned |
|----|-------|--------|--------|
| A1 | Must | Pass | 1.0 |
| A2 | Must | Fail | 0 |
| A3 | Must | Pass | 1.0 |
| … | … | … | … |

If earned = 7.0 / 10.0 → 70% → **140 / 200** architecture points.

Repeat for all categories, then sum.

## Mapping score to level

| Score | Level |
|-------|-------|
| > 950 | L3 Exemplary |
| > 800 | L2 Production-ready |
| > 600 | L1 Starter-ready |
| ≤ 600 | Below L1 — publish gaps, do not use badge |

**Additional gates for L1:** 100% of **Must** in Architecture, Security, and Angular—even if total score > 600. **Partial does not count as Pass** for gates.

**Additional gates for L2:** Full checklist in [l2-gates.md](./l2-gates.md) (16 gates).

**Rubric criteria last changed in v1.3** (SaaS8–12, U11–13, D9–10). v1.4 added documentation only.

**Optional profile criteria:** Draft profile IDs such as `DP1`–`DP8` and `AI1`–`AI12` are additive evidence tracks. Do not mix profile points into the 0-1000 core score unless a future major release changes the scoring model.

## Publishing results

In your repo’s `docs/QUALITY.md` (from template):

```markdown
## Summary

- **Rubric version:** Quality Framework v1.0
- **Date:** 2026-05-17
- **Score:** 682 / 1000
- **Level:** L1 Starter-ready (self-assessed)
- **Evidence:** [CI](link), [boundaries lint](link)
```

## Honesty guidelines

- Do not count **Partial** as Pass for badge eligibility.
- Mark demo-only auth/storage as **Fail** for production Must security criteria, with note “demo exception.”
- Pin rubric version when you assess; use [l2-gates.md](./l2-gates.md) for L2 claims.
- Pin profile version/status separately when claiming optional profile badges.

[← Maturity model](./maturity.md)
