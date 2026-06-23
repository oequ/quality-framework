# RFC-007 — 2026 Platform and Supply-Chain Security Refresh

**Status:** Proposed  
**Source:** [Security / Platform Refresh 2026 Summary](../research/12-security-platform-refresh-summary.md)  
**Breaking:** likely, if adopted as core gates  
**Target:** v2.0 or staged v1.5 clarifications + v2.0 gates

## Problem

By mid-2026, Angular/Nx/Supabase B2B SaaS starters face new platform and supply-chain risks:

- compromised developer tooling and marketplace extension updates;
- MCP/STDIO local command execution risks;
- generated-code architectural drift;
- Supabase explicit grants for exposed schemas;
- RLS bypass risks through default security-definer views;
- Angular 22 / Vitest / zoneless migration pressure;
- stronger OSS trust expectations around Scorecard, CODEOWNERS, SECURITY.md, SAST, and dependency controls.

The current v1.4 rubric covers many foundations, but it does not explicitly address these new risks.

## Goals

- Preserve stable criterion IDs unless a major release is approved.
- Add security guidance that can be adopted in v1.5 without breaking existing self-assessments.
- Identify true v2.0 candidates separately.
- Avoid reactive bans on specific IDE extensions.
- Prefer automated evidence over policy-only checklists.

## Proposed changes

### v1.5-compatible clarifications

These can be added as documentation, examples, or evidence notes:

- Supabase-backed projects should declare explicit `GRANT` statements for exposed tables.
- Supabase views exposed to client roles should use `WITH (security_invoker = true)` where supported.
- `AGENTS.md` should document local agent/tool safety boundaries and secret-handling rules.
- MCP/STDIO tooling should use static allowlists and avoid dynamic shell parameters.
- Supply-chain guidance should include dependency lifecycle controls such as `--ignore-scripts` where feasible.
- SAST examples should include shell-sink and subprocess injection checks.

### v2.0 candidates

These may change gates, criterion IDs, or scoring:

| Candidate | Rationale | Possible destination |
|-----------|-----------|----------------------|
| MCP/STDIO shell-sink containment criterion | Prevent prompt/user input from flowing into local command execution | Security |
| Supabase explicit grants criterion | Make exposed-schema access deterministic and secure-by-default | Security or SaaS |
| Security-invoker view criterion | Prevent RLS bypass through views | Security |
| Generated-code boundary drift criterion | Prevent AI agents from bypassing ports/adapters | Architecture |
| Stronger supply-chain gate | Reflect post-compromise trust requirements | Testing/CI or Documentation/OSS |
| Scorecard threshold review | Align L2/L3 with buyer expectations | Documentation/OSS |
| Vitest migration policy | Align with Angular platform direction | Testing/CI |
| Angular 22 / OnPush / zoneless review | Modernize platform baseline without excessive churn | Angular |

## Open questions

1. Should Supabase-specific database criteria be core, optional stack profile, or implementation guidance?
2. Should MCP/STDIO safety be one Security criterion, a Documentation criterion, or both?
3. Should `--ignore-scripts` be required for L2 or only recommended for high-security repos?
4. Should Scorecard L2 threshold remain ≥ 6.5 or move to ≥ 7.0?
5. Should Angular 22 be an L3 expectation before becoming an L2 gate?
6. Should Vitest be required only for newly generated apps?

## Non-goals

- Do not require Supabase-specific controls for non-Supabase stacks.
- Do not ban all local AI/MCP tooling.
- Do not force Angular 22 as a v1.5 L2 requirement.
- Do not rename stable IDs in a minor release.
- Do not turn developer workstation policy into unverifiable prose.

## Evidence examples

- SQL migration checks for missing `GRANT` statements.
- Static scan for `CREATE VIEW public.*` without `security_invoker = true`.
- Semgrep/CodeQL rules for subprocess shell sinks.
- `AGENTS.md` with secret-handling and local tool policy.
- OpenSSF Scorecard workflow and published result.
- CI job that verifies Nx module-boundary rules on every PR.

## Migration considerations

- Existing projects may fail immediately if strict Supabase grants are enforced without migration updates.
- Legacy Angular/Karma projects need a grace path before Vitest becomes mandatory.
- Third-party libraries may need verification before zoneless/OnPush hard gates are strengthened.
- Local agent tooling policies should balance safety and developer velocity to avoid shadow workflows.

