# User Story: 18 - Refuse off-topic AI request

**As a** security/privacy reviewer,
**I want** personal, non-work, unsafe, and prompt-injection requests to be refused,
**so that** the assistant remains limited to approved security operations.

## Acceptance Criteria

- Personal and non-work requests receive a controlled refusal.
- Prompt-injection attempts do not reveal system prompts, secrets, inaccessible SOPs, or cross-site data.
- The model cannot command a device or submit an incident report.
- Refusal reason and policy version are logged for audit and evaluation.
- Red-team cases are included in the release regression suite.

## Dependencies and validation

- AI safety evaluation set and approved refusal taxonomy require definition.

## Relevant Context

### Scope and workflow
- Meeting precedent: site phones were misused for international personal calls at agency cost; guardrails block personal/non-work/off-topic requests at the model layer. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md).

### Architecture and integration points
- Refusal enforcement is application-level plus prompt-level; retrieved content is untrusted input. See [security governance](../architecture/security-governance.md) §6.

### Security, privacy, and audit controls
- Risks R-011 (hallucination) and R-013 (prompt injection); red-team cases are release gates.

### Existing implementation touchpoints
- [docs/features/ai-sop-assistant.md](ai-sop-assistant.md) — guardrails list.
- [infra/docs/architecture/operations.md](../../infra/docs/architecture/operations.md) — AI refusal/latency monitoring signals.

### Validation dependencies
- Refusal taxonomy and evaluation thresholds agreed with security operations.
