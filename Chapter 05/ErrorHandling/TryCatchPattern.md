# Try/Catch/Finally Pattern

## Overview

This example demonstrates how to structure error handling in a **Power Automate for desktop** flow using a Try/Catch/Finally-style approach.

The goal is to separate the normal processing path from error handling and cleanup activities.

> **Note:** The exact implementation of Try/Catch/Finally behavior depends on the error-handling actions and flow blocks available in the Power Automate for desktop version being used.

## Pattern

A conceptual structure is:

```text
Try
 ↓
Perform Main Automation
 ↓
Success
 ↓
Finally
```

When an error occurs:

```text
Try
 ↓
Failure
 ↓
Catch
 ↓
Capture Error
 ↓
Recover / Escalate
 ↓
Finally
```

## Scenario

Suppose a Desktop Flow opens an application, processes a transaction, and then closes the application.

The flow should:

- Perform the main business operation.
- Capture failures.
- Attempt recovery when appropriate.
- Execute cleanup regardless of success or failure.

## Exercise

### Step 1 – Define the Try Block

Place the main business actions in the protected part of the flow.

For example:

```text
Open Application
      ↓
Read Data
      ↓
Enter Transaction
      ↓
Save Transaction
```

### Step 2 – Define the Catch Path

Configure the error-handling path to execute when the protected actions fail.

The catch path can:

- Retrieve error details.
- Record the failure.
- Attempt recovery.
- Notify support.
- Stop the process safely.

Conceptually:

```text
Main Action Fails
      ↓
Catch
      ↓
Get Error Details
      ↓
Recovery / Escalation
```

### Step 3 – Define the Finally Path

Use the final cleanup path for actions that should occur regardless of whether the main operation succeeds or fails.

Examples include:

- Close an application.
- Release temporary resources.
- Restore the application state.
- Record final status.

Conceptually:

```text
Success ──────┐
              ↓
             Finally
              ↓
          Cleanup

Failure → Catch
              ↓
           Finally
              ↓
           Cleanup
```

## Example

A transaction-processing Desktop Flow might use:

```text
TRY
 ├─ Open Application
 ├─ Read Transaction
 ├─ Enter Data
 └─ Save

CATCH
 ├─ Get Last Error
 ├─ Log Failure
 └─ Attempt Recovery / Escalate

FINALLY
 ├─ Close Application
 └─ Record Final Status
```

## Choosing What Belongs in Each Section

### Try

Put the actions that represent the main business operation here.

### Catch

Put actions that should execute because the main operation failed.

### Finally

Put cleanup or finalization actions that should happen whether the operation succeeds or fails.

## Testing

### Test 1 – Successful Execution

Run the flow without triggering an error.

Expected result:

```text
Try
 ↓
Success
 ↓
Finally
 ↓
Cleanup Complete
```

### Test 2 – Failure in the Try Path

Use a safe test condition that causes one of the protected actions to fail.

Expected result:

```text
Try
 ↓
Failure
 ↓
Catch
 ↓
Finally
```

### Test 3 – Recovery Failure

Allow the catch path to execute but make recovery unsuccessful.

Expected result:

The failure is captured and escalated appropriately, while the final cleanup still executes.

## Common Issues

### Catch Path Does Not Execute

Check that the failure is being handled by the intended error-handling structure and that the protected action is configured to expose the required error condition.

### Finally Cleanup Does Not Occur

Ensure cleanup actions are placed in the appropriate finalization path rather than only on the success route.

### Error Handling Hides the Original Failure

Keep the original error information available for diagnosis before performing recovery or escalation.

## Best Practices

- Keep the main business actions separate from recovery logic.
- Capture useful error details before changing the application state.
- Keep cleanup actions in a consistent finalization path.
- Do not use error handling to silently ignore failures.
- Test success, failure, and recovery-failure paths.
- Keep user-facing messages separate from technical diagnostic information.

## Security and Data Considerations

Error messages, logs, and screenshots can contain sensitive information.

Avoid exposing:

- Passwords.
- Access tokens.
- Customer information.
- Confidential business data.

Use sanitized diagnostic information when sharing errors with support teams.

## Related Resources

- [Error Handling](README.md)
- [Get Last Error](GetLastError.md)
- [Recovery Actions](RecoveryActions.md)
- [Retry Policy Examples](RetryPolicyExamples.md)

## Notes

The original resource defines this topic as **Try/Catch/Finally implementation guidance**. This article expands that concept into a practical Desktop Flow pattern. fileciteturn110file0L2-L6