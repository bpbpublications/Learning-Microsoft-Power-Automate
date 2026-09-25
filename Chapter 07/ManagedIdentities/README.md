# Managed Identities and Service Principals

## Overview

This folder contains identity patterns for secure Power Automate integration with Azure services and enterprise APIs.

The examples distinguish between **managed identities**, **service principals**, and **OAuth 2.0** configuration used when an automation needs application-level authentication.

## Resources

| File | Purpose |
|---|---|
| [Managed Identity Patterns](ManagedIdentityPatterns.md) | Compare system-assigned and user-assigned managed identities |
| [Service Principal Patterns](ServicePrincipalPatterns.md) | Understand application identities for non-interactive automation |
| [OAuth 2.0 Configuration](OAuth2-Configuration.md) | Review OAuth parameters and configuration flow for protected APIs |

## Recommended Learning Order

```text
Managed Identity
       ↓
Service Principal
       ↓
OAuth 2.0
       ↓
Apply Least Privilege
       ↓
Test and Monitor
```

Start with managed identities, then learn when a service principal is required, and finally review OAuth 2.0 configuration for protected APIs.

## Key Concepts

### Managed Identity

Managed identities allow supported Azure resources to authenticate without storing a client secret in application configuration.

There are two common forms:

- **System-assigned** — lifecycle is tied to the Azure resource.
- **User-assigned** — created as a separate Azure resource and reusable by supported resources.

### Service Principal

A service principal represents an application identity that can authenticate to Azure or another protected service.

For production automation, credentials associated with a service principal should be protected and rotated using an approved secrets-management solution.

### OAuth 2.0

OAuth 2.0 is an authorization framework commonly used to obtain access tokens for protected APIs.

The required tenant, client, audience, scopes, and credential configuration depend on the target API and identity architecture.

## Choosing an Identity Pattern

| Requirement | Preferred starting point |
|---|---|
| Supported Azure resource can authenticate without a stored secret | Managed identity |
| Application identity is required for non-interactive access | Service principal |
| Protected API requires token-based authorization | OAuth 2.0 configuration |

The final choice should be based on the target resource, connector capability, security requirements, and enterprise architecture.

## Security Principles

- Assign only the permissions required by the workload.
- Avoid storing client secrets directly in flow definitions.
- Prefer managed identity where the target architecture supports it.
- Protect service-principal credentials in Azure Key Vault or another approved vault.
- Review identity and API permissions regularly.
- Rotate application credentials and certificates according to policy.
- Monitor authentication and authorization failures.
- Never store real credentials in the repository.

## Validation Checklist

Before using an identity configuration in a business process, verify:

- The intended identity is enabled or configured.
- Required permissions are assigned at the narrowest practical scope.
- Authentication succeeds against the target resource.
- Access is denied when required permissions are removed.
- Expired or invalid credentials are handled safely.

## Related Resources

- [Chapter 7 – Credential Management](../README.md)
- [Azure Key Vault](../AzureKeyVault/README.md)
- [CyberArk](../CyberArk/README.md)
- [Custom Connectors](../CustomConnectors/)

## Notes

Authentication capabilities depend on the Azure resource, Power Automate connector, API, and environment. Follow the implementation described in the book for the exercises.