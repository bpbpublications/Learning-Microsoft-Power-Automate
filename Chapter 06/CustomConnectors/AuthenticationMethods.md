# Authentication Methods for Custom Connectors

Authentication determines how Power Automate proves its identity, or the identity of the user, to an external API.

## Choosing a method

| Method | Typical use | Main consideration |
|---|---|---|
| No authentication | Public APIs and controlled prototypes | No access control; rarely suitable for production systems. |
| Basic authentication | Internal or controlled username/password APIs | Static credentials require careful protection and rotation. |
| API key | Simple APIs and usage-controlled services | Key lifecycle and exposure must be managed. |
| OAuth 2.0 | Modern user-consented APIs | Token lifecycle, scopes, and consent add complexity. |
| Microsoft Entra ID OAuth | Microsoft 365 and enterprise scenarios | Application registration, permissions, governance, and organizational identity are involved. |

## No authentication

Use only when the API is intentionally public or when security is handled elsewhere. Do not mistake a public endpoint for an appropriate production integration without reviewing the API's security model.

## Basic authentication

Basic authentication sends a username and password with requests using the API's supported mechanism. The manuscript also demonstrates how Power Automate Desktop can call an API through **Invoke web service** and supply headers such as `Authorization` and `Content-Type`.

## API key

API keys are useful when the API uses a static key for access control or usage tracking. Treat the key as a secret and use approved connection or secret-management mechanisms.

## OAuth 2.0

OAuth 2.0 is suitable when access is token-based and user consent or delegated permissions are required. Pay attention to authorization URLs, token URLs, scopes, token expiry, and consent requirements.

## Microsoft Entra ID OAuth

For enterprise integrations, Entra ID can provide organizational identity, MFA, Conditional Access, application permissions, and governance controls. Follow the application's approved registration and consent process.

## Security principles

- Use least privilege.
- Avoid hard-coded credentials.
- Do not commit secrets to GitHub.
- Use HTTPS for cloud services.
- Review token and key lifecycle requirements.
- Keep authentication configuration appropriate to each environment.
