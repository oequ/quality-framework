# Security & privacy

B2B SaaS frontends: XSS prevention, auth storage, CSRF, and clear separation of UI guards vs server authorization.

| ID | Criterion | Level | Verification | Ports note |
|----|-----------|-------|--------------|------------|
| **S1** | **Strict CSP.** Content-Security-Policy restricts `unsafe-inline` / `unsafe-eval` in production. | Must | Headers / deploy config | Demos may use relaxed policy—document. |
| **S2** | **CSP nonces.** Angular configured for nonces where inline assets are required. | Should | Architecture | Pair with S1 for production. |
| **S3** | **No `bypassSecurityTrustHtml`.** Banned or strictly reviewed with security justification. | Must | ESLint / CodeQL | User-generated content in SaaS settings. |
| **S4** | **Trusted Types.** Headers/policy support Trusted Types where feasible. | Could | Headers | Defense in depth for DOM XSS. |
| **S5** | **Secure token storage.** Production: HttpOnly cookies (or BFF pattern)—not JWT in `localStorage`. | Must | Architecture / docs | Mock demos may use sessionStorage—label as non-production. |
| **S6** | **CSRF protection.** `withXsrfConfiguration` or equivalent for cookie-based APIs. | Must | TypeScript config | Enable in production HTTP adapters. |
| **S7** | **Auth interceptor.** Tokens/headers attached centrally—not per adapter ad hoc. | Must | Code review | Single place for auth refresh logic. |
| **S8** | **No dynamic code execution.** No `eval`, `new Function`, string `setTimeout`. | Must | ESLint | Baseline JS security. |
| **S9** | **Guards are UX only.** Docs state route guards ≠ authorization; backend/RLS enforces access. | Must | Documentation | Critical for starter credibility. |
| **S10** | **SSR proxy trust.** If using SSR, trusted proxy configuration documented (SSRF mitigation). | Should | Config | When applicable only. |

[← Rubric index](./README.md)
