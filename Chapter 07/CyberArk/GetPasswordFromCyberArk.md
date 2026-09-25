# Get Password from CyberArk in Power Automate Desktop

## Overview

Power Automate for desktop includes an action for retrieving credentials from CyberArk.

This pattern allows a Desktop Flow to obtain a username and password at runtime instead of storing the password directly in the flow.

## Required Inputs

The exact inputs depend on the CyberArk configuration. A representative configuration can include:

```text
Application ID
Safe
Folder
Object
```

## Example Configuration

```text
Application ID: PowerAutomateApp
Safe: ProdSafe
Folder: Root
Object: SQLAdmin
```

Use placeholder values such as these in documentation and training material. Do not use real Safe names or production account details.

## Usage Pattern

```text
Desktop Flow
    ↓
Get password from CyberArk
    ↓
Receive Credential
    ↓
Use Credential at Runtime
    ↓
Complete Operation
    ↓
Clear / Dispose Sensitive Values
```

The retrieved credential may then be used for a required SQL, SAP, API, or legacy-application operation, depending on the business scenario.

## Exercise

### Step 1 – Prepare CyberArk Access

Make sure the CyberArk application identity has the required permission to retrieve the target account.

### Step 2 – Configure the Action

Add the CyberArk credential-retrieval action to the Desktop Flow and provide the required identifying values.

### Step 3 – Use the Credential

Pass the retrieved values to the downstream action that requires authentication.

Avoid copying the password into ordinary text variables or logging actions unless the product and security design explicitly protect the value.

### Step 4 – Complete the Operation

After the protected operation is completed, clear sensitive values where supported and avoid exposing them in screenshots, logs, or output files.

## Example Flow

```text
Start Flow
   ↓
Get password from CyberArk
   ↓
Open target application
   ↓
Sign in with retrieved credential
   ↓
Perform required business operation
   ↓
Log status only
   ↓
End Flow
```

The log should record the outcome of the operation, not the retrieved password.

## Error Handling

Possible failures include:

- CyberArk endpoint unavailable.
- Application ID not authorized.
- Safe or account not accessible.
- Requested credential does not exist.
- Authentication or network failure.

A flow should handle these cases explicitly and report a useful error without exposing the secret.

## Security Notes

- Never write retrieved passwords to logs.
- Use secure handling for sensitive variables and outputs.
- Avoid screenshots containing credential values.
- Clear sensitive variables when they are no longer required.
- Apply least-privilege access in CyberArk.
- Keep production credential configuration outside the GitHub repository.

## Testing

### Test 1 – Valid Credential

Use a valid sample configuration.

Expected result:

The Desktop Flow retrieves the credential and completes the protected operation.

### Test 2 – Unauthorized Access

Use an identity without the required CyberArk permission.

Expected result:

The retrieval fails and the flow handles the error without exposing credential details.

### Test 3 – Account Unavailable

Use a non-existent or unavailable account reference.

Expected result:

The flow reports the retrieval failure and follows its defined exception path.

## Related Resources

- [CyberArk](README.md)
- [CCP Overview](CCPOverview.md)
- [CyberArk Security Practices](CyberArkSecurityPractices.md)
- [Custom Connector Authentication](../CustomConnectors/AuthenticationOptions.md)

## Notes

The exact CyberArk action inputs, authentication method, and available capabilities depend on the CyberArk deployment and Power Automate for desktop version used in the environment.