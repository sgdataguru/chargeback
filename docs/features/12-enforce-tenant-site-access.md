# User Story: 12 - Enforce tenant and site access

**As a** security/privacy reviewer,
**I want** every request, query, workflow, and retrieval to enforce tenant and site authorization,
**so that** customer and operational data cannot cross approved boundaries.

## Acceptance Criteria

- API, event consumer, control-room, analytics, and retrieval paths enforce server-side tenant/site policy.
- Cross-tenant and cross-site access attempts are denied and auditable.
- Deactivated devices and expired assignments cannot act for their prior scope.
- Access-denial tests cover officer, operator, supervisor, tenant administrator, and platform administrator roles.
- Sensitive fields are minimized in responses according to role and purpose.

## Dependencies and validation

- Enterprise identity, role model, and tenant/site hierarchy require confirmation.
- Penetration and authorization testing are required before production.

## Relevant Context

### Scope and workflow
- Multi-tenant shared platform with strong logical tenant/site isolation (strategy decision D-004). See [data-platform-strategy](../project-context/data-platform-strategy.md).
- Every core event carries tenant/site identifiers; the API is the policy enforcement point. See [architecture overview](../architecture/overview.md).

### Architecture and integration points
- Layer-by-layer enforcement matrix: API ingress, event consumers, operational store, control room, analytics, RAG retrieval. See [security governance](../architecture/security-governance.md) §3.

### Security, privacy, and audit controls
- Risk R-008 (cross-tenant/supervisor access) is Critical; automated authorization tests must cover cross-tenant, cross-site, stale-token, and deactivated-device attempts.

### Existing implementation touchpoints
- [src/sentinel_api/main.py](../../src/sentinel_api/main.py) — no authorization layer yet; must be added before any pilot use.
- [docs/features/control-platform.md](control-platform.md) — role definitions.

### Validation dependencies
- Identity provider selection and RBAC/ABAC model approval.
