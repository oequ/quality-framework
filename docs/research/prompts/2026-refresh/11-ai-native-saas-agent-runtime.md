# Gemini Deep Research — AI-Native SaaS / Agent Runtime Quality Rubric

Copy everything below the line into Gemini Deep Research.

---

You are a senior AI SaaS architect, AI billing systems researcher, and software quality standards author.

Today is June 23, 2026.

Research task:
Design an optional Quality Framework module or profile for **AI-native SaaS quality**, including AI economics, async AI runs, provider reliability, generated-content compliance, and agent workflow runtime.

Context:
`oequ/quality-framework` is currently an open quality standard for Angular B2B SaaS frontends. It uses stable criterion IDs, Must/Should/Could levels, L1/L2/L3 maturity, and evidence-based scoring.

Current domains:
1. Architecture & boundaries
2. Angular platform
3. TypeScript & code quality
4. Testing & CI
5. Security & privacy
6. Performance & accessibility
7. UX & design system
8. Documentation & OSS hygiene
9. SaaS domain

Example product layering (common among maintained SaaS starters):

```text
OSS SaaS Starter:
  generic SaaS and developer-platform primitives

AI-native SaaS extension:
  AI credit ledger, async AI runs, provider/model registry,
  token/provider-cost metering, spend caps, AI observability,
  generated-content compliance, agent workflow runtime

Domain-specific SaaS products:
  vertical workflows, domain data, prompts, catalogs, and GTM
```

Research framing:
Evaluate AI-native quality for products that charge for AI work. Do not assume every adopter ships a generic visual workflow builder; prefer criteria for reliable execution, evidence, auditability, and domain-specific outcomes behind the scenes.

Research objective:
Determine how Quality Framework should cover AI-native SaaS quality without bloating the core Angular B2B SaaS rubric.

Possible forms:
- optional appendix,
- optional profile badge,
- new domain file,
- separate companion standard.

Possible profile:

```text
AI-Native Profile: Cost-safe
AI-Native Profile: Agent-ready
AI-Native Profile: Compliance-ready
```

Research topics:

A. AI credit ledger and cost safety
- reserve/finalize/refund lifecycle,
- reaper for stale reservations,
- provider-cost reconciliation,
- prepaid credits,
- auto top-up,
- spend caps,
- budget alerts,
- pre-run cost previews,
- billing shock protection,
- per-org/per-user/per-key attribution,
- margin visibility.

B. Async AI run lifecycle
- queued/running/succeeded/failed/cancelled states,
- idempotent job creation,
- idempotent webhooks,
- retry and timeout policies,
- canonical output storage,
- user-facing failure states,
- provider degradation handling.

C. Provider/model registry
- provider abstraction,
- model catalog,
- provider allowlists,
- per-model limits,
- fallback policy,
- latency/cost/failure tracking,
- model deprecation handling.

D. AI observability
- provider latency,
- provider failures,
- cost per run,
- token usage,
- trace links,
- tool call logs,
- error taxonomy,
- alerting for anomalies.

E. Generated-content compliance
- AI disclosure in UI,
- EU AI Act Article 50 transparency,
- generated-content metadata,
- C2PA or watermarking strategy,
- prompt/output audit trail,
- abuse monitoring,
- NSFW or policy filters where applicable,
- data retention and training opt-out.

F. Agent workflow runtime
- `WorkflowSpec`,
- `WorkflowRun`,
- `StepRun`,
- tool registry,
- tool-call traces,
- approvals,
- evidence/artifacts,
- scheduled/manual runs,
- human-in-the-loop review,
- run history,
- cost limits per workflow,
- deterministic validation of LLM-produced specs.

G. Agent security and permissions
- tool permission scopes,
- secret isolation,
- no raw API keys in prompts,
- prompt injection risk mitigation,
- user approval before write actions,
- audit logs for agent actions,
- safe browser/sandbox execution.

Recent ecosystem signals to consider:
- GitHub, Cursor, OpenAI Codex, and Claude Code shifted toward AI credits / metered agent economics.
- AI inference and agent calls are increasingly usage-priced rather than flat-rate.
- EU AI Act Article 50 transparency obligations for generative content start August 2, 2026; machine-readable watermarking for existing products by December 2, 2026.
- Vercel AI Gateway Allowlist and sandbox/proxy controls indicate growing demand for provider governance and network inspection.
- Horizontal workflow builders are commoditizing; defensibility comes from reliable execution, evidence, auditability, and domain packs.

Specific questions:
1. Should AI-native quality be part of the core score or an optional profile?
2. Which criteria are Must for any AI SaaS that charges users for AI work?
3. Which criteria are L2 Production-ready vs L3 Enterprise-ready?
4. How should reserve/finalize/refund be scored?
5. How should generated-content transparency be scored?
6. How should agent workflow runtime be scored without encouraging generic no-code platform bloat?
7. Which criteria should apply only to media-generation products?
8. Which criteria should apply to text/research/agent products?
9. How should this integrate with existing Security, SaaS, Testing/CI, and Documentation domains?

For each proposed criterion, provide:
- ID, suggested prefix (`AI1`, `AIR1`, or another scheme),
- title,
- level: Must / Should / Could,
- rationale,
- verification method,
- example evidence,
- ports/adapters note,
- whether it belongs in core, optional profile, or separate standard.

Output format:
1. Executive recommendation.
2. Recommended structure: appendix/profile/domain/separate standard.
3. Proposed rubric table.
4. Suggested AI-native profile badges.
5. L2/L3 gate recommendations.
6. Updates needed to existing domains.
7. Example `docs/QUALITY.md` evidence.
8. Migration plan from v1.4.
9. Risks and what not to include.
10. Sources with links.

Important:
- Be skeptical. Do not add vague “AI ethics” checkboxes.
- Prioritize criteria that prevent losing money, leaking data, overcharging users, or shipping unsafe generated content.
- Distinguish reusable AI platform primitives from vertical product workflows.
- Avoid turning Quality Framework into a giant AI product checklist.

