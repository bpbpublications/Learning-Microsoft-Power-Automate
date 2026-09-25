# CyberArk Central Credential Provider Overview

## Overview

The **CyberArk Central Credential Provider (CCP)** enables applications to retrieve credentials from CyberArk through an HTTPS-based interface without embedding the privileged password in the consuming application.

A Power Automate integration can use a custom connector or an intermediary service to request the required account information from CCP.

## Integration Pattern

```text
Power Automate Custom Connector
        ↓
CyberArk CCP Endpoint
        ↓
CyberArk Vault
        ↓
Credential Response
```

The exact endpoint, authentication method, query parameters, and response depend on the CyberArk environment and CCP configuration.

## Example Endpoint

A representative CCP endpoint can look like:

```text
GET https://<CCPServer>/AIMWebService/api/Accounts
```

Do not use a real production URL in source code or documentation examples.

## Example Query Parameters

```text
AppID=PowerAutomateApp
Safe=ProdSafe
Object=SQLAdmin
```

These values identify the consuming application and the CyberArk account to retrieve. Use placeholders or approved sample values in learning material.

## Response Example

A simplified response may contain information such as:

```json
{
  "UserName": "sqladmin",
  "Address": "SQLPROD01",
  "Content": "REPLACE_WITH_SECURE_SECRET"
}
```

The `Content` field represents the protected credential value and should never contain a real password in a repository.

## Power Automate Usage

A cloud flow can follow this pattern:

```text
Trigger
   ↓
Call CCP Through Approved Integration
   ↓
Receive Credential Response
   ↓
Protect Flow Inputs / Outputs
   ↓
Use Credential for Required Operation
   ↓
Do Not Log Secret
```

## Security Considerations

- Use an approved authentication mechanism for the CCP endpoint.
- Grant the consuming identity access only to the required Safe and account.
- Protect the response in Power Automate run history where appropriate.
- Never write the password or secret content to logs.
- Monitor failed and successful retrieval requests.
- Rotate the underlying credential according to enterprise policy.

## Common Issues

### Credential Is Not Returned

Check:

- CCP endpoint availability.
- Application identity and authorization.
- Safe and account permissions.
- Query parameters.
- Network connectivity.

### Authentication Fails

Verify the configured authentication method and the identity used by the connector or intermediary service.

### Secret Appears in Run History

Review Secure Inputs and Secure Outputs settings and verify that downstream actions do not expose the credential.

## Related Resources

- [CyberArk](README.md)
- [Safe Configuration](SafeConfiguration.md)
- [Get Password from CyberArk](GetPasswordFromCyberArk.md)
- [Custom Connector Authentication](../CustomConnectors/AuthenticationOptions.md)

## Notes

This example is a conceptual CCP integration pattern. Exact CyberArk APIs, endpoints, authentication mechanisms, and response structures depend on the CyberArk deployment and enterprise configuration.