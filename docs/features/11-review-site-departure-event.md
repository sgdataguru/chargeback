# User Story: 11 - Review site-departure event

**As a** supervisor,
**I want** site-departure signals to appear as advisory events with context,
**so that** I can review a possible coverage issue without treating uncertain GPS as proof of misconduct.

## Acceptance Criteria

- A geofence-policy event includes site, device, assignment, time, location confidence, and applicable rule version.
- The event is clearly labelled as requiring human/contextual review.
- No automated disciplinary conclusion is generated.
- Supervisors see only site-level information within their authorization.
- Review action and outcome are recorded and auditable.

## Dependencies and validation

- Site geofence calibration and customer policy require agreement.
- GPS accuracy and indoor behavior require field validation.

## Relevant Context

### Scope and workflow
- Site-departure events target the handover-evasion problem from the meeting; they are advisory signals requiring human review, never automated misconduct findings. Risk R-005. See [risk register](../project-context/risk-constraint-register.md).

### Architecture and integration points
- Geofence evaluation consumes location events against per-site configured boundaries and rule versions; results publish as events.

### Security, privacy, and audit controls
- Supervisor sees site-level context only; review action and outcome are audited. See [security governance](../architecture/security-governance.md).

### Existing implementation touchpoints
- [docs/features/control-platform.md](control-platform.md) — device lifecycle and site-boundary policy evaluation.
- [docs/project-context/data-platform-strategy.md](../project-context/data-platform-strategy.md) §3.6 — geofence policy position.

### Validation dependencies
- Customer contracts defining permitted geofence use (assumption A-012).
