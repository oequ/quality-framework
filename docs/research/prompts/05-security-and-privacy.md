# Deep Research — Security & privacy (S1–S10)

Weight: 20% of total score. L1 gate: all Must criteria must pass. Highest buyer scrutiny area.

---

## Role

You are an application security engineer specializing in **SPA/SSR frontends**, **B2B SaaS auth**, and **OWASP ASVS** for browser applications.

## Context

Quality Framework v1.0 Security criteria:

| ID | Criterion | Level |
|----|-----------|-------|
| S1 | Strict CSP (no `unsafe-inline` / `unsafe-eval` in prod) | Must |
| S2 | CSP nonces with Angular | Should |
| S3 | No `bypassSecurityTrustHtml` without review | Must |
| S4 | Trusted Types | Could |
| S5 | Secure token storage (HttpOnly cookies / BFF — not JWT in localStorage) | Must |
| S6 | CSRF protection for cookie-based APIs | Must |
| S7 | Central auth interceptor / token attachment | Must |
| S8 | No dynamic code execution (`eval`, etc.) | Must |
| S9 | Route guards documented as UX-only; backend enforces auth | Must |
| S10 | SSR trusted proxy config (when applicable) | Should |

Our starter: Angular SPA, Supabase Auth (JWT in localStorage by default), meta-tag CSP with `unsafe-inline`, RLS on backend, demo labeled non-production for token storage.

## Research questions

### 1. 2026 B2B SaaS frontend security baseline

What do **OWASP**, **CISA**, and **enterprise procurement** expect from a commercial B2B web app frontend in 2026?

- OWASP ASVS 4.x / 5.x relevant chapters for SPA
- OWASP Top 10 2025 — frontend implications
- Is "frontend security" separately assessed vs full-stack?

### 2. Content Security Policy (S1, S2, S4)

Deep dive on **2026 CSP best practice** for Angular apps:

- Strict CSP without breaking Angular/Vite builds — proven configs
- Nonce-based CSP with Angular — official support status
- Trusted Types adoption rate and browser support
- Difference between **demo GitHub Pages CSP** vs **production CSP** — how should a starter document this?

Provide example CSP headers suitable for Angular 21 production.

### 3. Authentication token storage (S5)

Research the **localStorage vs HttpOnly cookie** debate as of 2026:

- Supabase official recommendation for SPAs vs SSR
- BFF pattern prevalence (Next.js influence on Angular teams)
- PKCE + refresh token rotation expectations
- Third-party cookie deprecation impact

**Critical question:** For an OSS **starter**, is localStorage acceptable if documented as demo-only? What must be true to claim L2?

### 4. CSRF and session security (S6, S7)

- When is CSRF mandatory for SPAs using bearer tokens vs cookies?
- Angular `withXsrfConfiguration` — still relevant in 2026?
- Centralized auth interceptors vs SDK-managed auth (Supabase client)
- Token refresh race conditions — patterns

### 5. XSS and Angular sanitization (S3, S8)

- `bypassSecurityTrustHtml` — real-world incident data
- DOM XSS in rich text settings (org descriptions, email templates)
- ESLint security plugins (eslint-plugin-security, CodeQL)

### 6. Authorization model (S9)

Industry standard messaging for **"guards are not security"**:

- How Supabase RLS + JWT claims fit the story
- Multi-tenant isolation testing expectations
- IDOR prevention — frontend responsibilities vs backend

### 7. Privacy and compliance signals (2026)

What **privacy expectations** do EU and US B2B buyers have from the frontend?

- Cookie consent (GDPR/ePrivacy) — minimum viable for starter
- Data residency UI concerns
- SOC2 / ISO 27001 — what frontend artifacts are requested?

### 8. L1 / L2 / L3 mapping for security

| ID | Demo/starter (L1) acceptable | L2 production required | L3 exemplary |
|----|------------------------------|------------------------|--------------|

Should S5 be **Partial Pass** at L1 with documented demo exception (current approach)?

### 9. Starter credibility vs false security claims

What security **marketing claims** destroy trust?

- "Bank-grade encryption" without details
- Missing SECURITY.md
- Mock auth presented as production-ready

## Output format

1. Executive summary — honest security posture for OSS starter vs production fork (2026)
2. CSP implementation guide (demo vs prod tiers)
3. Auth storage decision tree (SPA + Supabase + Angular)
4. L1/L2/L3 mapping (S1–S10) with Partial Pass rules
5. Minimum SECURITY.md content template for starters
6. Top 10 security fixes ranked by ROI for Angular B2B SaaS
7. Bibliography (OWASP, Supabase security docs, Angular security guide, NIST)

## Source priorities

- owasp.org (ASVS, Top 10, CSP Cheat Sheet — latest revisions)
- Supabase security documentation (2025–2026)
- Angular security guide (angular.dev)
- auth0 / OKTA SPA architecture whitepapers
- Google Trusted Types documentation
- CISA secure by design guidance

## Constraints

- Do not recommend security through obscurity.
- Clearly label **SPA limitations** (anything in browser is attacker-controlled).
- Separate frontend controls from backend/RLS enforcement.
