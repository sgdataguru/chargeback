# User Story: 13 - Restrict supervisor access to transcripts

**As a** supervisor,
**I want** site-level operational information without officer-to-device transcripts,
**so that** I can manage site assurance while respecting the required access boundary.

## Acceptance Criteria

- Supervisor views include authorized site-level alert, device, and workflow information.
- Supervisor role cannot retrieve raw audio, officer-to-device transcripts, or unrestricted voice-derived content.
- Attempts to access prohibited content are denied and logged.
- Control-room and privacy-approved roles have separate, auditable access paths where permitted.
- Access tests explicitly verify transcript denial for supervisors.

## Dependencies and validation

- Final privacy/legal policy and customer access model require confirmation.

## Relevant Context

### Scope and workflow
- Meeting decision: supervisors see site-level information only, not officer-to-device transcripts. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md).

### Architecture and integration points
- Supervisor queries hit curated control views that exclude transcript content by schema design, not just UI filtering. See [data flows](../architecture/data-flows.md) §6 storage zones.

### Security, privacy, and audit controls
- Transcript-access prohibition is a Prohibited Practice in [security and privacy](../admin/security-and-privacy.md); denial attempts are logged.

### Existing implementation touchpoints
- [docs/features/control-platform.md](control-platform.md) — supervisor role scope.
- [docs/architecture/security-governance.md](../architecture/security-governance.md) §3 — role boundaries table.

### Validation dependencies
- DPIA outcome confirming transcript access rules per role.
