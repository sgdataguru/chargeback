# User Story: 16 - Approve and index SOP content

**As a** SOP/content owner,
**I want** to approve, classify, version, and index site SOP content,
**so that** AI retrieval uses only current and authorized operational knowledge.

## Acceptance Criteria

- A document records owner, tenant, site, classification, validity period, version, approval state, and scenario tags.
- Only approved and valid documents are eligible for indexing.
- Index changes record corpus version, approver, timestamp, and source reference.
- Withdrawn or expired content is no longer retrievable for new queries.
- Invalid, unapproved, or incorrectly scoped content is quarantined or rejected.

## Dependencies and validation

- SOP source owners and regulator/report templates require confirmation.

## Relevant Context

### Scope and workflow
- Meeting decision: detailed SOPs remain in existing systems; the device gets critical steps; deeper queries hit the underlying document via AI on demand. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md).

### Architecture and integration points
- Intake → review → classification → tenant/site metadata → validity period → approval → index; only approved content is eligible. See [data-platform-strategy](../project-context/data-platform-strategy.md) §3.5.

### Security, privacy, and audit controls
- Risk R-025 (outdated/unapproved SOPs); approval and withdrawal are audited with version lineage.

### Existing implementation touchpoints
- [src/ai/README.md](../../src/ai/README.md) — AI module placeholder for search/OpenAI adapters.
- [docs/features/ai-sop-assistant.md](ai-sop-assistant.md) — guardrails and evaluation criteria.

### Validation dependencies
- Approved SOP corpus owners and classification scheme per site.
