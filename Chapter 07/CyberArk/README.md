# CyberArk

## Overview

This folder contains CyberArk credential-management patterns for **Power Automate** and **Power Automate for desktop**.

The examples focus on retrieving privileged credentials securely rather than embedding passwords in automation logic.

## Topics

- CyberArk Safes
- Central Credential Provider (CCP)
- Credential retrieval from Power Automate for desktop
- Custom connector integration for cloud flows
- Authentication options
- Security and operational practices

## Recommended Learning Order

```text
Safe Configuration
       ↓
CCP Overview
       ↓
Retrieve Credential in PAD
       ↓
Custom Connector Authentication
       ↓
Security Practices
```

## Resources

| File | Purpose |
|---|---|
| [Safe Configuration](SafeConfiguration.md) | Understand Safe design, permissions, and least-privilege access |
| [CCP Overview](CCPOverview.md) | Understand how applications retrieve credentials through CyberArk CCP |
| [Get Password from CyberArk](GetPasswordFromCyberArk.md) | Review the Power Automate for desktop credential-retrieval pattern |
| [Security Practices](CyberArkSecurityPractices.md) | Apply operational and security controls |

## Integration Pattern

A typical cloud or desktop automation can follow this pattern:

```text
Power Automate / PAD
        ↓
CyberArk Integration
        ↓
CyberArk Safe / CCP
        ↓
Retrieve Credential
        ↓
Use Credential at Runtime
```

The exact integration depends on the environment and whether the automation runs in the cloud or on a desktop machine.

## Security Principles

- Apply least privilege to Safe permissions.
- Avoid exposing retrieved credentials in logs.
- Protect credential values throughout the automation.
- Prefer strong authentication mechanisms supported by the environment.
- Monitor credential retrieval and authentication failures.
- Coordinate credential rotation with consuming automations.
- Store only placeholder values in this repository.

## Related Resources

- [Chapter 7 – Credential Management](../README.md)
- [Azure Key Vault](../AzureKeyVault/README.md)
- [Custom Connectors](../CustomConnectors/)
- [Managed Identities](../ManagedIdentities/README.md)

## Important Security Note

Never commit real CyberArk passwords, authentication tokens, certificates, API keys, Safe credentials, or other secrets to GitHub. Use approved enterprise secrets-management controls for production.