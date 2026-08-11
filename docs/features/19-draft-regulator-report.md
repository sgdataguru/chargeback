# User Story: 19 - Draft regulator-format incident report

**As a** control-room operator,
**I want** an AI-assisted incident report draft from approved event and source context,
**so that** I can prepare a report efficiently without losing source traceability.

## Acceptance Criteria

- Report drafting uses an approved template and only authorized incident context.
- Draft fields identify missing or uncertain information instead of inventing facts.
- Source event/content references are preserved where substantive claims are made.
- The draft is clearly marked as not submitted and requires human review.
- Corpus, model/prompt, template, and request versions are auditable.

## Dependencies and validation

- Regulator report format and customer submission process require confirmation.

## Relevant Context

### Scope and workflow
- Meeting decision: incident report forms auto-generated in the regulator's required format; deeper queries go into the underlying document on demand. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md).

### Architecture and integration points
- Draft uses approved templates plus authorized incident context; source references preserved. See [data flows](../architecture/data-flows.md) §3.

### Security, privacy, and audit controls
- Risk R-014: drafts must not invent facts or submit autonomously; missing info is flagged, never fabricated.

### Existing implementation touchpoints
- [docs/features/ai-sop-assistant.md](ai-sop-assistant.md) — report field completeness metric.
- [src/ai/README.md](../../src/ai/README.md) — adapter placeholder.

### Validation dependencies
- Regulator format specification from design partner.
