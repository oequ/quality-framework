# Gemini Deep Research — Security / Platform Refresh 2026

Copy everything below the line into Gemini Deep Research.

---

You are a senior application security researcher, Angular/Nx platform architect, and open-source software supply-chain reviewer.

Today is June 23, 2026.

Research task:
Update the existing Quality Framework rubric for 2026 platform changes and security threats affecting Angular/Nx/Supabase B2B SaaS starters and AI-assisted development workflows.

Context:
`oequ/quality-framework` is v1.4.0 and currently covers:
- architecture & boundaries,
- Angular platform,
- TypeScript/code quality,
- testing/CI,
- security/privacy,
- performance/a11y,
- UX/design system,
- documentation/OSS hygiene,
- SaaS domain.

This research should focus on **updates to existing domains**, not on creating the new Developer Platform or AI-native profiles. Those are handled in separate prompts.

Recent ecosystem signals:

1. Nx Console compromise:
   - A malicious Nx Console version v18.95.0 was published on May 18, 2026.
   - It attempted to steal Anthropic Claude Code tokens, npm tokens, AWS credentials, and SSH private keys.
   - CVE-2026-48027, critical severity.

2. MCP / agent tooling security:
   - MCP STDIO transport vulnerabilities in official Anthropic SDKs were disclosed in 2026.
   - Risks include arbitrary command execution through unsafe config, protocol pivoting, and lateral movement through compromised MCP servers.
   - MCP is moving toward stateless core, final spec expected around July 28, 2026.
   - Roots, Sampling, and Logging are deprecated in the new direction.

3. Supabase security change:
   - Since May 30, 2026, newly created Supabase public schema tables are not automatically exposed through Data API.
   - Client access requires explicit SQL `GRANT` statements for `anon`, `authenticated`, or `service_role`.
   - Views should use `security_invoker = true` to avoid bypassing RLS.

4. Angular / Nx platform:
   - Angular 22 released June 2026.
   - Signal Forms are GA.
   - Zoneless change detection is default for new projects.
   - Vitest replaces Karma as default test runner.
   - Angular CLI introduced `ng mcp`.
   - Dynamic loading patterns changed; old `NgModuleFactory` removed.

5. OSS trust:
   - Code generation makes shallow starters cheap.
   - Trust now depends on evidence: CI gates, OpenSSF Scorecard, CODEOWNERS, SECURITY.md, real boundary lint, SAST, dependency scanning.

Research objectives:
1. Identify which existing Quality Framework criteria should be updated.
2. Propose new criteria only if they clearly belong in existing domains.
3. Recommend which updates are patch/minor/major changes.
4. Recommend L1/L2/L3 gate changes.
5. Provide evidence and automation methods.
6. Avoid broad advice; produce rubric-ready changes.

Domains to evaluate:

A. Architecture & boundaries
- Nx depConstraints,
- ports/adapters,
- framework-free ports,
- abstract-class DI tokens vs Angular `InjectionToken`,
- route lazy loading,
- package boundaries,
- MCP tooling risks in monorepos,
- generated code boundary drift.

B. Angular platform
- Angular 22,
- Signal Forms,
- zoneless default,
- Vitest,
- `resource()` / `httpResource()`,
- standalone/lazy route patterns,
- deprecated `NgModuleFactory`,
- Angular CLI `ng mcp` security posture.

C. Testing & CI
- lint/test/build parallel jobs,
- Vitest migration,
- Playwright smoke on mock adapters,
- contract tests across mock + production adapters,
- SAST,
- dependency scanning,
- OpenSSF Scorecard,
- supply-chain controls for VS Code/Cursor extensions and local tooling.

D. Security & privacy
- CSP headers and nonces,
- cookie/BFF session path,
- localStorage JWT demo exceptions,
- no `eval` / `new Function`,
- no unsafe HTML bypass,
- Supabase explicit `GRANT`,
- `security_invoker = true` views,
- RLS tests and grants evidence,
- dev-token hygiene,
- MCP STDIO restrictions,
- agent tool allowlists,
- secrets never passed into prompts.

E. Documentation & OSS hygiene
- `AGENTS.md`,
- SECURITY.md,
- CODEOWNERS,
- PR template,
- OpenSSF Scorecard,
- honest limitations,
- self-assessment pinned to framework version,
- AI-agent safe local tooling policy.

F. SaaS domain
- multi-tenant context,
- billing through ports,
- members lifecycle,
- audit log,
- data export/deletion,
- Supabase grants as SaaS deployment requirement.

Specific questions:
1. Should Supabase explicit grants become a Must criterion?
2. Should `security_invoker = true` for views be Must, Should, or context-specific?
3. Should local MCP/STDIO tooling policy be a Documentation/OSS criterion, a Security criterion, or both?
4. Should `ng mcp` be mentioned as a risk/optional tool rather than a requirement?
5. Should Angular 22 be required for L2, or should Angular 21+ remain acceptable?
6. Should zoneless remain L2 gate?
7. Should Vitest be required for new apps but migration-only for existing apps?
8. Should OpenSSF Scorecard become L2 gate?
9. How should the framework avoid overreacting to one compromised extension while improving supply-chain posture?

For each proposed update, provide:
- existing criterion ID if applicable,
- proposed wording,
- old level and new level if changed,
- verification method,
- example evidence,
- migration impact,
- whether it is v1.5 compatible or v2.0 breaking.

Output format:
1. Executive summary.
2. Update table grouped by existing domain.
3. New criteria proposed for existing domains.
4. Criteria that should not change.
5. L1/L2/L3 gate recommendations.
6. v1.5 vs v2.0 recommendation.
7. Example self-assessment evidence.
8. CI / automation recommendations.
9. Risks and overreach warnings.
10. Sources with links.

Important:
- Do not design Developer Platform or AI-native SaaS criteria here; only reference them when a boundary matters.
- Focus on existing rubric maintenance.
- Keep criterion IDs stable where possible.
- Do not require bleeding-edge platform versions unless the market clearly demands them.
- Prefer evidence and CI gates over policy-only text.

