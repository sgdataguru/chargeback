# User Story: 23 - Monitor critical platform health

**As a** operations/SRE user,
**I want** alerts for device, event, API, data, AI, and security failures,
**so that** I can act before emergency workflows or evidence collection are materially affected.

## Acceptance Criteria

- Monitoring covers device connectivity, event lag, API failures, authorization denials, dead letters, alert delivery, AI retrieval, and retention jobs.
- Critical failures have severity, owner, runbook link, and escalation path.
- Monitoring records distinguish safety-critical, high, medium, and low conditions.
- Dashboards avoid exposing raw audio, transcripts, secrets, or unnecessary personal data.
- Alert rules are tested with synthetic or controlled failure events.

## Dependencies and validation

- SLOs, on-call model, SIEM integration, and alert thresholds require operations approval.

## Relevant Context

### Scope and workflow
- Full observability signal matrix: device/fleet, cellular delivery, API/identity, event/data, control room, AI/RAG, security. See [operations architecture](../../infra/docs/architecture/operations.md) §1.

### Architecture and integration points
- Azure Monitor + Application Insights + Microsoft Sentinel are the monitoring/SIEM candidates; diagnostic routing per environment.

### Security, privacy, and audit controls
- Risk R-018: monitoring gaps can hide device outages, access anomalies, or retention failures; dashboards exclude raw audio/transcripts.

### Existing implementation touchpoints
- [infra/docs/architecture/operations.md](../../infra/docs/architecture/operations.md) §2 — alert severity definitions.

### Validation dependencies
- SLO values and on-call ownership from operations.
