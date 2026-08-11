# User Story: 14 - Audit sensitive actions

**As a** security/privacy reviewer,
**I want** tamper-evident records of sensitive device, access, AI, content, and report actions,
**so that** I can investigate incidents and demonstrate control operation.

## Acceptance Criteria

- Audit records include actor/workload, action, tenant/site, target, timestamp, outcome, correlation ID, and version where relevant.
- Audit coverage includes device lifecycle, privileged changes, sensitive views, SOP approval/indexing, AI retrieval metadata, report approval, and deployment actions.
- Audit records are append-oriented or otherwise protected from unauthorized modification.
- Audit access is restricted and itself auditable.
- Security-event review procedures identify owner and evidence source.

## Dependencies and validation

- Audit retention, legal hold, and SIEM requirements require validation.

## Relevant Context

### Scope and workflow
- Audit coverage: device lifecycle, privileged changes, sensitive views, SOP approval/indexing, AI retrieval metadata, report approval, OTA, and deployment activity. See [security governance](../architecture/security-governance.md) §7.

### Architecture and integration points
- Audit events flow through the same event stream into the raw evidence/audit store; Microsoft Sentinel is the SIEM candidate. See [architecture overview](../architecture/overview.md).

### Security, privacy, and audit controls
- Audit records are append-oriented, time-synchronized, correlation-ID'd, and access-restricted.

### Existing implementation touchpoints
- [docs/architecture/security-governance.md](../architecture/security-governance.md) §7 — audit evidence requirements.
- [infra/docs/architecture/operations.md](../../infra/docs/architecture/operations.md) — security signal monitoring.

### Validation dependencies
- SIEM retention/cost model and audit review cadence.
