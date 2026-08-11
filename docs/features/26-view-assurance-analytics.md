# User Story: 26 - View governed assurance analytics

**As a** tenant administrator,
**I want** governed metrics for device availability, alert response, workflow completion, and service assurance,
**so that** I can evaluate Sentinel’s operational value without accessing prohibited raw personal data.

## Acceptance Criteria

- Metrics use documented definitions, owners, filters, periods, and data-quality status.
- Users see only authorized tenant/site aggregates.
- Raw audio, unrestricted location history, and officer-to-device transcripts are excluded.
- Metric lineage can be traced to curated source events and ruleset versions.
- Missing or low-quality data is visibly represented rather than hidden.

## Dependencies and validation

- Design-partner KPI definitions and analytics tool selection require confirmation.

## Relevant Context

### Scope and workflow
- Analytics serve assurance buyers: response times, guidance delivery, device availability, coverage exceptions, incident volumes. See [data-platform-strategy](../project-context/data-platform-strategy.md) §4.3.

### Architecture and integration points
- Curated analytics zone separate from operational control; metric catalogue with owner, formula, quality checks, and privacy classification. See [data flows](../architecture/data-flows.md) §6.

### Security, privacy, and audit controls
- No raw audio, transcripts, or raw location history in analytics; lineage to curated sources required.

### Existing implementation touchpoints
- [docs/architecture/security-governance.md](../architecture/security-governance.md) §5 — analytics boundary.

### Validation dependencies
- KPI definitions and reporting tool selection with design partner.
