# Security / Platform Refresh 2026 Summary

**Status:** reviewed summary  
**Date:** 2026-06-23  
**Prompt:** [2026-refresh/12-security-platform-refresh-2026.md](./prompts/2026-refresh/12-security-platform-refresh-2026.md)  
**Rubric impact:** existing-domain updates and v2.0 RFC candidates

## Executive summary

The research confirms that mid-2026 quality expectations are shifting from written policy toward automated, gate-driven verification. AI-assisted development, local agent tooling, and secure-by-default platform changes create new risks for Angular/Nx/Supabase B2B SaaS starters:

- compromised developer tooling and marketplace extensions;
- MCP/STDIO command execution risks;
- architectural drift introduced by generated code;
- Supabase explicit grants and RLS/view security;
- Angular 22 / Vitest / zoneless migration pressure;
- stronger OSS trust expectations such as Scorecard, CODEOWNERS, SECURITY.md, and supply-chain checks.

The raw report recommends a major v2.0 release. The reviewed decision is more conservative:

- capture breaking changes as RFC candidates;
- add v1.5-compatible documentation, evidence, and optional checks where possible;
- do not rename stable criterion IDs or force Angular 22/Vitest/OnPush as L1 gates without synthesis.

## Accepted direction

| Finding | Decision |
|---------|----------|
| Supabase exposed-schema tables require explicit grants | Accepted as a security/platform update candidate |
| Supabase views exposed to client roles should use `security_invoker = true` | Accepted as a security update candidate |
| MCP/STDIO and local agent tooling need explicit safety policy | Accepted as Security + Documentation update candidate |
| OpenSSF Scorecard should remain important for L2/L3 trust | Already partly covered; consider strengthening evidence |
| Angular 22, Vitest, and zoneless are important modernization signals | Accepted as migration pressure, not immediate L1 break |
| Do not reactively ban one compromised extension | Accepted; prefer systematic supply-chain controls |

## Changes from raw research

The raw report used proposed IDs such as `ARCH-02`, `ANG-01`, `TEST-01`, and `SEC-01`. Those do not match the current stable ID scheme:

- Architecture criteria use `A1`–`A13`.
- Angular criteria use `NG1`–`NG13`.
- Testing criteria use `T1`–`T14`.
- Security criteria use `S1`–`S11`.
- Documentation criteria use `D1`–`D10`.
- SaaS criteria use `SaaS1`–`SaaS12`.

Reviewed handling:

- Preserve current IDs in v1.x.
- Treat ID renames or level changes as v2.0 RFC work.
- Add new candidate IDs only after synthesis.

The raw report also recommends Angular 22, OnPush, and Vitest as L1-level breaking gates. This is too aggressive for v1.5 because the current framework supports Angular 21+ and already treats zoneless as an L2 gate.

## Candidate updates by domain

### Architecture & boundaries

| Candidate | Reviewed handling |
|-----------|------------------|
| AI-generated code must pass boundary checks | Add as clarification to `A2` / possible new `A14` in v1.5 or v2.0 |
| MCP tooling boundaries monitored via lint/static rules | Consider as documentation/security profile evidence |
| Abstract-class ports remain important | Already covered by `A1` and should not change |

### Angular platform

| Candidate | Reviewed handling |
|-----------|------------------|
| Angular 22 required | Do not require for L2 yet; consider L3 recommendation |
| Zoneless remains L2 gate | Keep current `NG1` / `NG2` L2 gate |
| Vitest for new apps | Already `T2 Should`; possible L2 clarification |
| `resource()` / `httpResource()` | Already `NG5 Should`; clarify standard REST operations if needed |
| `ng mcp` | Mention only as sensitive optional local tooling, not requirement |

### Testing & CI

| Candidate | Reviewed handling |
|-----------|------------------|
| `--ignore-scripts` by default | Strong candidate for `T7` / `T12` clarification or new supply-chain criterion |
| Scorecard as L2 gate | Already L2 via `D3`; consider threshold review |
| SAST/Semgrep for shell sinks | Candidate update to `S11` or new security criterion |

### Security & privacy

| Candidate | Reviewed handling |
|-----------|------------------|
| Explicit Supabase grants | Strong candidate for Supabase-specific evidence note under security/SaaS, not universal unless using Supabase Data API |
| `security_invoker = true` for exposed views | Strong candidate for view/RLS security note |
| MCP/STDIO shell-sink containment | Strong candidate for new `S12` or v2.0 security criterion |
| Workspace Trust and static MCP allowlists | Candidate for Documentation + Security evidence |

### Documentation & OSS hygiene

| Candidate | Reviewed handling |
|-----------|------------------|
| AGENTS.md declares agent/tool safety boundaries | Extend `D1` guidance; possible profile evidence |
| CODEOWNERS / SECURITY.md / PR template | Already covered by `D4`, `D6`, `D7` |
| Scorecard ≥ 7 | Existing `D3` L2 threshold is ≥ 6.5; review in synthesis |

## v1.5-compatible changes

These can be added without breaking existing self-assessments:

- Add security guidance for Supabase explicit `GRANT` and `security_invoker = true`.
- Add MCP/STDIO and local agent tooling safety notes to `D1` / AGENTS template.
- Add shell-sink static analysis examples under `S11` or implementation docs.
- Add `--ignore-scripts` / dependency lifecycle controls as a supply-chain hardening recommendation.
- Add Angular 22 / Vitest / Signal Forms notes as migration guidance, not hard gates.

## v2.0 RFC candidates

These may change gates, scoring, or stable criteria and should go through RFC:

- New security criterion for MCP/STDIO shell-sink containment.
- Explicit Supabase grants and `security_invoker` as formal Must criteria for Supabase-backed products.
- Reweighting supply-chain security and Scorecard gates.
- Making Vitest mandatory for new apps while documenting migration path for legacy Karma/Jasmine apps.
- Reviewing whether L3 should become “Enterprise-ready”.
- Adding an explicit “generated code boundary drift” criterion.

## What should not change immediately

- Do not rename existing stable IDs in a minor release.
- Do not require Angular 22 for L2 yet.
- Do not make OnPush or Vitest L1-breaking requirements for all existing adopters.
- Do not ban all IDE extensions after a single compromised extension.
- Do not require MCP or `ng mcp`; treat it as optional sensitive tooling.
- Do not make Supabase-specific rules mandatory for non-Supabase stacks.

## Recommended next step

Use this report as input to:

- [RFC-007 — 2026 Platform and Supply-Chain Security Refresh](../rfc/RFC-007-platform-security-refresh-2026.md)
- the final synthesis/versioning research;
- targeted v1.5 doc clarifications after synthesis.

