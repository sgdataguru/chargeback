# User Story: 9 - Acknowledge and escalate emergency alert

**As a** control-room operator,
**I want** to acknowledge and escalate an emergency alert from the control-room workflow,
**so that** ownership and response status are visible and auditable.

## Acceptance Criteria

- An authorized operator can acknowledge an active alert only for an authorized site.
- Escalation records reason, actor, time, destination/team, and workflow state.
- Acknowledgement and escalation update the alert state for authorized users.
- An unauthorized user cannot acknowledge or escalate another site’s alert.
- Late or duplicate workflow events reconcile without corrupting the active state.
- Each action produces an immutable event/audit record.

## Dependencies and validation

- Control-room RACI, escalation teams, and timers require design-partner agreement.

## Relevant Context

### Scope and workflow
- Acknowledgement and escalation are operator actions on the control workflow, producing immutable events. See [data flows](../architecture/data-flows.md) §1 sequence diagram.

### Architecture and integration points
- Operator actions go through the Sentinel API, which revalidates role/site authorization; state changes publish `Acknowledged` / `Escalated` events.
- Late or duplicate events reconcile per idempotency rules in [data flows](../architecture/data-flows.md) §5.

### Security, privacy, and audit controls
- Authorization enforcement matrix per layer is defined in [security governance](../architecture/security-governance.md) §3.

### Existing implementation touchpoints
- [docs/features/control-platform.md](control-platform.md) — role-based access model.

### Validation dependencies
- Escalation destinations and timer values from operations.
