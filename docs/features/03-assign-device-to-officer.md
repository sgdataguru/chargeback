# User Story: 3 - Assign device to officer and site

**As a** tenant administrator,
**I want** to assign a provisioned wearable to an authorized officer and site for a defined period,
**so that** device events are evaluated only in the correct tenant, site, and assignment context.

## Acceptance Criteria

- An administrator can select an active device, officer, tenant, site, start time, and end time.
- Conflicting active assignments are blocked or require an explicit authorized override.
- Device events include the validated assignment context, not just untrusted client claims.
- Assignment start, change, suspension, and end are event-driven and auditable.
- The device cannot use the previous assignment after the assignment ends.

## Dependencies and validation

- Tenant, site, user, and role directory model must be agreed.
- Field devices must support receiving and applying assignment or configuration state.

## Relevant Context

### Scope and workflow
- Assignment is the core assurance link: device ↔ officer ↔ site ↔ time period. The meeting decision requires GPS to detect devices leaving a site rather than being handed over between shifts. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md).
- `device assigned` / `device deactivated` are canonical domain events per [data-platform-strategy](../project-context/data-platform-strategy.md) §3.4.

### Architecture and integration points
- The API validates assignment server-side before scenario processing; untrusted client claims are not accepted. See [data flows](../architecture/data-flows.md).
- The starter API in [src/sentinel_api/main.py](../../src/sentinel_api/main.py) currently accepts only `scenario` and `site_id` — it lacks device identity and assignment validation and must be extended.

### Security, privacy, and audit controls
- Assignment changes are auditable; a device loses prior scope immediately on assignment end.

### Validation dependencies
- Vendor support for configuration/assignment state push to devices.
