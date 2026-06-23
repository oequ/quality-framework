# Quality Profiles

Quality Profiles extend the core Quality Framework rubric without changing the base 0-1000 score.

The core rubric remains focused on Angular B2B SaaS quality:

```text
Architecture, Angular, TypeScript, Testing/CI, Security,
Performance/a11y, UX/design system, Documentation/OSS, SaaS domain.
```

Profiles are opt-in evidence tracks for specialized product shapes:

| Profile | Status | Audience |
|---------|--------|----------|
| [AI-Native](./ai-native.md) | Draft v1.5 candidate | SaaS products that charge for AI work or run agentic workflows |
| [Developer Platform / API-ready](./developer-platform.md) | Draft v1.5 candidate | API-first SaaS products with public APIs, developer consoles, webhooks, and usage metering |
| Enterprise / Audit-ready | Planned | Teams selling into procurement-heavy B2B or regulated accounts |

## Design principles

- **Profiles do not dilute the core.** A non-AI SaaS starter should not fail the core rubric because it lacks AI credits or generated-content provenance.
- **Profiles are evidence-based.** A badge requires linked implementation evidence in `docs/QUALITY.md`, not a checklist claim.
- **Profiles are additive.** They may define gates and badges, but they do not change the core 0-1000 score unless a future major version explicitly reweights the model.
- **Profiles avoid vendor lock-in.** Criteria may mention examples, but compliance is based on capabilities, not a specific provider.
- **Profiles preserve stable IDs.** New criteria use stable profile-specific IDs and should not be renamed without a major version.

## Suggested badge model

```text
Quality Framework: L1 Starter-ready
Quality Framework: L2 Production-ready
Quality Framework: L3 Exemplary

AI-Native Profile: Cost-safe
AI-Native Profile: Agent-ready
AI-Native Profile: Compliance-ready
Developer Platform Profile: API-ready
Enterprise Profile: Audit-ready
```

## How profiles relate to core maturity

| Core level | Profile meaning |
|------------|-----------------|
| L1 Starter-ready | The app has a credible Angular B2B SaaS foundation. Profiles are optional and usually incomplete. |
| L2 Production-ready | The app may claim a profile badge if all profile Must criteria pass with evidence. |
| L3 Exemplary | Profile Should/Could coverage is broad enough to demonstrate enterprise-grade operation. |

## Related docs

- [Maturity model](../maturity.md)
- [Scoring guide](../scoring.md)
- [Framework evolution](../evolution.md)
- [AI-Native profile](./ai-native.md)
- [Developer Platform profile](./developer-platform.md)

