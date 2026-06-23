# AI-Native Profile: Cost-safe

**Status:** Draft v1.5 candidate  
**Purpose:** prove that an AI SaaS product can charge for AI work without losing money through race conditions, failed provider calls, runaway usage, or provider-cost drift.

## Required criteria

| ID | Criterion | Required result |
|----|-----------|-----------------|
| [AI1](./ai-native.md#ai1--atomic-ai-credit-ledger-lifecycle) | Atomic AI credit ledger lifecycle | Pass |
| [AI2](./ai-native.md#ai2--spend-caps-and-budget-alerts) | Spend caps and budget alerts | Pass |
| [AI3](./ai-native.md#ai3--async-run-idempotency) | Async run idempotency | Pass |

## Recommended criteria

| ID | Criterion | Target |
|----|-----------|--------|
| [AI4](./ai-native.md#ai4--providermodel-registry) | Provider/model registry | Partial or Pass when multiple models/providers exist |
| [AI5](./ai-native.md#ai5--ai-cost-and-inference-observability) | AI cost and inference observability | Partial or Pass for production usage |

## Evidence checklist

- Credit ledger supports `reserve`, `finalize`, and `refund`.
- Stale reservations are cleaned up by a reaper or equivalent recovery process.
- Duplicate create requests do not start duplicate expensive jobs.
- Duplicate provider webhooks do not double-finalize credits.
- Org-level budget or spend cap is enforced before AI work starts.
- Budget warnings are visible at meaningful thresholds.
- Provider/model cost attribution is available for investigation.

## Typical failures

- Charging users immediately before provider calls without refund path.
- Finalizing credits from provider webhooks without idempotency.
- Unlimited auto top-up with no hard monthly cap.
- Cost tracking only in provider dashboards, not in the product database or telemetry.

## Related criteria

- [SaaS3 — Billing via port](../rubric/09-saas-domain.md)
- [SaaS10 — Usage metering UX](../rubric/09-saas-domain.md)
- [T1 — E2E testing](../rubric/04-testing-ci.md)
- [S9 — Guards are UX only](../rubric/05-security.md)

