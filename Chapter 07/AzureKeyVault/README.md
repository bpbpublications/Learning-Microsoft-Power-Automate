# Azure Key Vault

## Overview

This folder contains Azure Key Vault patterns used in Chapter 7 to help Power Automate solutions retrieve and manage sensitive values without hardcoding credentials in flows.

## Topics

- Secrets, keys, and certificates
- Azure Key Vault architecture
- RBAC versus access policies
- Azure Key Vault connector in Power Automate
- Secure inputs and outputs
- Secret rotation and versioning
- Blue-green secret rotation pattern

## Recommended Learning Order

```text
Key Vault Architecture
        ↓
RBAC vs Access Policies
        ↓
Key Vault Connector
        ↓
Secret Rotation
        ↓
Blue-Green Rotation
```

Start with the architecture and access model, then move to connector usage and credential-rotation patterns.

## Resources

| File | Purpose |
|---|---|
| [Key Vault Architecture](KeyVaultArchitecture.md) | Understand Key Vault objects and the Power Automate integration pattern |
| [RBAC vs Access Policies](RBAC-vs-AccessPolicies.md) | Compare Key Vault access-management models |
| [Key Vault Connector](KeyVaultConnector.md) | Review common connector operations and secure secret usage |
| [Secret Rotation](SecretRotation.md) | Implement a controlled secret-rotation lifecycle |
| [Blue-Green Rotation](BlueGreenRotation.md) | Use two valid secret versions during transition and rollback |

## Core Security Principles

A secure implementation should:

- Avoid hardcoding credentials in flow definitions.
- Use least-privilege access.
- Protect secret values in flow run history with Secure Inputs and Secure Outputs where appropriate.
- Prefer managed, service, or workload identities where supported by the architecture.
- Rotate credentials periodically and validate the replacement before retiring the previous version.
- Monitor access and rotation activity.

## Secret Lifecycle

```text
Create
  ↓
Store in Key Vault
  ↓
Retrieve at Runtime
  ↓
Use Securely
  ↓
Rotate
  ↓
Validate
  ↓
Retire Previous Version
```

## Related Resources

- [Chapter 7 – Credential Management, Key Vault and CyberArk](../README.md)
- [Secret Rotation](SecretRotation.md)
- [Blue-Green Rotation](BlueGreenRotation.md)

## Notes

These resources are intended to accompany the Azure Key Vault section of Chapter 7 in *Learning Microsoft Power Automate*.

Exact connector operations, authentication options, roles, and Azure features can vary by environment and product version. Use the implementation and configuration described in the book as the primary reference for the exercises.