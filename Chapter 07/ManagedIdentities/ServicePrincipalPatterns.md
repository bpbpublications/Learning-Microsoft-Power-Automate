# Service Principal Patterns

## Overview

A **service principal** represents an application identity that can be used for non-interactive automation and API access.

Service principals are useful when a workload needs an application identity and the target integration does not use a supported managed identity pattern.

## Required Values

A typical configuration may require:

```text
Tenant ID
Client ID
Client Secret or Certificate
Target Resource or Audience
```

Use placeholders in documentation and source control. Do not store real client secrets or certificate material in GitHub.

## Authentication Pattern

```text
Power Automate / Application
        ↓
Service Principal
        ↓
Microsoft Entra ID
        ↓
Protected Azure Service / API
```

The service principal represents the application in the target identity system. The application then requests access to the protected resource using the permissions assigned to that identity.

## Secret vs Certificate

A service principal can use different credential mechanisms depending on the application and enterprise requirements.

| Credential | Consideration |
|---|---|
| Client Secret | Simple to configure but must be protected and rotated |
| Certificate | Strong credential option with certificate lifecycle management |

Prefer the credential method required by the target architecture and enterprise security policy.

## Recommended Usage

- Use service principals for approved non-interactive production scenarios.
- Prefer certificates over client secrets where appropriate and supported.
- Store client secrets or certificates in Azure Key Vault or another approved secrets-management platform.
- Assign least-privilege permissions.
- Review application permissions regularly.
- Rotate credentials according to enterprise policy.
- Avoid using a highly privileged identity for unrelated workloads.

## Service Principal vs Managed Identity

| Approach | Typical Use | Credential Management |
|---|---|---|
| Managed Identity | Supported Azure workload authentication | No application secret required |
| Service Principal + Secret | Application authentication when required | Secret must be protected and rotated |
| Service Principal + Certificate | Application authentication with certificate | Certificate lifecycle must be managed |

Prefer managed identity when the target architecture supports it and it meets the integration requirements.

## Testing

Validate:

1. Valid tenant and client configuration.
2. Required permissions are granted.
3. Authentication succeeds.
4. The application can access only the intended resource.
5. Access is denied when required permissions are removed.
6. Expired or invalid credentials are handled correctly.

## Common Issues

### Authentication Failure

Check tenant ID, client ID, credential validity, authority, audience or resource, and application permissions.

### Access Denied

Verify that the service principal has the required role or API permission at the correct scope.

### Secret Expired

Rotate the credential using the organization's approved process and validate the consuming automation afterward.

### Permission Is Too Broad

Review role and API assignments and reduce them to the narrowest practical scope.

## Security Practices

- Never commit client secrets, certificates, or tokens.
- Use an approved secrets-management platform.
- Protect credentials in flow run history where applicable.
- Monitor authentication failures and unusual access.
- Coordinate credential rotation with dependent automations.

## Related Resources

- [Managed Identities](README.md)
- [Managed Identity Patterns](ManagedIdentityPatterns.md)
- [OAuth 2.0 Configuration](OAuth2-Configuration.md)
- [Azure Key Vault](../AzureKeyVault/README.md)

## Notes

The exact authentication configuration depends on the Azure service, API, connector, and enterprise identity architecture used by the exercise.