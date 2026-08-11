# User Story: 24 - Recover platform from failure

**As a** operations/SRE user,
**I want** tested backup, restore, replay, and rollback procedures,
**so that** Sentinel can recover from cloud, data, deployment, or device-update failures without losing required evidence.

## Acceptance Criteria

- Backup and restore scope is defined by data class and approved retention policy.
- Event replay can rebuild control read models without changing source events.
- Failed application or infrastructure deployment has a documented rollback path.
- Failed OTA rollout has a tested stop or rollback process within vendor capability.
- Recovery tests verify tenant/site authorization and audit continuity after restoration.

## Dependencies and validation

- Azure service RPO/RTO, backup options, and recovery targets require validation.

## Relevant Context

### Scope and workflow
- Recovery model: durable events as source of truth; rebuildable projections; idempotent replay; tested rollback for application, infrastructure, and OTA. See [operations architecture](../../infra/docs/architecture/operations.md) §3.

### Architecture and integration points
- Restore must preserve tenant/site authorization and audit continuity; legal-hold and deletion consistency verified post-restore.

### Security, privacy, and audit controls
- Device compromise path: deactivate → revoke → preserve evidence → replace → verify wipe.

### Existing implementation touchpoints
- [infra/docs/architecture/operations.md](../../infra/docs/architecture/operations.md) §3 — resilience requirements.

### Validation dependencies
- Azure service DR capabilities and RPO/RTO agreement per data class.
