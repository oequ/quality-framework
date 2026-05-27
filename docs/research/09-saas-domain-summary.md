# Research summary — SaaS domain (May 2026)

Source: [A Technical Blueprint for Multi-Tenancy, Billing Abstractions, and Fine-Grained Authorization in 2026.txt](./A%20Technical%20Blueprint%20for%20Multi-Tenancy%2C%20Billing%20Abstractions%2C%20and%20Fine-Grained%20Authorization%20in%202026.txt)

## Executive summary

B2B control planes need **BillingPort**, **RLS-backed authZ**, token **invites with seat reservation**, and tenant switch **cache invalidation**. **URL path scoping** (`/org/:id`) is 2026 default for shareable links; **active-org session** is acceptable for L1 prototypes if documented. **Onboarding** is PLG-critical — promote to Must.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.3) |
|-------|----------------|----------------------|
| SaaS2 | `/org/:id` Should for L2; active-org OK for L1 with deep-link rules | Clarify SaaS2 tiers |
| SaaS5 | Onboarding Must — empty dashboard fails PLG | **SaaS5 → Must** |
| SaaS6 | Token invites; reserve seats at invite creation | Clarify SaaS6 |
| SaaS3 | IBillingPort; mock + Stripe adapters; past_due UX | Clarify SaaS3/SaaS4 |
| SaaS7 | UI RBAC + RLS; permission strings in JWT for coarse checks | Clarify SaaS7 |
| SaaS8–12 | Audit log, API keys, metering, SSO, export/delete | Add new IDs |

## L1 / L2 / L3 (research view)

| ID | L1 | L2 | L3 |
|----|----|----|-----|
| SaaS1 | In-memory org switcher | Invalidate caches on switch | Multi-region routing |
| SaaS2 | Active-org (documented) | Route `/org/:id` + guards | Subdomain tenancy |
| SaaS5 | Basic empty-state CTA | Guided onboarding checklist | Personalized PLG flows |
| SaaS6 | Admin adds email | Token invite + expiry | SCIM provisioning |
| SaaS12 | Support email for export/delete | Self-serve export + delete UX | Full purge + object storage |

## New criteria (v1.3)

| ID | Level | Summary |
|----|-------|---------|
| **SaaS8** | Should | Admin audit log (actor, IP, timestamp) |
| **SaaS9** | Could | Org-scoped API keys (hashed, masked) |
| **SaaS10** | Should | Usage/quota display vs plan limits |
| **SaaS11** | Could | Enterprise SSO (SAML/OIDC) — L3 path |
| **SaaS12** | Must | Data export + account/workspace deletion path (GDPR); L1 Partial = documented support process |

## Top actions for adopters

1. Implement `BillingPort` with mock + production adapter.
2. On tenant switch: abort pending HTTP, reset stores keyed by org id.
3. Block invite when seats exhausted; show upgrade CTA (SaaS4).
4. Document guards as UX; enforce RLS on backend (SaaS7, S9).
5. Add onboarding route for users without org (SaaS5).

[← Research index](./README.md)
