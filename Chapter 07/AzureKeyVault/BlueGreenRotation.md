# Blue-Green Secret Rotation Pattern

## Overview

The blue-green secret rotation pattern keeps two valid credential versions available during a controlled transition.

```text
Blue Secret  = Current active secret
Green Secret = Newly rotated secret
```

The approach provides a rollback option while a new secret is validated and promoted.

## Scenario

Consider an automation that depends on a credential stored in Azure Key Vault.

The credential must be rotated without creating an unnecessary outage.

The process can be represented as:

```text
Current Secret (Blue)
        ↓
Create Green Version
        ↓
Validate Green
        ↓
Promote Green
        ↓
Monitor Automation
        ↓
Retire Blue After Validation
```

## Rotation Flow

1. Create the new **green** secret version or replacement credential.
2. Validate the green credential against the target system.
3. Update the consuming automation or application to use the green credential.
4. Monitor execution after the change.
5. Keep the blue credential available during the defined rollback window.
6. Retire the blue credential only after successful validation.

## Why Use Blue-Green Rotation?

The pattern can:

- Reduce service interruption during credential changes.
- Provide a rollback path when validation fails.
- Reduce the risk of changing credentials across multiple consumers simultaneously.
- Make the promotion and retirement stages explicit.

## Validation Strategy

Validation should occur before the new credential becomes the only available version.

A practical sequence is:

```text
Green Created
     ↓
Connectivity / Authentication Test
     ↓
Business Process Test
     ↓
Promote Green
```

The exact validation checks depend on the target application or service.

## Rollback Strategy

If the green credential fails after promotion:

```text
Green Fails
   ↓
Restore Blue
   ↓
Verify Blue
   ↓
Investigate Green
```

Do not retire the previous credential until the defined rollback window has completed.

## Example

Suppose a Power Automate solution currently uses:

```text
Blue = Secret-Version-1
```

A new credential is created:

```text
Green = Secret-Version-2
```

After validation, the consuming process is updated to use version 2.

Version 1 remains available temporarily so that the solution can be rolled back if required.

## Testing

### Test 1 – Successful Rotation

Create and validate a green credential.

Expected result:

```text
Green validated
   ↓
Green promoted
   ↓
Automation succeeds
```

### Test 2 – Validation Failure

Use a new credential that cannot authenticate successfully.

Expected result:

The green credential is not promoted and the blue credential remains active.

### Test 3 – Post-Promotion Failure

Simulate a downstream failure after promotion.

Expected result:

The solution can revert to the blue credential during the rollback window.

## Best Practices

- Define the active and replacement versions clearly.
- Validate the new credential before promotion.
- Keep the previous version available for a controlled rollback window.
- Monitor the consuming automation after promotion.
- Define when the previous version will be retired.
- Record rotation and validation events without logging secret values.

## Security Considerations

Never place actual secret values in documentation, source control, screenshots, or log files.

Use references to secret names or versions rather than exposing the credential itself.

## Related Resources

- [Azure Key Vault](README.md)
- [Secret Rotation](SecretRotation.md)
- [Key Vault Architecture](KeyVaultArchitecture.md)

## Notes

This example expands the repository's blue-green secret rotation concept. The exact versioning and promotion mechanism depends on the Azure Key Vault and consuming application design.