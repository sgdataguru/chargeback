# User Story: 15 - Manage secrets and workload identity

**As a** platform administrator,
**I want** workloads to use managed identities and centrally governed secrets,
**so that** production credentials are not embedded in source code, devices, or deployment logs.

## Acceptance Criteria

- Application workloads use managed identities or an approved workload-identity mechanism.
- Production secrets and certificates are stored in Azure Key Vault or an approved equivalent.
- CI/CD uses federated identity rather than static cloud credentials.
- Secret access and rotation events are auditable.
- Source-control scans block common credential patterns.
- Break-glass access is restricted, documented, and reviewed.

## Dependencies and validation

- Azure identity model, subscription design, and GitHub federated identity configuration require implementation and review.

## Relevant Context

### Scope and workflow
- All production access uses managed identities and Key Vault; no credentials in source, device config artifacts, or logs. See [security governance](../architecture/security-governance.md) §4.

### Architecture and integration points
- CI/CD uses federated identity; the existing workflows in [.github/workflows/cd.yml](../../.github/workflows/cd.yml) and [.github/workflows/infrastructure.yml](../../.github/workflows/infrastructure.yml) use static `AZURE_CREDENTIALS`/client secrets and must be replaced before production use. See [operations architecture](../../infra/docs/architecture/operations.md) §4.

### Existing implementation touchpoints
- [.env.example](../../.env.example) — local-only placeholders.
- [infra/terraform/versions.tf](../../infra/terraform/versions.tf) — provider baseline.

### Validation dependencies
- Azure subscription and Entra ID federated credential setup.
