# Managed Identity Patterns

## Overview

Managed identities allow supported Azure resources to authenticate to Azure services without storing a client secret in application configuration.

The key benefit is that the Azure platform manages the identity credential lifecycle instead of requiring the application to store a password or client secret.

## System-Assigned Managed Identity

A system-assigned identity is tied to the lifecycle of the Azure resource that owns it.

```text
Azure Resource
     ↓
System-Assigned Managed Identity
     ↓
Role Assignment on Target Resource
```

This is useful when the identity should exist only with a specific Azure resource.

If the Azure resource is deleted, its system-assigned identity is also removed.

## User-Assigned Managed Identity

A user-assigned identity is a separate Azure resource that can be assigned to multiple supported resources.

```text
User-Assigned Identity
        ↓
  ┌─────┼─────┐
  ↓     ↓     ↓
Resource A  Resource B  Resource C
```

This can be useful when multiple workloads need a reusable identity and centralized governance model.

## Choosing Between Them

| Identity Type | Lifecycle | Typical Use |
|---|---|---|
| System-assigned | Tied to one Azure resource | Single-resource workload |
| User-assigned | Independent resource | Reusable identity across supported resources |

Choose based on workload lifecycle, reuse requirements, and governance needs.

## Power Automate Integration Pattern

A common architecture can place an Azure service between Power Automate and a protected Azure resource:

```text
Power Automate Flow
    ↓
HTTP / Approved Integration
    ↓
Azure Function or Supported Azure Resource
    ↓
Managed Identity
    ↓
Azure Key Vault / Protected Service
```

The exact pattern depends on the Power Automate connector, Azure resource, and authentication capabilities available in the environment.

## Example: Key Vault Access

Conceptually, an Azure workload using a managed identity can retrieve a secret without storing a client secret in application configuration:

```text
Azure Workload
      ↓
Managed Identity
      ↓
Key Vault Role Assignment
      ↓
Secret Access
```

The managed identity must have the appropriate permissions on the target resource.

## Security Principles

- Grant only the permissions required by the workload.
- Use the narrowest practical scope for role assignments.
- Avoid broad subscription-level access when a narrower scope is sufficient.
- Review role assignments regularly.
- Remove unused identity assignments.
- Monitor authentication and authorization failures.
- Do not use managed identity as a reason to grant excessive access.

## Testing

Validate that:

1. The identity is enabled or assigned correctly.
2. The target resource grants the required role.
3. The calling workload can authenticate.
4. The required operation succeeds.
5. Access is denied when the required role is removed.

## Troubleshooting

### Authentication Fails

Check:

- The managed identity is enabled or assigned.
- The calling resource supports the identity pattern.
- The target service supports managed identity authentication.
- The workload is using the expected identity.

### Access Denied

Check the role assignment and its scope on the target resource.

### Multiple Identities Are Available

For user-assigned identities, verify that the workload is explicitly configured to use the intended identity when multiple identities are assigned.

## Managed Identity vs Stored Credential

| Approach | Credential Storage | Typical Advantage |
|---|---|---|
| Managed Identity | No application client secret required | Reduces secret-management overhead |
| Service Principal Secret | Secret must be protected and rotated | Works for application identities where required |
| Certificate-Based Identity | Certificate lifecycle required | Strong credential-based application authentication |

Prefer managed identity when the target architecture supports it and it meets the integration requirements.

## Related Resources

- [Managed Identities](README.md)
- [Service Principal Patterns](ServicePrincipalPatterns.md)
- [OAuth 2.0 Configuration](OAuth2-Configuration.md)
- [Azure Key Vault](../AzureKeyVault/README.md)

## Notes

Managed identity support depends on the Azure resource and integration architecture. Use the implementation described in the book for the corresponding exercise.