# Azure Key Vault Architecture

## Overview

Azure Key Vault centralizes secrets, keys, and certificates so Power Automate solutions can retrieve sensitive values at runtime instead of storing them inside flow definitions.

## Key Vault Object Types

| Object Type | Purpose |
|---|---|
| Secret | Stores passwords, API keys, connection strings, tokens, and other text-based sensitive values |
| Key | Supports cryptographic operations such as encryption, decryption, signing, and key wrapping |
| Certificate | Manages certificates and their lifecycle for supported scenarios |

## Power Automate Integration Pattern

A common pattern is:

```text
Power Automate Flow
       ↓
Azure Key Vault
       ↓
Retrieve Secret
       ↓
Protect Flow Inputs / Outputs
       ↓
Use Secret in Downstream Action
```

The flow should retrieve the value only when it is needed and avoid embedding the secret directly in the flow definition.

## Example

A flow may retrieve an API credential and use it in an authenticated request:

```text
Trigger
  ↓
Get Secret from Key Vault
  ↓
Secure Outputs
  ↓
Authenticated Action
```

The exact connector operation and authentication model depend on the environment and implementation used in the chapter exercise.

## Access Control

Access to Key Vault should follow least-privilege principles.

For example:

```text
Automation Identity
      ↓
Required Key Vault Role
      ↓
Specific Vault / Scope
```

Avoid granting broad administrative access when the automation only needs to retrieve a secret.

## Secure Inputs and Outputs

When a flow handles secret values, configure **Secure Inputs** and **Secure Outputs** on the relevant actions where appropriate.

This helps reduce the exposure of sensitive values in flow run details.

Security settings should be applied consistently to every action that receives or outputs the secret.

## Monitoring

Monitor access to the Key Vault and review authentication and usage activity according to the organization's governance requirements.

Logging should capture useful operational information without recording the actual secret value.

## Recommended Practice

- Do not hardcode credentials in flow actions.
- Retrieve secrets dynamically at runtime.
- Use least-privilege access.
- Protect sensitive action inputs and outputs.
- Monitor Key Vault access.
- Rotate secrets according to the credential lifecycle.
- Keep secret values out of source control and documentation.

## Related Resources

- [Azure Key Vault](README.md)
- [RBAC vs Access Policies](RBAC-vs-AccessPolicies.md)
- [Key Vault Connector](KeyVaultConnector.md)
- [Secret Rotation](SecretRotation.md)

## Notes

This resource expands the repository's Azure Key Vault architecture concept. The exact authentication, permissions, connector actions, and monitoring configuration depend on the Azure environment and Power Automate implementation used in the book.