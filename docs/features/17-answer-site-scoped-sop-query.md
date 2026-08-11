# User Story: 17 - Answer site-scoped SOP query

**As a** security officer,
**I want** to ask an approved security-domain question and receive a cited answer from my site’s current SOPs,
**so that** I can get operational guidance without searching a long document.

## Acceptance Criteria

- The requester’s identity, tenant/site scope, purpose, and security-domain eligibility are checked before retrieval.
- Retrieval uses approved, valid, tenant/site-filtered content.
- Substantive answers include source references and indicate uncertainty when approved content is insufficient.
- Cross-tenant and cross-site content is never returned.
- Retrieval and generation metadata are auditable without exposing prohibited transcripts.

## Dependencies and validation

- Azure AI Search/OpenAI availability, corpus quality, and evaluation thresholds require validation.

## Relevant Context

### Scope and workflow
- Query flow: authenticate → tenant/site/purpose policy → filtered retrieval → guardrailed generation → cited answer. See [data flows](../architecture/data-flows.md) §3.

### Architecture and integration points
- Azure OpenAI + Azure AI Search RAG confirmed in project decisions; application enforces filters before retrieval — the model never chooses scope. See [security governance](../architecture/security-governance.md) §6.

### Security, privacy, and audit controls
- Risk R-012 (retrieval isolation failure) is Critical; adversarial isolation tests required. Corpus/prompt/model/retrieval versions are auditable.

### Existing implementation touchpoints
- [src/ai/README.md](../../src/ai/README.md) — adapter placeholder; [docs/features/ai-sop-assistant.md](ai-sop-assistant.md) — evaluation metrics (groundedness, citation accuracy, isolation).

### Validation dependencies
- Azure Singapore model/service availability confirmation (risk R-010).
