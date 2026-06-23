# Developer Platform / API Console Summary

**Status:** reviewed summary  
**Date:** 2026-06-23  
**Prompt:** [2026-refresh/10-developer-platform-api-console.md](./prompts/2026-refresh/10-developer-platform-api-console.md)  
**Rubric impact:** optional API-ready profile; possible future core domain

## Executive summary

API-first SaaS products require a quality layer that is more specific than generic SaaS UI quality. Developer-platform surfaces introduce risks around long-lived machine secrets, public API contracts, usage limits, webhooks, idempotency, audit logs, and tenant isolation for machine-to-machine access.

The research recommends a new **Developer Platform / API Console** quality domain. The immediate implementation keeps this as an optional profile:

```text
Developer Platform Profile: API-ready
```

This avoids changing the core 0-1000 score before synthesis decides whether the criteria should become a weighted `docs/rubric/10-developer-platform.md` domain.

## Accepted direction

| Finding | Decision |
|---------|----------|
| API keys deserve stronger treatment than the current `SaaS9 Could` | Accepted as `DP1 Must` in the API-ready profile |
| Public API contracts need explicit quality criteria | Accepted as `DP2 Must` |
| Developer console UX and docs-as-product should be measured | Accepted as `DP3 Should` |
| Rate limits and quota visibility are production requirements | Accepted as `DP4 Must` |
| Webhook infrastructure should be inspectable and retryable | Accepted as `DP5 Should` |
| Developer-platform actions need audit evidence | Accepted as `DP6 Should` |
| Idempotency matters for transactional endpoints | Accepted as `DP7 Could / L3` for now |
| Multi-tenant APIs require backend/database isolation evidence | Accepted as `DP8 Must` |

## Changes from raw research

The raw report recommended making Developer Platform a full core domain in v1.5 with conditional scoring. The reviewed decision is more conservative:

- Add an optional profile now.
- Do not reweight the base 0-1000 score in v1.x.
- Keep `SaaS9`, `SaaS10`, and related core criteria stable until synthesis.
- Treat `docs/rubric/10-developer-platform.md` as a possible future v2.0 or v1.5-RFC outcome.

The raw report also contained framework-specific and malformed code snippets. These were not copied into the profile. Criteria are expressed as capabilities and evidence, not vendor or framework requirements.

## Criteria mapped into profile

| Research concept | Framework criterion |
|------------------|---------------------|
| Secure API key storage and lifecycle | `DP1` |
| Versioned public API contract | `DP2` |
| Console UX and docs-as-product | `DP3` |
| Rate limits and quota visibility | `DP4` |
| Webhook signing, retries, delivery log | `DP5` |
| Developer audit log | `DP6` |
| Idempotency keys | `DP7` |
| Tenant isolation for API access | `DP8` |

## Proposed files

- [profiles/developer-platform.md](../profiles/developer-platform.md)

## Open questions

1. Should `Developer Platform Profile: API-ready` become a weighted core domain in v1.5, v2.0, or remain optional?
2. Should `DP7` idempotency move from Could/L3 to Should/L2 for APIs that create billable work?
3. Should `DP8` be L2 or L1 for any multi-tenant API?
4. Should API console UX remain in this profile or partly move to UX/design-system criteria?
5. How should profile scoring handle products with internal APIs but no public developer console?

## Recommended next step

Keep Developer Platform as an optional profile until:

1. Security/Platform refresh research is reviewed.
2. Synthesis decides profile vs core domain.
3. At least one reference implementation self-assesses against `DP1`–`DP8`.

