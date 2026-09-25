# Chapter 7 - Credential Management with Azure Key Vault and CyberArk

This folder contains companion assets for Chapter 7 of *Learning Microsoft Power Automate*.

Chapter 7 focuses on secure credential management for enterprise automation using Azure Key Vault, CyberArk, managed identities, service principals, custom connectors, and automated secret rotation patterns.

## What This Chapter Covers

- Fundamentals of secure secret storage
- Azure Key Vault architecture and access management
- CyberArk Safes and Central Credential Provider patterns
- Managed identities and service principals
- OAuth 2.0 configuration for protected APIs
- Azure Key Vault connector usage in Power Automate
- CyberArk credential retrieval through Power Automate Desktop and custom connectors
- Secret rotation, versioning, validation, rollback, and blue-green rotation patterns

## Folder Structure

```text
Chapter07-Credential-Management-KeyVault-CyberArk
│
├── AzureKeyVault
├── CyberArk
├── CustomConnectors
├── ManagedIdentities
├── SecretRotation
├── SampleData
└── Diagrams
```

## Recommended Learning Order

```text
Secure Credential Fundamentals
          ↓
Azure Key Vault
          ↓
CyberArk
          ↓
Managed Identities / Service Principals
          ↓
Custom Connectors
          ↓
Secret Rotation
          ↓
Validation and Rollback
```

Start with the vault and credential-storage concepts. Then review the identity and connector patterns before studying rotation and recovery.

## Security Principles

A secure implementation should:

- Never hardcode production credentials in flows, scripts, or repository files.
- Apply least-privilege access to vaults, Safes, applications, and connectors.
- Protect sensitive values in flow run history with Secure Inputs and Secure Outputs where appropriate.
- Prefer workload, managed, or service identities over embedded user credentials where supported.
- Rotate credentials according to enterprise policy.
- Validate a replacement credential before retiring the previous version.
- Monitor credential access and rotation activity.

## Related Resources

- [Azure Key Vault](AzureKeyVault/README.md)
- [CyberArk](CyberArk/README.md)
- [Managed Identities](ManagedIdentities/README.md)
- [Custom Connectors](CustomConnectors/)

## Important Security Note

All secrets, passwords, tokens, certificates, and keys in this repository must be placeholders or sample values for learning purposes only. Do not store real credentials in GitHub. Use Azure Key Vault, CyberArk, or another approved secrets-management platform for production automations.

## Notes

Configuration details, authentication options, connector behavior, and Azure or CyberArk features can vary by environment and product version. Follow the implementation and configuration described in the book for the exercises.