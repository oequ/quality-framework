# SaaS domain

B2B workspace apps: multi-tenancy, billing, members, RBAC. Business capabilities go through **ports**, not vendor SDKs in UI.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **SaaS1** | **Multi-tenant context.** UI supports isolated organization/workspace context (switcher or equivalent). | Must | Architecture review | Clear tenant state on switch; no stale data from previous org. |
| **SaaS2** | **Tenant scope in navigation.** Org context is explicit: route params (`/org/:id/...`) **or** documented active-org model with deep-link rules. | Should | Router / docs | Pick one strategy; document shareable URLs. |
| **SaaS3** | **Billing via port.** Invoices, plans, seat meter, upgrade flow use `BillingPort` (or equivalent). | Must | Architecture review | Swap Stripe/LemonSqueezy/custom in adapter only. |
| **SaaS4** | **Seat limit UX.** UI blocks invite (or shows upgrade CTA) when seats exhausted per billing summary. | Should | UX test | Adapter returns seat usage; UI does not hardcode limits. |
| **SaaS5** | **Onboarding flow.** New users without a workspace get creation/onboarding—not a broken dashboard. | Should | UX test | `OrgPort` / auth claims drive empty state. |
| **SaaS6** | **Members lifecycle.** Invite, remove, change role (as applicable) via `OrgPort` with typed results. | Must | UX + adapter review | Mutations return port errors (conflict, forbidden, seats). |
| **SaaS7** | **RBAC in UI.** Admin-only actions hidden or disabled by role; not security enforcement alone. | Must | UX test | Document that backend/RLS is authoritative. |

[← Rubric index](./README.md)
