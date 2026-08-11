# User Story: 4 - Monitor wearable health

**As a** control-room operator,
**I want** an authorized view of device connectivity, battery, firmware, assignment, and last-seen status,
**so that** I can identify devices that cannot reliably support emergency workflows.

## Acceptance Criteria

- The control room shows only devices and sites the operator is authorized to view.
- Health state distinguishes online, delayed, offline, low battery, unsupported firmware, and misassigned device conditions.
- Stale or missing telemetry is visibly marked rather than shown as current.
- Health state changes create events and audit evidence.
- The view does not expose officer-to-device transcripts or other prohibited content.

## Dependencies and validation

- Battery and connectivity thresholds must be calibrated from field measurements.
- Vendor telemetry capabilities require validation.

## Relevant Context

### Scope and workflow
- Health signals: last seen, connectivity, battery, firmware, assignment, SIM state, OTA state. See the observability model in [operations architecture](../../infra/docs/architecture/operations.md).

### Architecture and integration points
- Health/telemetry arrive as canonical events and project into the curated control read model; stale state is flagged, not hidden. See [data flows](../architecture/data-flows.md) storage zones.

### Security, privacy, and audit controls
- Views are site-scoped per role; supervisors never see officer-to-device transcripts. See [control platform feature](control-platform.md).

### Existing implementation touchpoints
- [docs/features/control-platform.md](control-platform.md) — access model and lifecycle records.
- [infra/docs/architecture/operations.md](../../infra/docs/architecture/operations.md) — device/fleet monitoring signals.

### Validation dependencies
- Vendor diagnostic/telemetry granularity; field-measured battery profile vs. 24-hour target.
