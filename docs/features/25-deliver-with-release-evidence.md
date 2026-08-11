# User Story: 25 - Deliver changes with release evidence

**As a** platform administrator,
**I want** code, infrastructure, AI, and device changes to pass automated and gated release checks,
**so that** only reviewed and tested changes reach staging or production.

## Acceptance Criteria

- Pull requests run linting, tests, secret scanning, dependency scanning, and infrastructure checks.
- Terraform changes produce reviewable plans and use federated deployment identity.
- AI prompt/model/corpus/template changes run the regression evaluation suite.
- Device/firmware changes require hardware-in-loop and staged rollout evidence.
- Production deployment requires explicit product/security/privacy/operations approval where applicable.
- Legacy Databricks or static-credential workflows are not used for Sentinel production.

## Dependencies and validation

- Final GitHub Actions, Azure federated identity, and scanning tool configuration require implementation.

## Relevant Context

### Scope and workflow
- Delivery uses trunk-based development, GitHub Actions, Terraform, federated identity, and gated environments. See [operations architecture](../../infra/docs/architecture/operations.md) §4.

### Architecture and integration points
- Existing [.github/workflows/ci.yml](../../.github/workflows/ci.yml) runs lint/tests/Terraform fmt; [.github/workflows/cd.yml](../../.github/workflows/cd.yml) and [.github/workflows/infrastructure.yml](../../.github/workflows/infrastructure.yml) contain legacy Databricks/static-secret patterns that must be replaced.

### Security, privacy, and audit controls
- AI evaluation regression gates prompt/model/corpus changes; firmware changes need hardware-in-loop evidence.

### Existing implementation touchpoints
- [pyproject.toml](../../pyproject.toml) — ruff/pytest config; [requirements.txt](../../requirements.txt) — dependency baseline.

### Validation dependencies
- Federated identity setup and scanning toolchain selection.
