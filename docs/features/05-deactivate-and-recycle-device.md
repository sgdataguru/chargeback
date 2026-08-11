# User Story: 5 - Deactivate and recycle device

**As a** hardware/edge operator,
**I want** to deactivate, reset, and recycle a wearable with evidence that credentials and prior scope were removed,
**so that** a previous officer, tenant, or site cannot be exposed through a reassigned device.

## Acceptance Criteria

- Deactivation revokes the device credential and blocks future operational requests.
- The platform requires confirmation or supported evidence of reset/wipe before reassignment.
- Device, assignment, SIM, and tenant history remain auditable.
- A reassigned device has no access to prior tenant/site data, cached content, or credentials.
- Deactivation, wipe verification, reassignment, and retirement are audit-logged.

## Dependencies and validation

- Vendor support for remote wipe/reset and credential revocation requires validation.
- Final data-handling and privacy requirements require review.

## Relevant Context

### Scope and workflow
- The commercial model is subscription-based with devices recyclable across officers when they leave the agency. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md).
- Deactivation → credential revocation → reset/wipe evidence → reassignment or retirement. See [data flows](../architecture/data-flows.md) device lifecycle diagram.

### Architecture and integration points
- Vendor adapter owns reset/wipe mechanics; Sentinel requires verification evidence before reassignment. See [component specifications](../../infra/docs/architecture/component-specifications.md).

### Security, privacy, and audit controls
- Risk R-007: reassignment must not expose prior officer/tenant/site data. See [risk register](../project-context/risk-constraint-register.md).

### Existing implementation touchpoints
- [docs/architecture/security-governance.md](../architecture/security-governance.md) — device credential revocation requirements.

### Validation dependencies
- Vendor remote-wipe/reset capability and proof mechanism.
