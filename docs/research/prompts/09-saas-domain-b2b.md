# Deep Research — SaaS domain B2B (SaaS1–SaaS7)

Weight: 15% of total score.

---

## Role

You are a B2B SaaS product architect specializing in **multi-tenant control planes**, **billing integrations**, and **RBAC** for workspace-based applications.

## Context

Quality Framework v1.0 SaaS domain criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| SaaS1 | Multi-tenant context (org/workspace switcher) | Must |
| SaaS2 | Tenant scope in navigation (route params or documented active-org model) | Should |
| SaaS3 | Billing via port (swap Stripe/LemonSqueezy/custom) | Must |
| SaaS4 | Seat limit UX (block invite / upgrade CTA) | Should |
| SaaS5 | Onboarding flow (no broken dashboard for new users) | Should |
| SaaS6 | Members lifecycle (invite, remove, change role) | Must |
| SaaS7 | RBAC in UI (admin actions hidden/disabled by role) | Must |

Example reference implementation: workspace switcher, active-org context (not URL `:orgId`), BillingPort with mock + Stripe, seat limits, onboarding/activation, members UI, admin guards, Supabase RLS.

## Research questions

### 1. 2026 B2B SaaS control-plane baseline

What features define a **credible B2B SaaS admin shell** in 2026?

- Workspace vs organization vs team terminology
- Minimum modules: auth, members, billing, settings, API keys, audit log?
- What do buyers consider "incomplete" vs "MVP starter"?

Benchmark against: Stripe Dashboard patterns, Clerk orgs, Auth0 organizations, Supabase multi-tenant guides, WorkOS.

### 2. Multi-tenancy models (SaaS1, SaaS2)

Compare tenant scoping strategies:

| Model | Pros | Cons | 2026 adoption |
|-------|------|------|---------------|
| URL path `/org/:id/...` | | | |
| Subdomain `tenant.app.com` | | | |
| Session active-org (no URL segment) | | | |
| JWT claims only | | | |

Which should Quality Framework recommend as **Should** vs document-as-choice?

Deep link sharing, back-button behavior, stale tenant data on switch — best practices.

### 3. Billing abstraction (SaaS3, SaaS4)

- Stripe Billing vs Stripe Checkout-only vs Paddle/Lemon Squeezy — starter expectations
- Per-seat vs usage-based vs flat — UI requirements for each
- Self-serve upgrade/downgrade flows — table-stakes for PLG B2B?
- Billing port pattern — case studies from production codebases
- Failed payment / past_due UX — required for L2?

### 4. Members and invitations (SaaS6)

2026 standards for team management UI:

- Email invite vs magic link vs SSO JIT provisioning
- Role models: owner/admin/member vs custom roles
- Seat enforcement at invite time vs accept time
- SCIM — too enterprise for starter or emerging Should?

### 5. RBAC and authorization UX (SaaS7)

- UI gating vs backend enforcement — messaging standards
- Permission matrices for settings routes
- Owner-only destructive actions
- Audit log correlation — frontend responsibility?

### 6. Onboarding and activation (SaaS5)

PLG onboarding patterns 2026:

- Empty workspace → create org → invite team → connect integration
- Activation metrics (aha moment) in starter templates
- Checklist UIs vs progressive disclosure

### 7. Backend coupling expectations

For starters advertising **Supabase** or **Firebase**:

- Minimum RLS policies buyers expect documented
- Edge Functions for billing webhooks — in-scope for starter?
- Mock adapter fidelity — what must match production contracts?

### 8. Buyer persona requirements

| Persona | Must-have SaaS modules | Nice-to-have | Will not buy without |
|---------|------------------------|--------------|----------------------|

Personas: indie SaaS, Series A startup, enterprise pilot, dev agency.

### 9. L1 / L2 / L3 mapping

| ID | 2026 L1 starter | 2026 L2 production | 2026 L3 exemplary |
|----|-----------------|--------------------|--------------------|

Should SaaS5 onboarding move from Should → Must?

### 10. Missing domain criteria for v1.1

Propose new criteria:

- Audit log UI
- API keys / service accounts
- Usage metering dashboard
- SSO/SAML (enterprise)
- Data export / GDPR delete

With suggested weights and levels.

## Output format

1. Executive summary — SaaS domain bar for Angular B2B starter (2026)
2. Multi-tenancy recommendation for rubric (with sources)
3. Billing/seats feature checklist (mock vs Stripe vs enterprise)
4. Members/RBAC minimum viable flows
5. L1/L2/L3 mapping (SaaS1–SaaS7)
6. Proposed SaaS8–SaaS12 criteria for v1.1
7. Competitive feature matrix (5 starters/boilerplates)
8. Bibliography (Stripe docs, Supabase multi-tenant, WorkOS, OWASP multi-tenancy cheatsheet)

## Source priorities

- Stripe SaaS integration guides (current)
- Supabase RLS multi-tenant documentation
- WorkOS / Clerk multi-tenant architecture posts
- Martin Fowler / InfoQ multi-tenancy patterns
- G2/Capterra feature comparisons for B2B admin tools
- Y Combinator SaaS metrics resources (for onboarding/activation)

## Constraints

- **Control-plane UI** focus — not full product vertical (CRM, ERP).
- Honest about **mock billing** vs production Stripe complexity.
- Note regional billing/tax UI (Stripe Tax) as out-of-scope for starter unless cited as L3.
