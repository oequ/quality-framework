# Gemini Deep Research — Synthesis / Versioning Plan for Quality Framework

Copy everything below the line into Gemini Deep Research.

Use this as the final synthesis prompt for the already completed 2026 refresh research.
Attach or paste the three reviewed summaries before running it:

1. `docs/research/11-developer-platform-summary.md`
2. `docs/research/10-ai-native-summary.md`
3. `docs/research/12-security-platform-refresh-summary.md`

The task is not to restart the research from scratch. The task is to reconcile the reviewed decisions, identify conflicts, and produce a maintainer-ready release/versioning plan.

---

You are a senior standards maintainer, open-source strategy advisor, and B2B SaaS platform architect.

Today is June 23, 2026.

Research task:
Synthesize multiple research reports into a concrete evolution plan for `oequ/quality-framework` after v1.4.

Context:
Quality Framework is an open standard for Angular B2B SaaS frontend quality.

Current version:
- v1.4.0
- Rubric domains:
  1. Architecture & boundaries
  2. Angular platform
  3. TypeScript & code quality
  4. Testing & CI
  5. Security & privacy
  6. Performance & accessibility
  7. UX & design system
  8. Documentation & OSS hygiene
  9. SaaS domain

Current model:
- stable criterion IDs,
- Must / Should / Could,
- L1 Starter-ready,
- L2 Production-ready,
- L3 Exemplary,
- 0–1000 weighted score,
- `docs/QUALITY.md` self-assessment evidence,
- templates and adoption roadmap.

Inputs:
You will be given three reviewed summaries:

1. Developer Platform / API Console quality
   - API keys,
   - public API baseline,
   - usage events,
   - rate limits,
   - webhooks,
   - audit logs,
   - developer console UX,
   - docs-as-product.

2. AI-Native SaaS / Agent Runtime quality
   - AI credits,
   - reserve/finalize/refund,
   - async AI runs,
   - provider/model registry,
   - spend caps,
   - AI observability,
   - EU AI Act Article 50,
   - agent workflow runtime,
   - approvals/evidence/traces.

3. Security / Platform Refresh 2026
   - Nx Console compromise,
   - MCP STDIO risks,
   - Supabase explicit grants,
   - `security_invoker = true`,
   - Angular 22,
   - zoneless,
   - Vitest,
   - Scorecard/SAST/CODEOWNERS.

Reviewed decisions already made from the reports:

- Developer Platform should start as an optional `Developer Platform Profile: API-ready`, not an immediate reweighting of the core 0-1000 score.
- API keys, public API contracts, quota visibility, tenant isolation, webhooks, audit logs, and idempotency should be measurable with `DP*` criteria.
- AI-native SaaS should start as optional profiles, not a core domain forced on every Angular B2B SaaS starter.
- AI profile criteria should focus on cost safety, async run reliability, provider governance, AI observability, generated-content transparency, agent tool permissions, secret isolation, approvals, sandboxing, and prompt/model regression tests.
- Generic visual workflow builders should not be scored as a quality requirement.
- The 2026 security/platform refresh should preserve stable v1.x IDs and capture breaking or stack-specific changes through RFCs.
- Supabase explicit grants, `security_invoker = true`, MCP/STDIO shell-sink containment, generated-code boundary drift, stronger supply-chain checks, Scorecard threshold review, Angular 22, Vitest, and zoneless changes need careful versioning.
- Do not rename stable criterion IDs or make Angular 22 / Vitest / OnPush L1-breaking requirements in a minor release without a migration path.

Existing draft files to evaluate, not blindly accept:

- `docs/profiles/developer-platform.md`
- `docs/profiles/ai-native.md`
- `docs/profiles/ai-cost-safe.md`
- `docs/profiles/ai-agent-ready.md`
- `docs/profiles/ai-compliance-ready.md`
- `docs/rfc/RFC-007-platform-security-refresh-2026.md`
- updates to `README.md`, `docs/README.md`, `docs/evolution.md`, `docs/maturity.md`, `docs/scoring.md`, `templates/SELF_ASSESSMENT.md.template`, and `CHANGELOG.md`

Main problem:
Quality Framework should evolve without becoming a giant checklist. It must preserve clarity, evidence-based scoring, stable IDs, and adoption friendliness.

Strategic questions:
1. Should the next release be v1.5, v2.0, or a staged v1.5 + v2.0 RFC track?
2. Should Developer Platform remain an optional profile for v1.5, become a core 10th domain, or be prepared as a v2.0 candidate?
3. Should AI-Native SaaS remain optional profiles, become:
   - an appendix,
   - an optional profile,
   - a companion standard,
   - or a core domain?
4. Should existing score weights change?
5. Should L3 become “Enterprise-ready” instead of “Exemplary”?
6. Should profiles/badges be introduced?
7. Which draft profile criteria are too broad, too vendor-specific, or too product-specific?
8. How should old adopters migrate without breaking self-assessments?
9. Which draft files should ship in v1.5 as stable, draft, or RFC-only?

Possible profile badges:

```text
Quality Framework: L1 Starter-ready
Quality Framework: L2 Production-ready
Quality Framework: L3 Enterprise-ready
Developer Platform Profile: API-ready
AI-Native Profile: Cost-safe
AI-Native Profile: Agent-ready
Enterprise Profile: Audit-ready
```

Constraints:
- Do not break stable IDs casually.
- Do not make every product satisfy AI-native requirements.
- Do not force public API requirements on SaaS products that are not API-first unless using an optional profile.
- Do not make L1 too hard for useful OSS starters.
- Do not let L2 mean “demo with some docs”.
- Avoid checklist washing.

Output objectives:
Produce a concrete maintainer-ready plan.

Required output:

1. Executive recommendation
   - v1.5 vs v2.0,
   - core vs optional profiles,
   - maturity model changes.

2. Proposed documentation structure
   Example:

   ```text
   docs/rubric/
     01-architecture.md
     ...
     09-saas-domain.md
     10-developer-platform.md

   docs/profiles/
     ai-native.md
     developer-platform.md
     enterprise.md
   ```

3. Criterion ID strategy
   - New prefixes,
   - whether to reserve `DP*`, `AI*`, `ENT*`,
   - how to avoid ID churn.

4. Scoring and maturity recommendation
   - Whether to adjust 0–1000 weights,
   - whether optional profiles affect base score,
   - L1/L2/L3 thresholds,
   - any new gates.

5. Migration plan
   - v1.4 → v1.5 or v2.0,
   - updates to `SELF_ASSESSMENT.md.template`,
   - updates to `AGENTS.md.template`,
   - changes to `docs/QUALITY.md` examples,
   - CHANGELOG and migration guide outline.

6. Release roadmap
   - 30 days,
   - 60 days,
   - 90 days.

7. Backlog of concrete issues
   - Each issue should have title, scope, affected files, acceptance criteria.

8. Review of existing draft files
   - Which files are ready.
   - Which files need edits before release.
   - Which files should remain draft/RFC only.
   - Any contradictions between summaries and draft docs.

9. What not to include
   - Over-broad or too-product-specific ideas.

10. Open questions for maintainers.

11. Sources and evidence mapping.

Decision lens:
Quality Framework should remain a standard that helps teams prove production trust. It should not become marketing material, a vendor checklist, or a product roadmap for one starter.

Be opinionated:
- Recommend a narrow, maintainable structure.
- Prefer optional profiles for specialized domains.
- Keep the core useful for Angular B2B SaaS starters.
- Make API-first SaaS and AI-native SaaS measurable without forcing every adopter into those categories.

