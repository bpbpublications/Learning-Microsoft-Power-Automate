# Azure Key Vault Connector in Power Automate

## Overview

The Azure Key Vault connector can be used by Power Automate solutions to work with secrets and supported cryptographic operations without placing sensitive values directly in a flow definition.

## Common Operations

Depending on the connector and environment, common operations can include:

```text
Get Secret
Encrypt Data with Key
Decrypt Data with Key
List Keys
```

Use only the operations required by the business scenario and grant the automation identity the minimum required permissions.

## Example Flow Pattern

```text
Trigger
   ↓
Get Secret from Azure Key Vault
   ↓
Protect Secret Output
   ↓
Use Secret in Downstream Action
   ↓
Protect Secret Input Where Appropriate
```

## Example HTTP Request

When a secret is used as an HTTP authorization value, the secret should be retrieved at runtime rather than stored directly in the action configuration.

A representative expression pattern is:

```json
{
  "Authorization": "Bearer @{outputs('Get_secret')?['body/value']}"
}
```

> **Important:** Treat this only as a pattern. The exact output property and action name depend on the connector action and flow implementation.

## Secure Inputs and Outputs

When an action receives or returns a secret, configure **Secure Inputs** or **Secure Outputs** where appropriate.

Apply the protection to the actions that expose the sensitive value so it is not unnecessarily visible in flow run details.

## Authentication Considerations

For production solutions, use an authentication model appropriate for the organization's identity and governance architecture.

Where supported, prefer managed or workload identities and other non-interactive authentication approaches over personal user connections for long-running automation.

## Secret Rotation

The consuming flow should not need to be redesigned whenever a secret is rotated.

A centralized pattern is:

```text
Key Vault
   ↓
Rotated Secret
   ↓
Same Secret Reference
   ↓
Power Automate Flow
```

The exact rotation mechanism depends on the target application and credential design.

## Testing

### Test 1 – Valid Secret

Retrieve a valid secret and use it in the downstream action.

Expected result:

The downstream operation authenticates successfully.

### Test 2 – Missing or Invalid Secret

Test the flow when the secret cannot be retrieved or is no longer valid.

Expected result:

The flow detects the failure and follows the configured error-handling path.

### Test 3 – Rotation

Rotate the secret and rerun the flow.

Expected result:

The flow continues to work without hardcoding a replacement value in the flow definition, provided the secret reference and target system are configured correctly.

## Best Practices

- Retrieve secrets at runtime.
- Use least-privilege access.
- Protect secret-bearing actions with Secure Inputs and Secure Outputs where appropriate.
- Avoid personal user connections for long-running production automation when a managed or workload identity is suitable.
- Centralize credential rotation.
- Never write the secret value to logs or repository files.

## Common Issues

### Access Denied

Check:

- The identity used by the connection.
- Key Vault permissions or RBAC role assignments.
- The selected vault and secret.
- Environment-specific connection configuration.

### Secret Retrieved but Downstream Call Fails

Check:

- The target credential is still valid.
- The secret value is formatted correctly.
- The downstream API expects the same authentication scheme.
- The correct secret version is being used.

### Secret Appears in Run History

Review Secure Inputs and Secure Outputs on the actions handling the value.

## Related Resources

- [Azure Key Vault](README.md)
- [Key Vault Architecture](KeyVaultArchitecture.md)
- [RBAC vs Access Policies](RBAC-vs-AccessPolicies.md)
- [Secret Rotation](SecretRotation.md)
- [Blue-Green Rotation](BlueGreenRotation.md)

## Notes

This resource expands the repository's Azure Key Vault connector pattern. Exact connector operations, authentication options, output schemas, and available features can vary by environment and product version.