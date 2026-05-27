# SaaS domain

B2B workspace apps: multi-tenancy, billing, members, RBAC. Business capabilities go through **ports**, not vendor SDKs in UI. See [research summary](../research/09-saas-domain-summary.md).

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **SaaS1** | **Multi-tenant context.** UI supports isolated organization/workspace context (switcher or equivalent). On switch: invalidate in-memory caches and cancel in-flight requests. | Must | Architecture review | No stale data from previous org. |
| **SaaS2** | **Tenant scope in navigation.** **L1:** active-org model allowed if deep-link rules documented. **L2:** route params (`/org/:id/...`) with guards validating membership. **L3:** subdomain/custom domain option. | Should | Router / docs | Pick one model; document shareable URLs. |
| **SaaS3** | **Billing via port.** Plans, checkout, portal, subscription state via `BillingPort` (mock + production adapters). | Must | Architecture review | No Stripe/SDK in feature components. |
| **SaaS4** | **Seat limit UX.** Block invite (or upgrade CTA) when seats exhausted; handle `past_due` billing states in UI. | Should | UX test | Adapter returns seat usage + subscription status. |
| **SaaS5** | **Onboarding flow.** Users without a workspace get guided creation/onboarding—not a blank dashboard. | Must | UX test | PLG activation baseline (v1.3). |
| **SaaS6** | **Members lifecycle.** Token-based invite (expiry), role changes, remove member via `OrgPort`; reserve seats at invite creation. | Must | UX + adapter review | Typed port errors (conflict, forbidden, seats). |
| **SaaS7** | **RBAC in UI.** Permission- or role-gated UI; backend/RLS authoritative (pairs with S9). | Must | UX test | Owner/Admin/Member/Viewer model documented. |
| **SaaS8** | **Admin audit log.** Record sensitive admin actions (role change, export, billing) with actor + timestamp. | Should | Adapter / DB review | L3: immutable exportable trail. |
| **SaaS9** | **API keys (optional).** Org admins create scoped, hashed API keys with masked display. | Could | Feature review | Enterprise integrations. |
| **SaaS10** | **Usage metering UX.** Show usage vs plan quota (seats, API calls, storage) where applicable. | Should | UX test | Progress/warnings at 80%/95%. |
| **SaaS11** | **Enterprise SSO.** SAML/OIDC for org-level login (Okta, Entra). | Could | Config review | L3 differentiator; L1 OAuth social OK. |
| **SaaS12** | **Data export & deletion.** Self-serve workspace export and account/org deletion path (GDPR/CCPA). **L1 Partial:** documented support process. **L2:** automated export + delete flows in UI. | Must | UX + backend review | Backend must actually purge data. |

[← Rubric index](./README.md)
