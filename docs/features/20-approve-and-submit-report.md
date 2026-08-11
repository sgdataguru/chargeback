# User Story: 20 - Approve and submit incident report

**As a** control-room operator,
**I want** to review, revise, and explicitly approve an incident report before submission or export,
**so that** a human remains accountable for the final operational record.

## Acceptance Criteria

- A draft cannot be submitted or exported without an authorized explicit approval.
- Review and revision changes are retained with actor, timestamp, and version.
- The approved final report is distinguishable from AI-generated draft content.
- Submission/export records destination, method, actor, timestamp, and outcome.
- Unauthorized approval attempts and report tampering are blocked and logged.

## Dependencies and validation

- Submission integration versus controlled export and regulator requirements require confirmation.

## Relevant Context

### Scope and workflow
- Human review and explicit approval precede any submission/export; this is a core trust boundary in [architecture overview](../architecture/overview.md).

### Architecture and integration points
- Approval state machine: draft → under review → approved → submitted/exported; each transition is an auditable event. See [data flows](../architecture/data-flows.md) §3.

### Security, privacy, and audit controls
- Prohibited practice: no unattended AI report submission. See [security and privacy](../admin/security-and-privacy.md).

### Existing implementation touchpoints
- [docs/features/ai-sop-assistant.md](ai-sop-assistant.md) — human approval requirement.

### Validation dependencies
- Regulator submission channel (API vs. manual export) from design partner.
