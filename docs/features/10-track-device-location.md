# User Story: 10 - Track device location with confidence

**As a** control-room operator,
**I want** device location updates to include accuracy and freshness information,
**so that** I can interpret the device position without mistaking approximate GPS data for certainty.

## Acceptance Criteria

- Location events include occurred/received timestamps, coordinates, and accuracy/confidence where available.
- Stale, low-confidence, or implausible locations are visibly flagged.
- Location visibility is restricted to authorized tenant/site roles and approved purpose.
- Raw location history is not exposed to analytics or supervisors by default.
- Location events are deduplicated and auditable.

## Dependencies and validation

- GPS accuracy at indoor and outdoor pilot sites requires field testing.
- Final privacy and customer policy for location use requires approval.

## Relevant Context

### Scope and workflow
- GPS is built in to detect site departure rather than shift handover; location is sensitive personal data. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md).

### Architecture and integration points
- Location events use the canonical envelope with `occurred_at`/`received_at`; coordinates carry accuracy. See [data/schemas/emergency-event.schema.json](../../data/schemas/emergency-event.schema.json) location object (`accuracy_metres`).

### Security, privacy, and audit controls
- Location classified as sensitive personal data; analytics users get no raw location history. See [security governance](../architecture/security-governance.md) §5.

### Existing implementation touchpoints
- [docs/project-context/data-platform-strategy.md](../project-context/data-platform-strategy.md) §3.6 — geofence events are advisory, not proof of misconduct.

### Validation dependencies
- Field GPS accuracy measurements; DPIA outcome for location processing.
