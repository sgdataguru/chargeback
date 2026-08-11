# User Story: 8 - Receive duress alert

**As a** control-room operator,
**I want** a high-priority alert when an authorized officer invokes duress on an assigned device,
**so that** I can coordinate a timely response.

## Acceptance Criteria

- A valid duress event reaches the authorized control-room view as high priority.
- The alert identifies tenant, site, device, assignment context, scenario, timestamps, and permitted location information.
- The operator can acknowledge the alert and record escalation status.
- Alert creation, delivery, acknowledgement, and escalation are auditable.
- Operators cannot see alerts outside their authorized sites.
- Duplicate delivery does not create multiple active incidents.

## Dependencies and validation

- Alert latency, escalation timer, and notification thresholds must be agreed with operations.
- Cellular and device delivery behavior require field testing.

## Relevant Context

### Scope and workflow
- Duress is a distinct high-priority scenario in the approved catalogue. See [emergency guidance feature](emergency-guidance.md) acceptance criteria.

### Architecture and integration points
- Alerts propagate via the event stream to the curated control read model; the control room consumes authorized read models, not raw device data. See [architecture overview](../architecture/overview.md) and [data flows](../architecture/data-flows.md) §1.
- Delivery states: requested, delivered, displayed, acknowledged, escalated.

### Security, privacy, and audit controls
- Operators see only authorized sites; all alert lifecycle transitions are auditable.

### Existing implementation touchpoints
- [src/sentinel_api/main.py](../../src/sentinel_api/main.py) — duress scenario exists but no alert publication path yet.
- [infra/docs/architecture/operations.md](../../infra/docs/architecture/operations.md) — alert severity model.

### Validation dependencies
- Control-room escalation policy and latency targets from design partner.
