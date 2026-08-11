# User Story: 22 - Apply approved retention and deletion

**As a** security/privacy reviewer,
**I want** retention and deletion jobs to apply the approved policy per data class,
**so that** audio, transcripts, reports, events, and analytics are not retained longer than authorized.

## Acceptance Criteria

- Data records carry classification, purpose, tenant/site, source, and retention policy metadata.
- The system executes approved retention, archival, legal-hold, and deletion actions.
- Deletion jobs produce completion/failure evidence without logging sensitive content.
- Provisional audio 30-day and transcript/report two-year policies are configurable, not hard-coded as final law.
- Backup and restore behavior is tested for consistency with approved deletion.

## Dependencies and validation

- DPIA, legal basis, customer contract, and final retention schedule require approval.

## Relevant Context

### Scope and workflow
- Provisional policy: audio 30 days; transcripts/reports two years. These are configurable placeholders pending DPIA/legal/customer confirmation. See [security and privacy](../admin/security-and-privacy.md).

### Architecture and integration points
- Retention/legal-hold/deletion flow with audit evidence is diagrammed in [data flows](../architecture/data-flows.md) §4; lifecycle policies apply per zone.

### Security, privacy, and audit controls
- Risks R-009 (PDPA compliance) and R-017 (retention conflict); restored backups must not reintroduce deleted data.

### Existing implementation touchpoints
- [docs/architecture/security-governance.md](../architecture/security-governance.md) §5 — classification and lineage.
- [infra/docs/architecture/operations.md](../../infra/docs/architecture/operations.md) §3 — backup/restore consistency.

### Validation dependencies
- Final retention schedule per data class from legal review.
