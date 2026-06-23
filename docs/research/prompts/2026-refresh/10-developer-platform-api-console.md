# Gemini Deep Research — Developer Platform / API Console Quality Rubric

Copy everything below the line into Gemini Deep Research.

---

You are a senior B2B SaaS platform architect and software quality researcher.

Today is June 23, 2026.

Research task:
Design a new Quality Framework rubric domain for **Developer Platform / API Console quality** in Angular B2B SaaS and API-first SaaS starters.

Context:
`oequ/quality-framework` is an open standard for Angular B2B SaaS frontend quality.

Current framework:
- Version: v1.4.0.
- Targets Angular 21+, Nx, ports/adapters, design systems, multi-tenant workspaces, billing, members, RBAC.
- Uses stable criterion IDs, Must/Should/Could levels, L1/L2/L3 maturity, and evidence-based self-assessment.

Existing rubric domains:
1. Architecture & boundaries
2. Angular platform
3. TypeScript & code quality
4. Testing & CI
5. Security & privacy
6. Performance & accessibility
7. UX & design system
8. Documentation & OSS hygiene
9. SaaS domain

Strategic reason for this research:
Modern OSS SaaS starters increasingly need API-first developer-platform primitives:
- API keys,
- public API baseline,
- OpenAPI docs,
- usage events,
- rate limits,
- webhooks,
- audit logs,
- developer console,
- docs-as-product,
- onboarding snippets.

The maintainers are considering adding a new domain:

```text
docs/rubric/10-developer-platform.md
Criterion IDs: DP1–DP?
```

Example product layering (common among maintained SaaS starters):

```text
OSS SaaS Starter:
  auth, orgs, billing, API keys, developer console, public API baseline,
  generic usage events, rate limits, webhooks, audit logs, docs, extension points

AI-native SaaS extension:
  AI credits, tokens, models, providers, AI run metrics, orchestration usage,
  AI cost controls, AI observability
```

The new domain must distinguish:
- generic OSS developer-platform quality;
- AI-specific console extensions that should not be required for generic OSS.

Reference market signal:
Mature API-first SaaS products (including public AI API providers) expose developer consoles with patterns such as:
- Overview,
- API Keys,
- Billing,
- Settings,
- Docs,
- Models,
- Pricing,
- Policies,
- token/orchestration usage.

Research objectives:
1. Determine whether Developer Platform / API Console should become a new core rubric domain, an optional profile, or part of existing SaaS/Documentation/Security domains.
2. Propose concrete rubric criteria with stable IDs `DP1`, `DP2`, etc.
3. For each criterion, specify:
   - ID,
   - title,
   - level: Must / Should / Could,
   - rationale,
   - verification method,
   - example evidence,
   - ports/adapters note,
   - whether it is L1, L2, or L3 relevant.
4. Recommend scoring weight if this becomes a core domain.
5. Recommend whether this should affect L2 gates.
6. Avoid checklist washing: every criterion should have concrete evidence or automation.

Topics to research:

A. API key quality
- scoped keys,
- hashed storage,
- masked display,
- one-time reveal,
- revoke,
- rotate,
- last-used timestamps,
- per-key usage,
- org admin permissions,
- audit events for create/revoke/rotate.

B. Public API baseline
- `/v1` versioning,
- Bearer API key auth,
- standard error format,
- request IDs,
- idempotency keys,
- pagination,
- rate-limit headers,
- OpenAPI spec,
- example SDK snippets.

C. Developer console UX
- overview dashboard,
- first-run onboarding,
- empty states,
- copy-paste curl / TypeScript / Python snippets,
- docs-as-product,
- API playground safety,
- settings,
- pricing and policy links.

D. Generic usage and quotas
- usage events,
- usage by key,
- usage vs plan quota,
- 80%/95% warnings,
- rate-limit visibility,
- clear `429` UX,
- distinction from AI-specific tokens/credits.

E. Webhooks
- endpoint management,
- signing secrets,
- event catalog,
- delivery log,
- retries,
- manual retry,
- test event,
- idempotency guidance.

F. Audit log
- API key lifecycle,
- billing plan changed,
- webhook endpoint changed,
- security setting changed,
- export/deletion initiated,
- actor + timestamp + target.

G. Security and tenancy
- org-scoped API keys,
- tenant isolation,
- permission-gated developer actions,
- no SDK/vendor leakage in Angular components,
- backend/RLS authoritative,
- explicit grants for public API tables in Supabase.

Specific questions:
1. Which of these are required for a credible OSS starter (Must)?
2. Which are production-grade expectations (Should)?
3. Which are enterprise differentiators (Could)?
4. Should API keys remain `SaaS9 Could`, or become Developer Platform Must?
5. Should webhooks and audit logs become part of this domain or stay in SaaS/Security?
6. How should the domain handle products without public APIs?
7. Should there be an optional badge/profile:

```text
Developer Platform Profile: API-ready
```

8. What evidence should `docs/QUALITY.md` require for each criterion?

Output format:
1. Executive recommendation.
2. Proposed domain placement: core domain vs optional profile.
3. Proposed rubric table for `10-developer-platform.md`.
4. Suggested updates to existing criteria (`SaaS9`, `SaaS10`, `D9`, `D10`, security criteria).
5. Suggested L2/L3 gate changes.
6. Scoring impact and migration notes from v1.4.
7. Example self-assessment evidence snippets.
8. Risks and what not to include.
9. Sources with links.

Important:
- Do not simply add every possible platform feature.
- Keep the rubric narrow enough to be adopted.
- Distinguish generic SaaS API quality from AI-specific API quality.
- Prefer verifiable criteria over broad advice.
- Preserve stable IDs and migration discipline.

