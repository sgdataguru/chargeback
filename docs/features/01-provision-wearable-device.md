# User Story: 1 - Provision wearable device identity

**As a** hardware/edge operator,
**I want** to register and provision a vendor wearable with a unique device identity and approved configuration,
**so that** only trusted devices can send Sentinel operational events.

## Acceptance Criteria

- A platform administrator can register device metadata including supplier, model, firmware version, and capability profile.
- The device receives or presents a unique credential supported by the vendor before first operational use.
- The platform records provisioning status, timestamp, initiating principal, and device capability evidence.
- An unregistered, deactivated, or revoked device is rejected at ingress.
- Provisioning and credential events create audit records.
- Vendor-specific integration remains isolated behind the device-management adapter.

## Dependencies and validation

- Vendor wearable SDK/API support for secure identity and provisioning must be confirmed.
- Device secure storage, attestation, and certificate/key rotation support require supplier validation.
- Device certification and supplier commitments must not be assumed.

## Relevant Context

### Scope and workflow
- The wearable is a managed endpoint; the cloud owns tenancy, authorization, and policy decisions. Lifecycle: supplier approval → registration → identity provisioning → SIM association → assignment. See [data flows](../architecture/data-flows.md) (device lifecycle diagram).

### Architecture and integration points
- Vendor-specific provisioning behavior is isolated behind the device-management adapter; Sentinel owns lifecycle state and evidence. See [component specifications](../../infra/docs/architecture/component-specifications.md).
- Ingress validates device identity, credential status, freshness, and nonce/sequence before any workflow. See [security governance](../architecture/security-governance.md).

### Security, privacy, and audit controls
- Provisioning and credential issuance events are auditable; revoked/deactivated devices are rejected at ingress.

### Existing implementation touchpoints
- [hardware/device-config/device-baseline.md](../../hardware/device-config/device-baseline.md) — secure identity, remote provisioning, OTA requirements.
- [src/edge/README.md](../../src/edge/README.md) — placeholder for device protocol adapters and provisioning clients.

### Validation dependencies
- Supplier evidence for certificate/key model, attestation, secure storage, and 3–4 year continuity commitment.
