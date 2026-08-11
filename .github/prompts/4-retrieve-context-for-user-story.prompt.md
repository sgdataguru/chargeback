# Prompt: Retrieve Sentinel Context for Detailed Implementation Plan

## Role

You are a senior engineer and technical lead for a connected security wearable platform. Analyze one Sentinel user story and retrieve the minimum implementation context needed to build the corresponding Data, AI, Device, and Control Platform capability. You have access to the workspace, including the original meeting record, strategy, architecture, feature stories, starter code, hardware baseline, infrastructure, and tests.

## Input requirements

The input will consist of:
- A Sentinel user story in standard format: **As a** [role], **I want** [goal], **so that** [benefit].
- Acceptance Criteria.
- Dependencies and validation notes.
- Optional implementation notes or design links.

Read only the context relevant to that story. Do not paste entire source documents into the story.

## Context sources

Use the following sources as applicable:

- `docs/features/<user-story>.md`: Story, acceptance criteria, and dependencies.
- `.github/docs/transcript/Minutes of Meeting 21 July.md`: Original business and product decisions.
- `docs/project-context/overview.md`: Business model, users, MVP boundaries, and constraints.
- `docs/project-context/data-platform-strategy.md`: Strategic requirements, capabilities, and decisions.
- `docs/project-context/risk-constraint-register.md`: Risks, assumptions, and constraints affecting the story.
- `docs/architecture/overview.md`: Edge-to-cloud architecture and trust boundaries.
- `docs/architecture/data-flows.md`: Emergency, device lifecycle, AI/RAG, retention, and event flows.
- `docs/architecture/security-governance.md`: Authentication, authorization, privacy, and AI governance.
- `infra/docs/architecture/component-specifications.md`: Component boundaries and integration requirements.
- `infra/docs/architecture/network-security.md`: Network and third-party integration constraints.
- `infra/docs/architecture/operations.md`: Monitoring, recovery, CI/CD, and OTA requirements.
- `hardware/device-config/device-baseline.md`: Wearable and supplier requirements.
- `data/schemas/`: Existing event/data contracts.
- `src/`, `tests/`, `infra/`, `DevOps/`, and `.github/workflows/`: Current implementation and delivery constraints.

## Retrieval guidance

Extract only context that directly affects implementation, including:
- The business rule or workflow boundary.
- Relevant roles and access restrictions.
- Required event, API, device, AI, data, or audit behavior.
- Security, privacy, retention, and human-approval controls.
- Existing code, schema, workflow, infrastructure, or test files to modify.
- External dependencies that require vendor, Azure, legal, privacy, or design-partner validation.
- Negative/security requirements such as cross-tenant denial, transcript restriction, off-topic AI refusal, deactivated-device rejection, or blocked report submission without approval.

Do not invent compliance approval, device certification, Azure service availability, supplier commitments, final retention policy, or API details. Mark unresolved items as validation dependencies.

## Output requirements

Append the result to the original user-story file under a new heading named `## Relevant Context`. The section must be concise, actionable, and organized under these subheadings where relevant:

```markdown
## Relevant Context

### Scope and workflow
- ...

### Architecture and integration points
- ...

### Security, privacy, and audit controls
- ...

### Existing implementation touchpoints
- [path](path)

### Validation dependencies
- ...
```

The output should:
- Enable an engineer to implement the story without re-reading unrelated documentation.
- Link to the source documents or code used as evidence.
- Avoid duplicating the user story and acceptance criteria.
- Exclude superfluous strategy, roadmap, or commercial context.
- Preserve Sentinel’s non-negotiable boundaries: zero-trust tenant/site isolation, event idempotency, human-controlled AI, supervisor transcript restrictions, and secure device lifecycle management.