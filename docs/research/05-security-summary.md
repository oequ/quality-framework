# Research summary — Security & privacy (May 2026)

Source: [Technical Assessment and Architectural Blueprint Modern Frontend Security.txt](./Technical%20Assessment%20and%20Architectural%20Blueprint%20Modern%20Frontend%20Security.txt)

## Executive summary

Enterprise buyers evaluate frontends against **OWASP ASVS 5.0** (Chapter V3 Web Frontend). OSS starters optimize onboarding and often ship **localStorage JWT** + **meta CSP** — acceptable only when labeled **demo-tier**. L2 requires **HTTP CSP with nonces**, **secure session transport** (cookies/BFF), and documented **guards = UX only**.

## Key findings

| Topic | 2026 consensus | Rubric action (v1.2) |
|-------|----------------|----------------------|
| S1 CSP | Demo: meta + limited unsafe-inline; Prod: HTTP header, nonce + strict-dynamic | Tier notes on S1 |
| S2 nonces | L2: `ngCspNonce` / `CSP_NONCE`; L3: edge-generated per request | L2 gate S2 Pass |
| S5 tokens | L1: localStorage only if demo-labeled; L2: HttpOnly/BFF path in repo | L2 gate S5 Pass |
| S6 CSRF | Required when using session cookies; N/A for bearer-only | Clarify S6 |
| S7 interceptor | Atomic refresh queue (RxJS) for concurrent 401s | Clarify S7 |
| S9 guards | UX only; RLS/API enforces authZ | Stay Must |
| S11 (new) | SAST: eslint secure-coding + browser-security in CI | Add S11 Should |
| Rich text | DOMPurify before any `bypassSecurityTrustHtml` | Clarify S3 |

## L1 / L2 / L3 (research view)

| ID | L1 (demo) | L2 (production) | L3 |
|----|-----------|-----------------|-----|
| S1 | Meta CSP documented | HTTP CSP, no unsafe-inline/eval | Edge + CDN nonce injection |
| S5 | localStorage + demo label (Partial ok) | Cookies or BFF migration path | HttpOnly + rotation + BFF |
| S2 | Not required | Nonces configured | Edge nonces |
| S4 | Not required | Trusted Types fallback | Strict TT enforcement |
| S9 | Comment in code | Documented + backend enforcement | E2E cross-tenant tests |

**Partial Pass:** S5 at L1 only with demo label + migration docs; S1/S6/S8/S9 — no Partial for Must gates.

## Top actions for adopters

1. Document demo vs production security in `docs/QUALITY.md`.
2. Replace meta CSP with HTTP headers before claiming L2.
3. Add BFF or `@supabase/ssr` cookie path; PKCE + refresh rotation.
4. Ban unreviewed sanitizer bypasses; ESLint security plugins in CI.
5. E2E: Tenant A token cannot read Tenant B resources.

[← Research index](./README.md)
