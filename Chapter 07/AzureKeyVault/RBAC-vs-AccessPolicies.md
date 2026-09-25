# RBAC vs Access Policies in Azure Key Vault

## Overview

Azure Key Vault supports two access-management approaches: **Azure role-based access control (RBAC)** and **access policies**.

The choice affects how permissions are assigned and governed. For new enterprise designs, use the access model required by the organization's Azure governance standards and the Key Vault configuration used for the solution.

## Access Policies

Access policies are vault-specific permission rules.

A simplified example is:

```text
Identity: Power Automate service principal
Permissions: Get, List secrets
Scope: Individual Key Vault
```

Access policies can be useful in environments that already use this model.

## Azure RBAC

Azure RBAC uses Azure role assignments at supported scopes such as a subscription, resource group, or individual resource.

For Key Vault scenarios, examples include:

```text
Key Vault Reader
Key Vault Secrets User
Key Vault Administrator
```

Choose the role that provides only the permissions required by the automation.

## Comparison

| Area | Access Policies | Azure RBAC |
|---|---|---|
| Permission model | Vault-specific policy entries | Azure role assignments |
| Scope | Key Vault | Azure resource hierarchy and resource |
| Governance | More vault-specific | Aligns with broader Azure governance |
| Least privilege | Can be configured narrowly | Can be configured narrowly with appropriate role and scope |
| Enterprise management | Useful for existing implementations | Often preferred for standardized Azure governance |

## Example Decision

Suppose a new enterprise automation requires read access to secrets in one Key Vault.

A typical RBAC design might be:

```text
Power Automate Identity
        ↓
Key Vault Secrets User
        ↓
Specific Key Vault Scope
```

The exact role should match the operation required by the flow.

## Migration Considerations

Before changing an existing vault from one access model to another:

- Inventory existing applications and identities.
- Identify the permissions currently required.
- Map permissions to appropriate roles or policies.
- Test all consumers in a non-production environment.
- Plan the change to avoid breaking running automations.

## Best Practices

- Follow the organization's approved Azure access model.
- Apply least privilege.
- Assign permissions to workload or service identities rather than individual users where appropriate.
- Avoid granting administrator roles when secret retrieval is the only requirement.
- Review role assignments and policies regularly.
- Separate development, test, and production access.

## Related Resources

- [Azure Key Vault](README.md)
- [Key Vault Architecture](KeyVaultArchitecture.md)
- [Key Vault Connector](KeyVaultConnector.md)

## Notes

This article expands the repository's comparison of access policies and Azure RBAC. Exact roles, scopes, and supported configuration depend on the Azure environment and the Key Vault implementation.