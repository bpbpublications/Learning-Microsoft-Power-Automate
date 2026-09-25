# Secret Rotation with Azure Key Vault

## Overview

Secret rotation reduces risk by periodically replacing credentials used by automations and dependent applications.

A well-designed rotation process should change the credential without unnecessarily interrupting the business process.

## Rotation Pattern

```text
Create New Secret / Version
        ↓
Validate New Credential
        ↓
Update Dependent Application or Flow Reference
        ↓
Monitor Execution
        ↓
Retire Previous Version
```

The exact implementation depends on whether the target system supports overlapping credentials, versioned secrets, or another controlled transition mechanism.

## Why Rotate Secrets?

Regular rotation can help reduce the exposure period of compromised or outdated credentials and support organizational security requirements.

Rotation should be treated as a lifecycle process rather than a one-time change.

## Step-by-Step Example

### Step 1 – Create the Replacement

Create the replacement credential or secret version in Azure Key Vault.

Do not place the actual secret value in source control or documentation.

### Step 2 – Validate the Replacement

Verify that the new credential works with the target application or service before making it active for all consumers.

Possible checks include:

- Authentication succeeds.
- Required permissions are available.
- The business operation completes successfully.

### Step 3 – Update the Consumer

Update the consuming automation or application so it retrieves the replacement credential from Key Vault.

Where possible, avoid embedding a version-specific value directly in flow actions.

### Step 4 – Monitor

Monitor the automation after the change.

Look for:

- Authentication failures.
- Increased flow failures.
- Unexpected downstream errors.
- Successful execution of representative transactions.

### Step 5 – Retire the Previous Version

After the defined validation and rollback period, retire the previous credential according to the organization's retention and security policy.

## Event-Driven Rotation

Azure services can be used to signal lifecycle events, such as an approaching secret expiry, so that an automation can begin a rotation process.

A conceptual pattern is:

```text
Expiry / Rotation Event
        ↓
Rotation Workflow
        ↓
Create Replacement
        ↓
Validate
        ↓
Promote
        ↓
Notify / Monitor
```

The exact event source and Power Automate trigger depend on the Azure architecture used by the solution.

## Validation and Rollback

A rotation process should define what happens when the replacement credential fails validation.

```text
New Credential
     ↓
Validation Failed
     ↓
Keep Previous Credential Active
     ↓
Investigate / Correct
```

Where overlapping credentials are supported, a controlled rollback window reduces the risk of service interruption.

## Testing

### Test 1 – Successful Rotation

Create a replacement credential and validate it.

Expected result:

```text
New Credential Valid
       ↓
Consumer Updated
       ↓
Automation Succeeds
```

### Test 2 – Validation Failure

Use an invalid replacement credential in a controlled test environment.

Expected result:

The existing credential remains active and the rotation is not promoted.

### Test 3 – Post-Rotation Monitoring

After successful rotation, run representative transactions.

Expected result:

The automation continues to operate without exposing the credential value.

## Recommended Controls

- Validate the new secret before promotion.
- Keep the previous credential available during the defined transition or rollback period.
- Notify administrators when rotation starts, succeeds, or fails.
- Record the secret version or identifier, rotation timestamp, and validation result without recording the secret value.
- Separate development, test, and production rotation processes.
- Use least-privilege permissions for the identities performing rotation.

## Common Issues

### Rotation Breaks the Automation

Check:

- The replacement credential is valid.
- The target system accepted the new credential.
- The consumer is retrieving the expected secret.
- Required permissions remain unchanged.

### Old Credential Is Retired Too Early

Define a clear rollback or validation window and do not retire the previous credential until the required checks have completed.

### Secret Appears in Logs

Review flow actions, error handling, logging, and run-history settings. Protect sensitive inputs and outputs where appropriate and never log the actual secret value.

## Security Considerations

Never publish real credentials, secret values, access tokens, or confidential connection strings in the repository.

Use sample secret names, versions, and identifiers in documentation instead.

## Related Resources

- [Azure Key Vault](README.md)
- [Key Vault Architecture](KeyVaultArchitecture.md)
- [Key Vault Connector](KeyVaultConnector.md)
- [Blue-Green Rotation](BlueGreenRotation.md)

## Notes

This example expands the repository's secret-rotation lifecycle. The exact rotation trigger, credential versioning, consumer update, and retirement mechanism depend on the Azure environment and target system used in the book exercise.