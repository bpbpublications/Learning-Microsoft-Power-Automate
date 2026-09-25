# CyberArk Custom Connector Authentication Options

## Overview

A Power Automate custom connector can use different authentication models when integrating with CyberArk or an intermediary service.

The correct option depends on the endpoint, enterprise identity model, network architecture, and security requirements.

## API Key Authentication

A custom connector can pass an API key in a header when the target API is designed to use API-key authentication.

```text
Authentication type: API Key
Location: Header
Header name: x-api-key
```

Use API keys only when they are explicitly supported and governed by the target service. Store the key securely and rotate it according to policy.

## OAuth 2.0 Authentication

OAuth 2.0 can be used when the target service is protected by an identity provider.

```text
Authentication type: OAuth 2.0
Authorization URL: <identity-provider-authorization-url>
Token URL: <identity-provider-token-url>
Scopes: <required-scopes>
```

The exact URLs, scopes, and client configuration depend on the identity provider and API.

## Client Certificate Authentication

Some CyberArk integrations may require certificate-based authentication. When the Power Automate custom connector cannot directly satisfy the required certificate flow, an intermediary service can be used.

```text
Power Automate
    ↓
Azure Function / Logic App proxy
    ↓
CyberArk CCP with certificate authentication
```

The intermediary should validate requests, enforce authorization, and avoid returning unnecessary sensitive information.

## Choosing an Authentication Model

| Model | Typical Use | Key Consideration |
|---|---|---|
| API Key | API designed for key-based access | Protect and rotate the key |
| OAuth 2.0 | Identity-provider protected API | Scope access carefully |
| Client Certificate | Certificate-based enterprise integration | Certificate lifecycle and secure storage |

Use the simplest authentication model that meets the security and integration requirements.

## Security Practices

- Never hardcode real API keys, client secrets, or certificates in the repository.
- Use least-privilege scopes and permissions.
- Protect authentication material in an approved secrets-management platform.
- Rotate credentials and certificates according to enterprise policy.
- Log authentication failures without exposing secret material.
- Use TLS for network communication.

## Testing

Test at least:

1. Valid authentication.
2. Invalid or expired credentials.
3. Insufficient permissions.
4. Endpoint unavailable.
5. Unauthorized access attempts.

## Related Resources

- [CyberArk](../CyberArk/README.md)
- [CCP Overview](../CyberArk/CCPOverview.md)
- [Custom Connectors](./)

## Notes

The exact authentication choices available depend on the custom connector configuration, target API, CyberArk deployment, and enterprise identity architecture.