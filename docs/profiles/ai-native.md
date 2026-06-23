# AI-Native Quality Profile

**Status:** Draft v1.5 candidate  
**Scope:** AI SaaS products that charge for AI work, run asynchronous AI jobs, generate user-visible content, or execute agentic workflows.  
**Core score impact:** none. This is an optional profile on top of the base Quality Framework score.

## Why this profile exists

The core Quality Framework rubric measures Angular B2B SaaS quality. AI-native SaaS adds failure modes that the core rubric should not force onto every adopter:

- AI work is expensive and probabilistic.
- Async provider calls fail, retry, and deliver duplicate webhooks.
- Agents can loop, call unsafe tools, or leak secrets through prompts.
- Generated content is increasingly regulated.
- Flat subscriptions no longer cover unpredictable agentic inference costs.

This profile defines evidence-based quality criteria for the production AI layer while keeping the core rubric focused.

## Profile badges

| Badge | Meaning |
|-------|---------|
| [Cost-safe](./ai-cost-safe.md) | The product can charge for AI work without losing money through race conditions, runaway usage, or provider-cost drift. |
| [Agent-ready](./ai-agent-ready.md) | The product can run agentic workflows with validated specs, scoped tools, approvals, and safe execution boundaries. |
| [Compliance-ready](./ai-compliance-ready.md) | The product can disclose, audit, and preserve provenance for AI-generated or AI-modified content. |

## Criteria summary

| ID | Criterion | Level | Badge | Applies to |
|----|-----------|-------|-------|------------|
| **AI1** | Atomic AI credit ledger lifecycle | Must | Cost-safe | Paid AI work |
| **AI2** | Spend caps and budget alerts | Must | Cost-safe | Usage-priced AI work |
| **AI3** | Async run idempotency | Must | Cost-safe | Async AI jobs and provider webhooks |
| **AI4** | Provider/model registry | Should | Cost-safe | Multi-provider or model-catalog products |
| **AI5** | AI cost and inference observability | Should | Cost-safe | Paid AI work; L3 for complex agents |
| **AI6** | Generated-content disclosure | Must | Compliance-ready | Generated or materially modified content |
| **AI7** | Content provenance strategy | Should | Compliance-ready | Media generation; L3 for regulated markets |
| **AI8** | WorkflowSpec validation | Should | Agent-ready | Agent-built or dynamic workflows |
| **AI9** | Tool permission scopes | Must | Agent-ready | Agents with tools or external API access |
| **AI10** | Secret isolation and human approval for critical actions | Must | Agent-ready | Agents with write actions or secrets |
| **AI11** | Sandboxed execution for generated code | Could | Agent-ready | Agents that execute generated or user-provided code |
| **AI12** | Prompt and model regression tests | Should | Agent-ready | Prompt templates with business-critical output |

## AI1 — Atomic AI credit ledger lifecycle

**Level:** Must  
**Badge:** Cost-safe  
**Applies to:** products that charge users for AI work.

### Requirement

AI credit accounting must separate expensive AI work into an atomic lifecycle:

```text
reserve -> finalize | refund
```

The ledger must protect against:

- charging users for failed provider calls;
- free usage through concurrent race conditions;
- stale reservations after worker or provider failure.

### Verification

- Code review of the credit ledger and job lifecycle.
- Database review for append-only ledger or equivalent immutable accounting.
- Integration test for provider failure after reserve.
- Reaper or cleanup job evidence for stale reservations.

### Example evidence

- `CreditLedgerPort` or equivalent domain boundary.
- SQL/RPC or adapter implementation for `reserve`, `finalize`, `refund`.
- Test that simulates provider failure and verifies a compensating refund entry.
- Scheduled reaper job for stale pending reservations.

### Ports note

Feature components must not mutate ledger state directly. Credit operations go through a port or backend RPC boundary.

## AI2 — Spend caps and budget alerts

**Level:** Must  
**Badge:** Cost-safe  
**Applies to:** usage-priced AI work.

### Requirement

The product must prevent billing shock through explicit limits before AI work starts.

Minimum evidence:

- org-level spend cap or credit limit;
- per-run or per-workflow maximum budget where applicable;
- budget warnings at meaningful thresholds such as 80% and 95%;
- hard stop when the configured cap is reached.

Auto top-up is allowed only with a hard monthly or billing-period maximum.

### Verification

- Adapter/backend review for pre-run limit checks.
- UI review for budget and warning states.
- Tests for insufficient budget and cap exceeded paths.

### Ports note

Quota and budget validation should be isolated behind a port or backend service so UI components cannot bypass it.

## AI3 — Async run idempotency

**Level:** Must  
**Badge:** Cost-safe  
**Applies to:** async AI jobs, provider webhooks, long-running agent turns.

### Requirement

Creating an AI run must be idempotent. Retried client requests and duplicate provider webhooks must not create duplicate expensive work or double-finalize credits.

### Verification

- API or adapter supports an idempotency key, client-provided run ID, or equivalent.
- Provider webhook handling is idempotent.
- Tests submit duplicate create requests and duplicate completion webhooks.

### Example evidence

- `Idempotency-Key` support or unique `(organization_id, idempotency_key)` constraint.
- Test that two identical create requests return the same `WorkflowRun` / job ID.
- Test that duplicate provider webhook delivery does not double-charge.

## AI4 — Provider/model registry

**Level:** Should  
**Badge:** Cost-safe  
**Applies to:** products with more than one model, provider, or model capability.

### Requirement

The product should maintain a model/provider registry that records:

- provider;
- model ID;
- capability;
- cost unit;
- availability/deprecation status;
- safety or compliance constraints;
- fallback or degradation policy when applicable.

Automatic failover is not required for L2 because models are not always behaviorally interchangeable. A clear degradation state is acceptable.

### Verification

- Registry or catalog evidence.
- UI/API behavior for unavailable/deprecated models.
- Test for provider 429/5xx handling or degradation state.

## AI5 — AI cost and inference observability

**Level:** Should  
**Badge:** Cost-safe  
**Applies to:** paid AI work; L3 expectation for complex agents.

### Requirement

AI runs should emit enough telemetry to investigate cost, latency, failures, and tool behavior.

Recommended evidence:

- provider latency;
- provider/model used;
- input/output tokens or equivalent usage unit;
- provider cost estimate or actual cost;
- trace ID through run, steps, and tool calls;
- normalized error taxonomy.

### Verification

- Observability dashboard or event store.
- Trace ID propagation through worker/tool calls.
- Sample incident investigation using run history.

## AI6 — Generated-content disclosure

**Level:** Must  
**Badge:** Compliance-ready  
**Applies to:** generated or materially modified content.

### Requirement

Users must be clearly informed when content is AI-generated or materially AI-modified.

For media and published content, the product must record metadata that supports later audit of generation origin.

### Verification

- UI disclosure on generation/export surfaces.
- Database or artifact metadata with generated-content origin.
- Policy/docs page explaining AI-generated content handling.

### Notes

This is the L2 baseline for EU AI Act Article 50 readiness. Machine-readable provenance is covered separately by AI7.

## AI7 — Content provenance strategy

**Level:** Should  
**Badge:** Compliance-ready  
**Applies to:** media generation, regulated markets, public distribution.

### Requirement

The product should define and implement a machine-readable provenance strategy for generated media or exported artifacts.

Acceptable approaches include:

- C2PA or equivalent content credentials;
- signed metadata manifest;
- watermarking strategy;
- dual-layer provenance for higher-risk media.

### Verification

- Provenance architecture doc.
- Export pipeline evidence.
- Test artifact with verifiable metadata or watermark where implemented.

### L3 note

L3 may require cross-layer integrity checks, such as detecting mismatch between metadata provenance and embedded watermark signals. Do not make vendor-specific watermark systems mandatory.

## AI8 — WorkflowSpec validation

**Level:** Should  
**Badge:** Agent-ready  
**Applies to:** agent-built, dynamic, or user-configurable workflows.

### Requirement

LLM-produced workflow specs must be validated before execution.

Minimum validation:

- strict schema validation;
- allowed tool names only;
- input/output shape validation;
- cycle detection or bounded execution plan;
- deterministic error when validation fails.

### Verification

- Schema definition, such as JSON Schema or Zod.
- Unit tests for invalid tool names, bad input types, and cyclic workflows.
- Runtime evidence that invalid specs do not execute.

## AI9 — Tool permission scopes

**Level:** Must  
**Badge:** Agent-ready  
**Applies to:** agents with tools, integrations, or external API access.

### Requirement

Agent tools must declare permission scopes and side-effect levels.

At minimum, the runtime must distinguish:

- read-only tools;
- write tools;
- destructive tools;
- external network or third-party API tools.

### Verification

- Tool registry with permissions metadata.
- Runtime checks before tool invocation.
- Tests that disallowed tools cannot be called in a restricted workflow.

## AI10 — Secret isolation and human approval for critical actions

**Level:** Must  
**Badge:** Agent-ready  
**Applies to:** agents with secrets, write actions, or customer data access.

### Requirement

Raw secrets must never be placed in prompts, model messages, or tool descriptions. Tools receive credentials through a server-side secret boundary.

Critical actions must require human approval or explicit pre-authorization.

Examples of critical actions:

- sending email or messages externally;
- writing to CRM/account systems;
- deleting or exporting data;
- purchasing, billing, or changing permissions;
- running code with external network access.

### Verification

- Secret access architecture.
- Tool specs with `needsApproval` or equivalent.
- Approval log evidence with actor, timestamp, action, and target.
- Test that write action pauses until approved.

## AI11 — Sandboxed execution for generated code

**Level:** Could  
**Badge:** Agent-ready  
**Applies to:** agents that execute generated, user-provided, or untrusted code.

### Requirement

Generated or untrusted code should run in an isolated sandbox with resource and network controls.

Examples:

- microVMs;
- containers with strict seccomp/AppArmor and non-root execution;
- WASM sandbox;
- managed sandbox service.

The rubric should require capability and evidence, not a specific vendor.

### Verification

- Sandbox architecture doc.
- Egress allowlist or deny-by-default network policy.
- Test proving access to local metadata/internal network is blocked.

## AI12 — Prompt and model regression tests

**Level:** Should  
**Badge:** Agent-ready  
**Applies to:** prompt templates or model calls that produce business-critical output.

### Requirement

Business-critical prompts should be versioned and tested against stable fixtures or golden sets.

Regression tests should verify:

- required structured output shape;
- refusal/validation behavior;
- known edge cases;
- no unsupported tool selection;
- acceptable quality thresholds where measurable.

### Verification

- Prompt/version registry.
- Eval or test suite in CI or scheduled jobs.
- Changelog for prompt/model changes.

## Profile gate guidance

### Cost-safe badge

Required:

- AI1 Pass
- AI2 Pass
- AI3 Pass

Recommended:

- AI4 Partial/Pass when multiple models/providers exist
- AI5 Partial/Pass for production usage

### Agent-ready badge

Required:

- AI9 Pass
- AI10 Pass

Required when workflows are generated by an LLM:

- AI8 Pass

Required when generated code is executed:

- AI11 Pass

Recommended:

- AI12 Pass for business-critical prompts

### Compliance-ready badge

Required:

- AI6 Pass

Required for media generation in regulated or public-distribution contexts:

- AI7 Partial/Pass with a documented rollout plan

L3 expectation:

- AI7 Pass with durable machine-readable provenance and integrity validation.

## What not to include

- Do not require a visual no-code workflow builder.
- Do not require a specific model provider, observability vendor, or sandbox vendor.
- Do not make AI profiles mandatory for non-AI SaaS products.
- Do not require advanced media provenance for text-only internal agent products.
- Do not score vague ethics claims without evidence.

## Related docs

- [Quality Profiles](./README.md)
- [Maturity model](../maturity.md)
- [Scoring guide](../scoring.md)
- [Security rubric](../rubric/05-security.md)
- [SaaS domain rubric](../rubric/09-saas-domain.md)

