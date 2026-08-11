# User Story: 7 - Invoke approved emergency scenario

**As a** security officer,
**I want** to select an approved emergency scenario on my assigned wearable,
**so that** I can receive concise critical guidance and notify the control room without reading a long SOP.

## Acceptance Criteria

- The device offers only approved scenarios: fire, medical emergency, intrusion, duress, and suspicious person/package.
- The request is rejected when the device is unregistered, deactivated, unassigned, or assigned to another tenant/site.
- A valid request records device, site, assignment, scenario, location confidence where available, and occurred/received timestamps.
- A valid request returns or displays the relevant approved three-to-six critical steps.
- An out-of-scope request is safely blocked and creates a policy event.
- The event remains auditable if the immediate device response is delayed or lost.

## Dependencies and validation

- Emergency interaction and offline/fallback behavior require wearable vendor validation.
- Final scenario content and escalation policy require design-partner approval.

## Relevant Context

### Scope and workflow
- Meeting decision: emergency prompts limited to 5–6 critical steps per scenario (fire, medical, break-in, etc.); full SOP dumps rejected. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md) and [emergency guidance feature](emergency-guidance.md).
- Flow: officer invokes scenario → signed event with site/location context → platform validates assignment → device receives steps → control room alerted. See [data flows](../architecture/data-flows.md) §1.

### Architecture and integration points
- Synchronous response limited to receipt/approved guidance; alert delivery is event-driven and durable.

### Existing implementation touchpoints
- [src/sentinel_api/main.py](../../src/sentinel_api/main.py) — `APPROVED_SCENARIOS` catalogue and `/emergency-prompts` endpoint; needs device identity, assignment validation, and event publication added.
- [data/schemas/emergency-event.schema.json](../../data/schemas/emergency-event.schema.json) — event contract with scenario enum and location object.
- [tests/unit/test_main.py](../../tests/unit/test_main.py) — approved/blocked scenario tests.

### Validation dependencies
- Design-partner sign-off on the three-to-six steps per scenario.
