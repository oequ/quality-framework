# 2026 Refresh Synthesis / Versioning Summary

**Status:** reviewed synthesis  
**Date:** 2026-06-23  
**Prompt:** [2026-refresh/99-synthesis-versioning-plan.md](./prompts/2026-refresh/99-synthesis-versioning-plan.md)  
**Inputs:** [10 AI-native](./10-ai-native-summary.md), [11 Developer Platform](./11-developer-platform-summary.md), [12 Security / Platform Refresh](./12-security-platform-refresh-summary.md)  
**Rubric impact:** v1.5 optional profiles + v2.0 RFC track

## Executive summary

The synthesis supports a two-track evolution plan:

1. **v1.5** should remain backward-compatible. It may introduce optional profiles, profile badges, documentation clarifications, and RFCs, but it should not reweight the base 0-1000 score or rename stable core criteria.
2. **v2.0** should be the track for breaking changes: score reweighting, core-domain promotion, stricter platform baselines, renamed maturity labels, or mandatory stack-specific security gates.

This keeps the core framework useful for ordinary Angular B2B SaaS starters while making API-first and AI-native products measurable through opt-in profiles.

## Accepted direction

| Topic | Reviewed decision |
|-------|-------------------|
| Release strategy | Ship v1.5 as additive profiles + guidance; keep breaking changes in RFCs for v2.0. |
| Core scoring | Preserve the base 0-1000 score in v1.x. Optional profiles do not alter core score. |
| Stable IDs | Preserve current core IDs in v1.x. Do not rename `A*`, `NG*`, `T*`, `S*`, `D*`, or `SaaS*`. |
| Developer Platform | Keep `Developer Platform Profile: API-ready` as an optional profile for v1.5. Treat core Domain 10 as a possible v2.0 candidate. |
| AI-native SaaS | Keep AI-native criteria as optional profiles, not a core domain required for every SaaS starter. |
| AI IDs | Preserve the current draft `AI1`-`AI12` mapping. Do not collapse it to `AI1`-`AI10`. |
| AI compliance | Keep `AI Compliance-ready` in v1.5 as a draft/profile track, with conservative wording. Do not make advanced C2PA/watermarking mandatory for all AI products. |
| Enterprise profile | Reserve `ENT*` as a possible future namespace only. Do not ship an Enterprise profile in v1.5 without separate research. |
| L3 naming | Keep `L3 Exemplary` in v1.5. Consider `L3 Enterprise-ready` only through a v2.0 RFC because it changes public badge language. |
| Security/platform refresh | Use [RFC-007](../rfc/RFC-007-platform-security-refresh-2026.md) for breaking or stack-specific changes. |

## Corrections to raw synthesis

The raw synthesis was useful but too assertive in several places. These recommendations are intentionally adjusted:

| Raw synthesis claim | Reviewed handling |
|---------------------|------------------|
| Promote `DP*` into a stable core Domain 10 soon | Keep as optional v1.5 profile; evaluate core promotion in v2.0 after adoption evidence. |
| Use `AI1`-`AI10` | Keep current `AI1`-`AI12`; the extra criteria cover sandboxing and regression tests. |
| Defer all `ai-compliance-ready` work to v2.0 | Keep draft v1.5 profile for disclosure/origin metadata; defer stricter provenance gates if needed. |
| Add `ENT*` profile to templates now | Reserve namespace only; no template section until dedicated enterprise/audit research exists. |
| Rename L3 to Enterprise-ready now | Treat as v2.0 naming/maturity RFC, not a v1.5 change. |
| Mandate Angular 22, Vitest, and zoneless as future accepted v2.0 gates | Keep as RFC candidates, not already-approved v2.0 requirements. |
| Treat Supabase public schema exposure as blanket default CRUD exposure | Use precise, stack-specific wording: require intentional grants, RLS evidence, and `security_invoker` views where exposed to client roles. |
| Use `docs/rubrics/` structure | Keep current repository path `docs/rubric/`. |

## v1.5 release recommendation

v1.5 should include:

- Optional profile model in [profiles/README.md](../profiles/README.md).
- `Developer Platform Profile: API-ready` with `DP1`-`DP8`.
- AI-native profile family with `AI1`-`AI12`.
- Cost-safe, Agent-ready, and Compliance-ready profile docs as draft v1.5 candidates.
- Self-assessment template support for optional profiles.
- Non-breaking notes for supply-chain hardening, MCP/STDIO safety, generated-code boundary drift, Supabase grants/views, Angular 22, Vitest, and zoneless modernization.
- RFC-007 as the home for breaking security/platform changes.

v1.5 should not include:

- Base score reweighting.
- Renamed core criteria.
- A required Developer Platform core domain.
- A required AI-native core domain.
- A real `ENT*` profile.
- Mandatory Angular 22 / Vitest / OnPush / zoneless requirements for all adopters.

## v2.0 RFC candidates

These are worth exploring for v2.0, but are not accepted as final requirements yet:

- Promote Developer Platform from optional profile to core Domain 10.
- Reweight security/supply-chain criteria.
- Rename `L3 Exemplary` to `L3 Enterprise-ready`.
- Add formal security criteria for MCP/STDIO shell-sink containment.
- Make Supabase/PostgREST grants and `security_invoker` formal stack-specific gates.
- Add explicit generated-code boundary drift criteria.
- Strengthen OpenSSF Scorecard thresholds.
- Make Vitest mandatory for new Angular apps while preserving a migration path for existing projects.
- Revisit zoneless requirements after more Angular 22 adoption evidence.

## Draft file review

| File | Reviewed status |
|------|-----------------|
| `docs/profiles/developer-platform.md` | Keep as draft v1.5 profile. Verify `DP7` idempotency level and `DP8` tenant-isolation wording before release. |
| `docs/profiles/ai-native.md` | Keep as draft v1.5 profile family using `AI1`-`AI12`. |
| `docs/profiles/ai-cost-safe.md` | Good v1.5 profile candidate. Ensure reserve/finalize/refund evidence remains implementation-agnostic. |
| `docs/profiles/ai-agent-ready.md` | Good v1.5 profile candidate. Keep MCP/security wording capability-based, not tied to one protocol implementation. |
| `docs/profiles/ai-compliance-ready.md` | Keep as draft. Separate basic disclosure/origin metadata from advanced provenance/watermarking expectations. |
| `docs/rfc/RFC-007-platform-security-refresh-2026.md` | Keep as RFC. It should guide v1.5 clarifications and v2.0 decisions, not act as a stable rubric today. |
| `templates/SELF_ASSESSMENT.md.template` | Keep optional profile sections additive and clearly outside base score. |
| `templates/AGENTS.md.template` | Useful, but should remain generic: capabilities, approvals, secrets, filesystem/network/shell boundaries. |

## Source quality notes

Use as stronger evidence:

- Angular official docs for zoneless, Signal Forms, and Vitest migration.
- Supabase official docs for API security, RLS, and `security_invoker` advisor guidance.
- OWASP ASVS and OWASP cheat sheets for application security expectations.
- OpenSSF Scorecard / Best Practices Badge for OSS trust.
- Reputable security research for MCP/STDIO and shell-sink risks.

Use only as weak context, not normative evidence:

- Reddit threads.
- Generic SaaS blog posts.
- Vendor marketing pages without technical controls.
- Unverified lists of MCP servers or tool catalogs.

## Backlog

1. **Finalize v1.5 profile wording**
   - Scope: `docs/profiles/*`.
   - Acceptance: criteria are capability-based, vendor-neutral, evidence-based, and consistent with `DP1`-`DP8` and `AI1`-`AI12`.

2. **Add synthesis links**
   - Scope: `docs/research/README.md`, `docs/evolution.md`, `CHANGELOG.md`.
   - Acceptance: synthesis is discoverable as the reviewed decision point for the 2026 refresh.

3. **Review Supabase wording**
   - Scope: RFC-007, security guidance, profile evidence examples.
   - Acceptance: wording requires intentional grants/RLS/view security without making inaccurate blanket claims about default CRUD exposure.

4. **Keep Enterprise profile out of v1.5**
   - Scope: profiles README and self-assessment template.
   - Acceptance: `ENT*` appears only as planned/future if mentioned at all.

5. **Prepare v2.0 issue list**
   - Scope: RFC index and GitHub issues.
   - Acceptance: each v2.0 candidate has scope, migration impact, and evidence needed before adoption.

## Open questions

1. Should `DP7` idempotency become L2/Should for APIs that create billable work?
2. Should `AI6` disclosure apply to text-only internal assistants or only externally visible generated content?
3. Should `AI12` prompt/model regression testing remain in the AI profile or move into Testing & CI in v2.0?
4. What adoption evidence is required before promoting Developer Platform to a core domain?
5. Should L3 be renamed to Enterprise-ready in v2.0, or should Enterprise readiness remain an optional profile?

