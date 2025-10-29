# 07. Security

## Identity and Access
- Authentication: who you are (JWT, OAuth2/OpenID Connect).
- Authorization: what you can do (RBAC/ABAC).

## Service-to-Service Trust
- mTLS between services.
- Rotate certificates and secrets.

## Data Protection
- Encrypt in transit (TLS) and at rest.
- Do not log secrets or PII.

## Input Validation
- Validate at edges. Sanitize user input.

## Supply Chain
- Pin versions. Scan dependencies. SBOM.

## Multi-Tenancy and Isolation
- Separate data and access per tenant.

## Rate Limiting and WAF
- Protect from abuse and attacks.
