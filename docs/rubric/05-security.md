# Security & privacy

B2B SaaS frontends: XSS prevention, session management, ASVS-aligned controls. See [research summary](../research/05-security-summary.md).

| ID | Criterion | Level | Verification | L1 demo / L2 production notes |
|----|-----------|-------|--------------|-------------------------------|
| **S1** | **Strict CSP.** Restricts `unsafe-inline` / `unsafe-eval` in production deployments. | Must | Headers / deploy config | **L1:** HTML `<meta>` CSP allowed if documented demo-only (styles-only `unsafe-inline` max). **L2:** HTTP `Content-Security-Policy` header; no unsafe-inline/eval. **No Partial** for production claims. |
| **S2** | **CSP nonces with Angular.** `ngCspNonce`, `CSP_NONCE`, or `autoCsp` for inline styles/scripts with strict CSP. | Should | Architecture | **L2 gate:** Pass required. **L3:** per-request nonce at CDN edge (not origin-cached). |
| **S3** | **No unreviewed `bypassSecurityTrustHtml`.** Banned or security-reviewed; DOMPurify (or equivalent) before rich HTML. | Must | ESLint / CodeQL | **L1 Partial:** isolated, documented bypasses not exposed to user HTML. |
| **S4** | **Trusted Types.** CSP `require-trusted-types-for 'script'` where feasible; Angular fallback sanitization. | Could | Headers | **L2:** supported as fallback. **L3:** strict enforcement. |
| **S5** | **Secure token storage.** Production: HttpOnly cookies or BFF — not JWT in `localStorage`. | Must | Architecture / docs | **L1 Partial:** `localStorage`/`sessionStorage` only if labeled **demo/sandbox** + migration path documented. **L2 gate:** Pass requires cookie/BFF config in repo. |
| **S6** | **CSRF protection.** `withXsrfConfiguration` (or equivalent) for **cookie-based** session APIs. | Must | TypeScript config | Not required for pure `Authorization: Bearer` from memory. **No Partial** if cookies used without CSRF. |
| **S7** | **Auth interceptor.** Central token attach + refresh; **single-flight** refresh on concurrent 401s. | Must | Code review | No per-adapter ad hoc auth headers. |
| **S8** | **No dynamic code execution.** No `eval`, `new Function`, string `setTimeout` code. | Must | ESLint | **No Partial.** |
| **S9** | **Guards are UX only.** Documented: route guards ≠ authorization; backend/RLS/API enforces access. | Must | Documentation + tests | **No Partial.** Cross-tenant negative tests recommended for L3. |
| **S10** | **SSR trusted proxy.** Trusted proxy / forwarded-header config documented when using SSR. | Should | Config | **L1 N/A** if no SSR. |
| **S11** | **SAST in CI.** ESLint security plugins (e.g. secure-coding, browser-security) on PRs. | Should | CI | Complements S3/S8; maps to ASVS V1/V3 themes. |

[← Rubric index](./README.md)
