# User Story: 6 - Manage staged OTA release

**As a** hardware/edge operator,
**I want** to roll out a signed wearable firmware release to staged cohorts with monitoring and rollback controls,
**so that** updates can be deployed without disrupting deployed safety workflows.

## Acceptance Criteria

- Only approved and signed firmware artifacts can be selected for deployment.
- A release records source/version, test evidence, target cohort, start state, rollout progress, and rollback plan.
- Rollout progresses in stages and can be stopped by an authorized operator.
- Device post-update health and critical workflow status are monitored.
- Failed rollout triggers rollback or stop workflow according to validated vendor capability.
- OTA approval, deployment, monitoring, stop, and rollback actions are audit-logged.

## Dependencies and validation

- Vendor signed firmware, rollback, staged rollout, and diagnostics capabilities require supplier validation.
- Hardware-in-loop testing must be completed before promotion.

## Relevant Context

### Scope and workflow
- OTA flow: signed approved release → hardware-in-loop test → staged cohort rollout → health monitoring → stop/rollback. See [data flows](../architecture/data-flows.md).
- Risk R-024: unauthorized or failed OTA can disrupt deployed safety devices. See [risk register](../project-context/risk-constraint-register.md).

### Architecture and integration points
- Release approval, cohorts, stop conditions, and rollback evidence are specified in [operations architecture](../../infra/docs/architecture/operations.md) §5.

### Security, privacy, and audit controls
- Signed packages, provenance, and release audit trail are mandatory; OTA security review required before production per [security and privacy](../admin/security-and-privacy.md).

### Existing implementation touchpoints
- [infra/docs/architecture/operations.md](../../infra/docs/architecture/operations.md) — OTA release pipeline requirements.

### Validation dependencies
- Supplier signed-firmware and rollback support.
