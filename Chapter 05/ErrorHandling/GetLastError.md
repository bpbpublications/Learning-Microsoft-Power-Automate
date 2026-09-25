# Get Last Error

## Overview

This example demonstrates how to retrieve and process error information in **Power Automate for desktop**.

Capturing error details helps a Desktop Flow diagnose a failure, record useful information, and decide what should happen next.

## Scenario

Suppose an application action fails while a Desktop Flow is running.

Instead of allowing the failure to remain unexplained, the flow can capture the available error information and use it for troubleshooting or recovery.

```text
Action Fails
     ↓
Get Last Error
     ↓
Capture Error Details
     ↓
Log / Recover / Escalate
```

## Exercise

### Step 1 – Create a Test Failure

Create or identify an action that can fail safely during testing.

For example, use a test condition where a required application or UI element is unavailable.

Do not deliberately introduce failures into a production process merely to test error handling.

### Step 2 – Retrieve the Error

Use the error-handling capability available in the Desktop Flow to retrieve the latest error information after the failure.

The exact action and error properties depend on the Power Automate for desktop version and the configuration used in the exercise.

### Step 3 – Inspect the Error Details

Review the available error information and identify details that can help diagnose the failure.

Conceptually:

```text
Error Object
    ↓
Error Message
Error Type / Details
    ↓
Determine Next Action
```

### Step 4 – Use the Error Information

The captured error details can be used to:

- Record a diagnostic message.
- Decide whether recovery is possible.
- Trigger an escalation path.
- Provide context to a downstream process.

## Example

Suppose a UI action cannot find the expected control.

A useful error-handling sequence is:

```text
UI Action
   ↓
Failure
   ↓
Retrieve Last Error
   ↓
Record Diagnostic Information
   ↓
Attempt Recovery or Escalate
```

## Testing

### Test 1 – Successful Action

Run the flow without a failure.

Expected result:

The normal flow completes without invoking the error-handling path.

### Test 2 – Controlled Failure

Use a safe test condition that causes an action to fail.

Expected result:

The error-handling path captures the available error information.

### Test 3 – Recovery Decision

Use the captured error information to determine whether the failure should be retried, recovered, or escalated.

## Common Issues

### No Error Information Is Available

Check:

- The error-handling step executes after the failure.
- The correct error-handling capability is being used.
- The action actually generated an error.

### Error Information Is Too Technical

Capture a concise business-friendly message in addition to technical details when the information will be shown to users or support teams.

### Sensitive Information Appears in the Error

Review what is logged or displayed. Do not expose credentials, tokens, or confidential business data in diagnostic messages.

## Best Practices

- Capture errors close to the point of failure.
- Record useful diagnostic context.
- Keep user-facing messages understandable.
- Avoid logging secrets or unnecessary sensitive data.
- Use the error details to support a clear recovery or escalation decision.

## Related Resources

- [Error Handling](README.md)
- [Recovery Actions](RecoveryActions.md)
- [Retry Policy Examples](RetryPolicyExamples.md)
- [Try/Catch Pattern](TryCatchPattern.md)

## Notes

The original resource defines this topic as retrieving and processing last-error details. This article expands that concept into a practical Desktop Flow example. fileciteturn107file0L2-L6