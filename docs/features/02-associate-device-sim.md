# User Story: 2 - Associate device and SIM

**As a** hardware/edge operator,
**I want** to associate each wearable with an approved SIM and cellular plan,
**so that** device connectivity and lifecycle ownership can be tracked and controlled.

## Acceptance Criteria

- The platform records device identifier, SIM identifier, carrier/provider, plan, association period, and status.
- A device cannot become active without a valid SIM association or an explicitly approved exception.
- SIM activation, suspension, replacement, and deactivation events are auditable.
- The platform does not store production SIM credentials in source control or logs.
- SIM/provider API failures produce an operational error with retry guidance.

## Dependencies and validation

- Carrier/provider integration capabilities and commercial terms require confirmation.
- Cellular coverage at pilot sites requires field validation.

## Relevant Context

### Scope and workflow
- SIM association underpins the subscription model; the meeting record notes ~100 SIMs at SGD 8/month via SimTel with a 400+ SIM volume-pricing target. See [meeting transcript](../../.github/docs/transcript/Minutes%20of%20Meeting%2021%20July.md).
- Lifecycle: SIM activation → device association → suspension/replacement → deactivation.

### Architecture and integration points
- Carrier/SIM APIs are a third-party trust boundary: dedicated integration identity, scoped permissions, outbound allowlists where practical. See [network security](../../infra/docs/architecture/network-security.md).

### Security, privacy, and audit controls
- No SIM credentials or details in source control or logs; association events are auditable.

### Existing implementation touchpoints
- [hardware/device-config/device-baseline.md](../../hardware/device-config/device-baseline.md) — LTE/4G cellular-only requirement.

### Validation dependencies
- SimTel (or alternate) API capabilities for programmatic SIM lifecycle management.
