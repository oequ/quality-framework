# Developer Platform Quality Profile

**Status:** Draft v1.5 candidate  
**Scope:** API-first SaaS products with public APIs, API keys, developer consoles, usage metering, webhooks, or integration surfaces.  
**Core score impact:** none in v1.x. This profile may become a core domain or weighted profile in a future major version.

## Why this profile exists

Modern B2B SaaS products increasingly expose developer-facing integration surfaces. Those surfaces have quality risks that are more specific than general SaaS UI quality:

- long-lived API secrets;
- public API compatibility;
- rate limits and quota UX;
- webhook delivery reliability;
- idempotency for transactional requests;
- auditability of developer actions;
- tenant isolation for machine-to-machine access;
- docs-as-product and time-to-first-successful-call.

The core rubric already covers SaaS tenancy, security, documentation, and UX. This profile adds a focused evidence track for products that claim to be API-ready.

## Profile badge

```text
Developer Platform Profile: API-ready
```

Only claim the badge when all profile Must criteria pass and all applicable L2 gates have evidence in `docs/QUALITY.md`.

## Activation rule

Use this profile when a product exposes a public or customer-facing API, webhook system, developer console, integration API, or API keys.

If the product is a UI-only SaaS with no customer-facing API, mark this profile as `N/A`. Do not penalize the core score.

## Criteria summary

| ID | Criterion | Level | Maturity | Applies to |
|----|-----------|-------|----------|------------|
| **DP1** | API key lifecycle and storage safety | Must | L1 | Products with API keys |
| **DP2** | Public API contract baseline | Must | L1 | Public or customer-facing APIs |
| **DP3** | Developer console UX and docs-as-product | Should | L2 | Developer consoles and API docs |
| **DP4** | Rate limits and quota visibility | Must | L2 | Public APIs and usage-limited plans |
| **DP5** | Webhook infrastructure | Should | L2 | Products emitting customer webhooks |
| **DP6** | Developer audit log | Should | L2 | API keys, webhooks, billing, security settings |
| **DP7** | Idempotency for transactional requests | Could | L3 | Create/update/payment/async-job APIs |
| **DP8** | Tenant isolation for API access | Must | L2 | Multi-tenant APIs |

## DP1 — API key lifecycle and storage safety

**Level:** Must  
**Maturity:** L1  
**Applies to:** products with customer-facing API keys.

### Requirement

API keys must be treated as long-lived machine secrets.

Minimum evidence:

- keys are generated with high entropy;
- raw key value is shown only once;
- stored representation is one-way hashed or otherwise non-recoverable;
- UI displays only masked keys;
- keys can be revoked;
- key creation/revocation is permission-gated;
- key lifecycle events are auditable or ready for audit integration.

Recommended evidence:

- key prefixes such as `sk_live_` / `sk_test_` or equivalent environment markers;
- scopes;
- rotation flow;
- last-used timestamp;
- per-key usage.

### Verification

- Database schema review: no plaintext customer API keys.
- UI review: one-time reveal and masked display.
- Security test: revoked key cannot authenticate.
- Code review: constant-time comparison or equivalent safe verification path.

### Ports note

Feature components should call an `ApiKeyPort` / backend endpoint. They must not implement cryptographic verification or direct key-table access.

## DP2 — Public API contract baseline

**Level:** Must  
**Maturity:** L1  
**Applies to:** public or customer-facing APIs.

### Requirement

The public API must provide a stable integration contract.

Minimum evidence:

- versioned API path or versioned media type;
- bearer API key authentication or documented alternative;
- standard error envelope;
- request ID on responses;
- OpenAPI or equivalent machine-readable contract;
- pagination guidance for list endpoints.

Recommended evidence:

- RFC 7807 Problem Details or equivalent error schema;
- idempotency guidance for transactional endpoints;
- rate-limit headers;
- SDK or typed examples generated from the API contract.

### Verification

- OpenAPI lint in CI or documented manual check.
- Contract tests for representative success and error responses.
- API docs include authentication, errors, pagination, and rate limits.

### Ports note

HTTP controllers or Edge Functions are driving adapters. Business logic should live behind application services or ports, not inside route handlers.

## DP3 — Developer console UX and docs-as-product

**Level:** Should  
**Maturity:** L2  
**Applies to:** products with developer console or public API docs.

### Requirement

Developer onboarding should reduce time-to-first-successful-call.

Expected evidence:

- API key empty state with create CTA;
- quickstart with copyable curl example;
- TypeScript and Python snippets where appropriate;
- docs links inside the console;
- safe playground or clearly labeled test mode;
- useful empty/loading/error states;
- pricing, usage, and policy links where relevant.

### Verification

- UX review of first-run path.
- E2E or smoke test for key creation -> copy snippet -> successful API call.
- Docs review for runnable examples.

### Ports note

Console components should use ports/facades for key, usage, billing, and docs data. They should not import vendor SDKs directly.

## DP4 — Rate limits and quota visibility

**Level:** Must  
**Maturity:** L2  
**Applies to:** public APIs and usage-limited plans.

### Requirement

The product must protect API infrastructure and expose limits clearly to developers.

Minimum evidence:

- rate limits are enforced server-side;
- `429` responses use a clear error shape;
- quota or usage status is visible in the console where plans are usage-limited;
- limits are scoped by tenant and/or API key;
- limit implementation works across multiple server instances.

Recommended evidence:

- standard rate-limit headers;
- usage warnings at 80% and 95%;
- documented quota policy;
- tests for concurrent requests.

### Verification

- Integration or load test for rate limit behavior.
- UI review for quota/usage states.
- Architecture review: no in-memory-only counters for horizontally scaled APIs unless explicitly single-instance.

### Ports note

Quota configuration should come from a port or backend policy service, not hard-coded in Angular components.

## DP5 — Webhook infrastructure

**Level:** Should  
**Maturity:** L2  
**Applies to:** products emitting customer-facing webhooks.

### Requirement

Webhook delivery must be secure, inspectable, and retryable.

Expected evidence:

- endpoint management UI or API;
- signing secrets;
- signature verification docs;
- event catalog;
- delivery log;
- retry policy;
- manual retry;
- test event.

### Verification

- Integration test signs a payload over the raw body.
- Delivery log shows status code and attempt history.
- Retry behavior is tested for failed endpoints.

### Ports note

Webhook dispatch should be an outbound port backed by a queue or delivery adapter. API request handling should not block on third-party webhook delivery.

## DP6 — Developer audit log

**Level:** Should  
**Maturity:** L2  
**Applies to:** API keys, webhooks, billing, security settings, exports.

### Requirement

Developer-platform configuration changes should be auditable.

Expected events:

- API key created, rotated, revoked;
- webhook endpoint created, updated, disabled;
- signing secret rotated;
- billing plan or quota changed;
- security setting changed;
- export/deletion requested.

Minimum event shape:

- actor;
- actor type (`user`, `api_key`, `system`);
- action;
- target;
- timestamp;
- organization/workspace;
- request ID or trace ID when available.

### Verification

- Schema or event store review.
- Tests that critical developer actions emit audit events.
- UI or export path for audit evidence where applicable.

### Ports note

Audit recording should be centralized behind an `AuditLogPort` or equivalent service. Avoid ad hoc logs inside UI components.

## DP7 — Idempotency for transactional requests

**Level:** Could  
**Maturity:** L3  
**Applies to:** create/update/payment/async-job APIs where duplicate requests can cause side effects.

### Requirement

Transactional endpoints should support idempotency keys or equivalent deduplication.

Expected behavior:

- same idempotency key + same payload returns the original result;
- same idempotency key + different payload returns a deterministic validation error;
- concurrent duplicate requests result in one side effect;
- stored responses expire according to documented policy.

### Verification

- Contract test for duplicate requests.
- Concurrency test for duplicate create operations.
- Docs for idempotency key semantics and retention.

### Ports note

Idempotency is an inbound adapter concern. It should protect application services from duplicate side effects without leaking cache implementation details into domain logic.

## DP8 — Tenant isolation for API access

**Level:** Must  
**Maturity:** L2  
**Applies to:** multi-tenant APIs.

### Requirement

Machine-to-machine API access must preserve the same tenant isolation guarantees as user-facing access.

Minimum evidence:

- API keys are scoped to an organization/workspace;
- backend authorization validates key ownership and scope;
- database access is protected by RLS, scoped queries, or equivalent;
- privileged service-role credentials are never exposed to client bundles;
- tests attempt cross-tenant API access.

Supabase projects should explicitly document grants for tables exposed through the Data API and use `security_invoker = true` for views where applicable.

### Verification

- RLS or backend authorization tests.
- Client bundle scan or config review for service-role keys.
- Migration review for explicit grants and RLS policies.
- Cross-tenant negative tests.

### Ports note

Angular UI should not talk directly to privileged database APIs. Tenant context must be enforced in backend adapters and database policies, not only in the UI.

## Profile gate guidance

### API-ready badge

Required:

- DP1 Pass
- DP2 Pass
- DP4 Pass
- DP8 Pass for multi-tenant APIs

Required when webhooks are offered:

- DP5 Pass

Recommended for L2:

- DP3 Pass
- DP6 Partial/Pass

L3 expectation:

- DP7 Pass for transactional endpoints.
- DP6 Pass with exportable audit evidence.

## What not to include

- Do not require public APIs for every SaaS product.
- Do not require SDK generation for L1.
- Do not require idempotency for read-only endpoints.
- Do not mix AI token/credit usage into generic API quota criteria.
- Do not require a specific API framework, API gateway, Redis provider, or webhook vendor.
- Do not treat UI route guards as API authorization.

## Relationship to existing core criteria

| Existing criterion | Relationship |
|--------------------|--------------|
| `SaaS9` API keys | Becomes superseded by DP1 when this profile is active. Keep `SaaS9` for non-profile historical compatibility until a major release. |
| `SaaS10` Usage metering UX | DP4 adds developer-platform quota visibility; keep generic SaaS usage in `SaaS10`. |
| `SaaS8` Admin audit log | DP6 specializes audit events for developer-platform actions. |
| `D9` README credibility | DP3 covers docs-as-product for API developers. |
| `S1`–`S11` Security | DP1, DP4, DP8 add API-specific security evidence. |

## Related docs

- [Quality Profiles](./README.md)
- [SaaS domain rubric](../rubric/09-saas-domain.md)
- [Security rubric](../rubric/05-security.md)
- [Documentation & OSS rubric](../rubric/08-documentation-oss.md)
- [AI-Native profile](./ai-native.md)

