# AI-Native SaaS / Agent Runtime Summary

**Status:** reviewed summary  
**Date:** 2026-06-23  
**Prompt:** [2026-refresh/11-ai-native-saas-agent-runtime.md](./prompts/2026-refresh/11-ai-native-saas-agent-runtime.md)  
**Rubric impact:** optional profiles, not core scoring

## Executive summary

AI-native SaaS introduces quality risks that are not covered by the base Angular B2B SaaS rubric:

- expensive and probabilistic provider calls;
- async job failures and duplicate webhooks;
- runaway agent loops;
- secret leakage through prompts and tools;
- generated-content disclosure and provenance obligations;
- auditability of tool calls, approvals, and workflow steps.

The research recommendation is to add **optional AI-Native Quality Profiles**, not to merge AI criteria into the core 0-1000 score.

Recommended profiles:

```text
AI-Native Profile: Cost-safe
AI-Native Profile: Agent-ready
AI-Native Profile: Compliance-ready
```

This preserves the core framework for non-AI Angular B2B SaaS while giving commercial AI products evidence-based gates.

## Accepted direction

| Finding | Decision |
|---------|----------|
| AI-specific criteria should not dilute the core rubric | Accepted |
| Profiles should use stable IDs and evidence in `docs/QUALITY.md` | Accepted |
| Cost-safe should focus on credit lifecycle, caps, idempotency | Accepted |
| Agent-ready should focus on validated workflow specs, scoped tools, secret isolation, approvals | Accepted |
| Compliance-ready should focus on disclosure and provenance | Accepted |
| Generic visual workflow builders should not be scored | Accepted |

## Criteria mapped into profiles

| Research concept | Framework criterion |
|------------------|---------------------|
| Atomic AI transaction lifecycle | `AI1` |
| Billing shock prevention | `AI2` |
| Async run idempotency | `AI3` |
| Provider registry and failover | `AI4` |
| Inference observability | `AI5` |
| EU AI Act Article 50 / disclosure | `AI6` |
| C2PA / watermarking / provenance | `AI7` |
| Deterministic workflow spec validation | `AI8` |
| Tool permission scopes | `AI9` |
| Secret isolation and approval | `AI10` |
| Sandboxed generated-code execution | `AI11` |
| Prompt/model regression tests | `AI12` |

## Changes from raw research

Some raw recommendations were too strict for L2 or too vendor-specific. They were softened:

- C2PA + invisible watermark + public verifier is not L2 Must for every product. L2 requires disclosure and origin metadata; machine-readable provenance is `AI7 Should`, with L3 stronger expectations.
- MicroVM execution is not required for every AI product. It is required only when generated or untrusted code is executed.
- Dynamic provider failover is not required for L2 because models are not always interchangeable. A provider/model registry and degradation behavior are enough for `AI4 Should`.
- Vendor-specific examples such as E2B, Vercel Sandbox, Langfuse, SynthID, Digimarc, and HSMs are examples, not requirements.
- Long family IDs such as `AI-LEDG-01` were simplified to stable profile IDs `AI1`–`AI12` for consistency with the existing rubric style.

## Proposed files

- [profiles/README.md](../profiles/README.md)
- [profiles/ai-native.md](../profiles/ai-native.md)
- [profiles/ai-cost-safe.md](../profiles/ai-cost-safe.md)
- [profiles/ai-agent-ready.md](../profiles/ai-agent-ready.md)
- [profiles/ai-compliance-ready.md](../profiles/ai-compliance-ready.md)

## Open questions

1. Should AI profiles ship in v1.5 as draft profiles or wait for v2.0?
2. Should profile badges be published in the root README before at least one reference implementation self-assesses?
3. Should AI criteria remain `AI1`–`AI12`, or should the project reserve family prefixes such as `AICost*`, `AIAgent*`, and `AIComp*`?
4. Should `AI6` apply to text-only internal assistants, or only to externally visible generated content?
5. Should `AI12` become part of Testing & CI instead of the AI profile?

## Recommended next step

Keep the profile docs as draft v1.5 candidates until:

1. Developer Platform research is reviewed.
2. Security/Platform refresh research is reviewed.
3. Synthesis decides v1.5 vs v2.0 and profile badge wording.

