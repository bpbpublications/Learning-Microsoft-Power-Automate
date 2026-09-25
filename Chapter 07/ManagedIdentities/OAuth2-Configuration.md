# OAuth 2.0 Configuration for Power Automate HTTP Connector

## Overview

OAuth 2.0 allows a Power Automate integration to obtain an access token for a protected API instead of sending a username and password directly to the API.

The exact configuration depends on the identity provider, API, tenant, client application, and required permissions.

## Example Parameters

```text
Authority: https://login.microsoftonline.com/<tenant-id>
Tenant ID: <tenant-id>
Client ID: <application-client-id>
Credential: <client-secret-or-certificate>
Audience: https://graph.microsoft.com/
```

These values are placeholders for learning purposes. Never publish real client secrets or certificates.

## Common Use Cases

OAuth 2.0 can be used with scenarios such as:

```text
Microsoft Graph API
Custom APIs protected by Microsoft Entra ID
Dataverse APIs
Azure Management APIs
```

The actual audience/resource and scopes must match the target API.

## Configuration Flow

```text
Register / Configure Application
        ↓
Grant Required API Permissions
        ↓
Configure OAuth 2.0 in Connector / HTTP Integration
        ↓
Authenticate
        ↓
Obtain Access Token
        ↓
Call Protected API
```

## Important OAuth Concepts

| Term | Purpose |
|---|---|
| Tenant ID | Identifies the Microsoft Entra tenant |
| Client ID | Identifies the application registration |
| Client Secret / Certificate | Authenticates the application when required |
| Audience / Resource | Identifies the API the token is intended for |
| Scope / Permission | Defines what the application is allowed to access |
| Access Token | Token presented to the protected API |

## Security Practices

- Use least-privilege API permissions.
- Do not hardcode client secrets in flows or source control.
- Store secrets or certificates in an approved secrets-management solution.
- Prefer certificate-based authentication where appropriate and supported.
- Rotate credentials according to policy.
- Review application permissions regularly.
- Protect tokens and credential-bearing actions in flow history where applicable.

## Common Issues

### Authentication Fails

Check:

- Tenant ID.
- Client ID.
- Authority URL.
- Client credential.
- Audience or resource.
- Required permissions and consent.

### Access Token Is Issued but API Call Fails

Check whether the token contains the permissions required by the target API and whether the correct audience or resource was requested.

### Insufficient Permission

Verify the API permission or scope assigned to the application and whether administrator consent is required by the target environment.

### Credential Expired

Rotate the client credential using the organization's approved process and validate the dependent automation afterward.

## Testing

Test with:

1. Valid application credentials.
2. Insufficient API permissions.
3. Expired or invalid credentials.
4. Incorrect audience or resource.
5. Unauthorized API access.

Confirm both successful and denied access paths.

## Related Resources

- [Managed Identities](README.md)
- [Managed Identity Patterns](ManagedIdentityPatterns.md)
- [Service Principal Patterns](ServicePrincipalPatterns.md)
- [Custom Connector Authentication](../CustomConnectors/AuthenticationOptions.md)

## Notes

OAuth 2.0 settings and supported authentication modes vary by connector, API, Microsoft Entra configuration, and environment. Follow the configuration used in the corresponding Chapter 7 exercise.