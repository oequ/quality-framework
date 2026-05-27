# Procurement appendix (informative)

**Status:** Informative draft for v1.4 — not part of the normative rubric. Maps Quality Framework criteria to common buyer questionnaires. For official requirements, see [rubric/](./rubric/README.md) and [l2-gates.md](./l2-gates.md).

**Rubric version:** Quality Framework v1.3+

## How buyers use this

Enterprise procurement often asks for:

- Security architecture evidence (ASVS, SOC2-oriented questions)
- Accessibility (VPAT / WCAG)
- Open-source supply chain (Scorecard, SBOM)
- Data subject rights (GDPR export/delete)

This appendix helps **map** framework IDs to those themes. It does **not** certify compliance.

## Security and privacy

| Buyer theme | Framework IDs | Evidence artifacts |
|-------------|---------------|-------------------|
| OWASP ASVS V3 Web Frontend | S1, S2, S3, S4, S8 | CSP headers, sanitizer policy, ESLint security |
| Session management | S5, S6, S7 | Cookie/BFF docs, CSRF config, interceptor |
| Authorization vs UI | S9, SaaS7 | QUALITY.md, RLS documentation |
| Vulnerability disclosure | D4, SECURITY.md | Private reporting, SLAs |
| SAST in CI | S11 | ESLint secure-coding workflow |
| Tenant isolation | SaaS1, SaaS2, T1 E2E | Cross-tenant E2E, RLS |

## Accessibility

| Buyer theme | Framework IDs | Evidence artifacts |
|-------------|---------------|-------------------|
| WCAG 2.2 AA primary flows | P1, P2, P3, P4, P11 | axe CI logs, manual audit |
| VPAT / ACR | P1 (L3 manual) | Roadmap in QUALITY.md if Partial L1 |
| EU Accessibility Act context | P1, synthesis | [00-synthesis-2026-summary.md](./research/00-synthesis-2026-summary.md) |

## Supply chain and OSS hygiene

| Buyer theme | Framework IDs | Evidence artifacts |
|-------------|---------------|-------------------|
| OpenSSF Scorecard | D3, T7 | README badge, scorecard workflow |
| Dependency automation | T7, T12 | Dependabot/Renovate, cooldown |
| Maintained project | D5, D6, D9 | CHANGELOG, CODEOWNERS, recent commits |
| AI-assisted development safety | D1 | AGENTS.md forbidden actions |

## SaaS and data governance

| Buyer theme | Framework IDs | Evidence artifacts |
|-------------|---------------|-------------------|
| Multi-tenancy | SaaS1, SaaS2 | Architecture diagram, E2E isolation |
| Billing | SaaS3, SaaS4 | BillingPort, adapter swap |
| GDPR export / erasure | SaaS12 | Export/delete UX or documented process |
| Audit trail | SaaS8 | Admin action logs |
| Enterprise SSO | SaaS11 | IdP integration (L3) |

## Architecture and engineering quality

| Buyer theme | Framework IDs | Evidence artifacts |
|-------------|---------------|-------------------|
| Modular monorepo | A1–A13 | Nx graph, boundary lint |
| Test strategy | T1–T4, T8, T11 | CI workflows, coverage reports |
| Production config | TS8 | Runtime config documentation |

## Suggested README sentence

```markdown
Self-assessed against [Quality Framework v1.3](https://github.com/oequ/quality-framework)
([docs/QUALITY.md](./docs/QUALITY.md)). Procurement mapping: [procurement appendix](https://github.com/oequ/quality-framework/blob/main/docs/procurement-appendix.md).
```

## v2.0 note

Normative procurement tier (buyer checklist template) is a [v2.0 RFC candidate](./rfc/README.md)—feedback welcome via GitHub issues (`rubric-feedback`).

[← Documentation index](./README.md)
