# User Story: 21 - Process device events idempotently

**As a** operations/SRE user,
**I want** delayed, retried, and duplicate device events to reconcile safely,
**so that** alert state and audit evidence remain accurate under unreliable cellular connectivity.

## Acceptance Criteria

- Canonical events include event ID, schema version, tenant/site, device, occurred/received timestamps, and correlation ID.
- Duplicate event IDs do not create duplicate active incidents or workflow actions.
- Late events update or reconcile state according to documented ordering rules.
- Invalid or incompatible events are quarantined with review evidence.
- Replay can rebuild derived state without changing immutable source events.

## Dependencies and validation

- Event schema governance, vendor message semantics, and retry behavior require validation.

## Relevant Context

### Scope and workflow
- Cellular retries, duplicates, delayed delivery, and clock drift are expected operating conditions, not exceptions. Risk R-016. See [risk register](../project-context/risk-constraint-register.md).

### Architecture and integration points
- Canonical envelope fields and processing-mode boundaries are defined in [data flows](../architecture/data-flows.md) §5; consumers deduplicate on event ID and route invalid events to quarantine/dead letter.

### Security, privacy, and audit controls
- Rejected/replayed requests create audit events without triggering workflows.

### Existing implementation touchpoints
- [data/schemas/emergency-event.schema.json](../../data/schemas/emergency-event.schema.json) — initial event contract; needs `schema_version`, `received_at`, `correlation_id`, and idempotency fields added.
- [src/sentinel_api/main.py](../../src/sentinel_api/main.py) — no event publication yet.

### Validation dependencies
- Vendor message retry/ordering semantics from field testing.
