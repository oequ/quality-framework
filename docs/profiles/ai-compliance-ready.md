# AI-Native Profile: Compliance-ready

**Status:** Draft v1.5 candidate  
**Purpose:** prove that a product can disclose, audit, and preserve provenance for AI-generated or AI-modified content.

## Required criteria

| ID | Criterion | Required result |
|----|-----------|-----------------|
| [AI6](./ai-native.md#ai6--generated-content-disclosure) | Generated-content disclosure | Pass |

Required for media generation in regulated, public-distribution, or EU-market contexts:

| ID | Criterion | Required result |
|----|-----------|-----------------|
| [AI7](./ai-native.md#ai7--content-provenance-strategy) | Content provenance strategy | Partial or Pass with documented rollout plan |

## L3 expectation

| ID | Criterion | Target |
|----|-----------|--------|
| [AI7](./ai-native.md#ai7--content-provenance-strategy) | Content provenance strategy | Pass with durable machine-readable provenance and integrity validation |

## Evidence checklist

- Generation UI clearly indicates when content is AI-generated or materially AI-modified.
- Export/download surfaces preserve AI-origin metadata where applicable.
- `docs/QUALITY.md` links to the AI disclosure policy or user-facing docs.
- Generated artifacts record origin metadata in a database, manifest, or artifact store.
- Media products have a documented provenance strategy such as C2PA, signed metadata, watermarking, or an equivalent standard.
- Provenance implementation is verified with sample exported artifacts.

## EU AI Act Article 50 note

Article 50 transparency requirements for generated content begin taking effect in 2026. The profile treats clear user disclosure as the L2 baseline and machine-readable provenance as the next step for media products.

Do not claim this profile solely because marketing pages mention AI. Evidence must exist in the product UI, exported artifacts, or audit metadata.

## Typical failures

- No UI disclosure that generated media is AI-generated.
- Provenance stored only in logs that users cannot access or verify.
- Custom watermarking claims with no detection or verification path.
- Requiring advanced media provenance for an internal text-only assistant without external publication risk.

## Vendor neutrality

Examples such as C2PA, SynthID, Digimarc, or managed signing infrastructure may be useful, but the profile requires a verifiable provenance capability, not a specific vendor.

## Related criteria

- [S1 — Strict CSP](../rubric/05-security.md)
- [S5 — Secure token storage](../rubric/05-security.md)
- [SaaS12 — Data export & deletion](../rubric/09-saas-domain.md)
- [D9 — README credibility](../rubric/08-documentation-oss.md)

