---
description: Generate Sentinel user stories from the Data, AI, Device, and Control Platform architecture
stage: Development
subcategory: subcategory-development-common
rule_name: generate-sentinel-stories-from-architecture
rule_version: latest
---

# Prompt: Generate Sentinel User Stories from Architecture and Project Context

## Role

You are an expert Agile Business Analyst / Product Owner assistant for a connected security wearable platform. Analyze Sentinel project context and architecture artifacts to extract user stories that capture requirements and desired functionality for officers, control-room operators, supervisors, tenant/platform administrators, content owners, and operations teams.

## Input

You will receive the following documents:

- `docs/project-context/overview.md`: Business model, users, MVP boundaries, and constraints
- `docs/project-context/data-platform-strategy.md`: Strategic requirements, capabilities, and decisions
- `docs/project-context/value-delivery-roadmap.md`: Value outcomes and phase gates
- `docs/project-context/risk-constraint-register.md`: Risks, assumptions, and constraints
- `docs/architecture/overview.md`: Edge-to-cloud logical architecture and trust boundaries
- `docs/architecture/data-flows.md`: Emergency, device lifecycle, AI/RAG, retention, and data flows
- `docs/architecture/security-governance.md`: Authentication, authorization, privacy, and AI governance
- `infra/docs/architecture/component-specifications.md`: Component responsibilities and integration boundaries
- `infra/docs/architecture/network-security.md`: Network and integration security design
- `infra/docs/architecture/operations.md`: Monitoring, recovery, CI/CD, and OTA operations

Use the documents as requirements evidence. Do not invent compliance approval, device certification, Azure service availability, supplier commitments, or final retention policy. Where a story depends on an unvalidated decision, include that dependency in the story or acceptance criteria.

## Task

Analyze the provided files and generate a list of user stories based on their contents. The stories should represent distinct pieces of functionality or value from an end-user, operational, security, or governance perspective.

Prioritize stories for the Sentinel MVP:

- Device provisioning, identity, SIM association, assignment, health, deactivation, recycling, and OTA lifecycle
- Emergency scenario invocation, approved guidance, control-room alerting, acknowledgement, escalation, and audit evidence
- GPS/location and geofence-policy events with accuracy and human-review safeguards
- Tenant/site/role authorization, supervisor transcript restrictions, and audit logging
- Approved SOP ingestion, tenant/site-scoped retrieval, cited AI answers, off-topic refusal, and prompt-injection protection
- Incident-report drafting, human review, approval, and controlled submission/export
- Data quality, event idempotency, retention/deletion, monitoring, recovery, and operational support
- CI/CD, infrastructure, security scanning, and release evidence where they deliver stakeholder value

## Output Format & Guidelines

Generate **each user story as a separate Markdown file** within the `docs/features/` directory of the project.

**File Naming Convention:** Use a two-digit sequential number prefix followed by kebab-case based on the story's core goal (e.g., `01-provision-wearable-device.md`, `02-receive-duress-alert.md`).

**File Content Format:** Each markdown file should contain *one* user story following the standard format:

```markdown
# User Story: [Story Number] - [Brief Title Describing the Goal]

**As a** [type of user/role],
**I want** [to perform an action or achieve a goal],
**so that** [I gain a specific benefit or value].

## Acceptance Criteria

*   [Criterion 1]
*   [Criterion 2]
*   ... (Include if mentioned in the documents or clearly implied)

## Dependencies and validation

*   [Dependency, assumption, or validation item, if applicable]
```

**Crucially, ensure each story adheres to the INVEST principles:**

1.  **Independent:** Stories should be self-contained and ideally implementable without depending on others in the same batch (though natural dependencies between features are okay). Avoid tightly coupling unrelated concepts in one story.
2.  **Negotiable:** Stories are not contracts. They represent the essence of the requirement, leaving room for discussion and refinement of details during backlog grooming or sprint planning.
3.  **Valuable:** Each story must deliver tangible value to a specific end-user, stakeholder, or the system itself (e.g., improving performance, security). Clearly articulate the "so that" benefit.
4.  **Estimable:** The story should be clear and defined enough that the development team can reasonably estimate the effort required to implement it. Avoid vague or overly broad stories.
5.  **Small:** Stories should be small enough to be completed within a single iteration (e.g., a typical sprint). Break down large epics or features into smaller, manageable stories.
6.  **Testable:** Each story must have implicit or explicit acceptance criteria. It should be possible to verify that the story has been implemented correctly.

**VERY IMPORTANT: Vertical Slicing**

*   **DO:** Create stories that represent a complete, thin slice of end-to-end functionality, delivering user value. Example: "As a control-room operator, I want to receive and acknowledge a duress alert from an assigned device so that I can coordinate a timely response." (Touches device, API, event processing, control-room workflow, and audit evidence).
*   **DO NOT:** Split stories horizontally by technical layer or component. Avoid stories like: "Create the alert database table," "Build the alert API endpoint," or "Design the alert UI." These are tasks, not user stories.
*   **DO:** Include security, privacy, AI safety, device lifecycle, and operational stories when they deliver verifiable stakeholder value.
*   **DO NOT:** Create stories that assume the AI can autonomously submit reports, command devices, or access unapproved content.

## Constraints

*   Assign a sequential number to each story title (e.g., `# User Story: 1 - Provision Wearable Device`).
*   Focus on extracting user-centric requirements and value propositions discussed.
*   Ignore conversational filler, off-topic discussions, or administrative details unless they directly inform a requirement.
*   Use Sentinel roles where applicable: security officer, control-room operator, supervisor, tenant administrator, platform administrator, SOP/content owner, hardware/edge operator, security/privacy reviewer, and operations/SRE.
*   If acceptance criteria are explicitly discussed, include them as bullet points under the relevant story.
*   Include negative/security acceptance criteria where relevant, such as cross-tenant access denial, supervisor transcript denial, off-topic AI refusal, deactivated-device rejection, and report submission without approval being blocked.
*   Keep stories small enough for a single iteration and avoid combining unrelated device, AI, data, and control-room capabilities.
*   Present the output as a clear list of user stories.