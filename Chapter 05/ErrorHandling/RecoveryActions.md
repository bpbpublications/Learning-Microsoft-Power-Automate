# Recovery Actions

## Overview

This example demonstrates recovery and escalation patterns for **Power Automate for desktop**.

When a Desktop Flow encounters a failure, the next step should depend on the type of failure. Some conditions can be recovered automatically, while others require escalation or a controlled stop.

## Scenario

Suppose a legacy application fails to respond after an automation step.

A recovery strategy can attempt to restore the expected state before deciding whether the process should continue.

```text
Failure
   ↓
Identify Condition
   ↓
Recovery Action
   ↓
Verify Recovery
   ├─ Success → Continue
   └─ Failure → Escalate / Stop
```

## Recovery Examples

Common recovery actions may include:

- Reopen an application.
- Bring the required window to the foreground.
- Close an unexpected dialog.
- Return to a known application state.
- Reattempt a failed action when the failure is transient.
- Record the failure and notify support.

The exact actions should match the application and Desktop Flow used in the exercise.

## Exercise

### Step 1 – Identify the Failure State

Determine the application state that indicates the normal path cannot continue.

Examples include:

```text
Unexpected dialog
Application not responding
Target window closed
Temporary connection failure
```

### Step 2 – Define the Recovery Action

Choose an action that can safely return the process to a known state.

For example:

```text
Unexpected Dialog
      ↓
Close Dialog
      ↓
Verify Main Window
```

### Step 3 – Verify Recovery

Do not assume that the recovery action succeeded.

Verify the expected state before continuing.

```text
Recovery Action
      ↓
Check Expected State
      ↓
Valid → Continue
Invalid → Escalate
```

### Step 4 – Escalate When Recovery Fails

When automatic recovery is not successful, capture useful information and move the process to an appropriate exception path.

Possible actions include:

- Log the failure.
- Notify a support team.
- Create an exception record.
- Stop the flow safely.

## Example

Suppose a legacy application displays an unexpected pop-up after saving a transaction.

The flow can use:

```text
Save Transaction
      ↓
Check Expected Result
      ↓
Unexpected Dialog?
   ├─ Yes → Close Dialog
   │          ↓
   │      Verify State
   │          ↓
   │      Continue / Escalate
   └─ No → Continue
```

## Recovery vs Retry

Recovery and retry are related but different.

**Retry** repeats an operation because the failure may be temporary.

**Recovery** attempts to restore the application or process to a valid state before continuing.

For example:

```text
Temporary Timeout
      ↓
Retry Action
```

versus:

```text
Application in Unexpected State
      ↓
Recover Application State
      ↓
Retry or Continue
```

## Testing

### Test 1 – Recovery Succeeds

Create a controlled test condition where the recovery action can restore the expected state.

Expected result:

The flow verifies the recovery and continues.

### Test 2 – Recovery Fails

Use a condition where the recovery action cannot restore the expected state.

Expected result:

The flow records or escalates the failure rather than continuing incorrectly.

### Test 3 – Recovery Must Not Repeat Indefinitely

Verify that repeated recovery attempts have a reasonable limit.

Expected result:

The flow eventually escalates or stops instead of entering an endless recovery loop.

## Common Issues

### Recovery Action Does Not Restore the Application

Check:

- The recovery action matches the actual failure state.
- The application has enough time to respond.
- The expected post-recovery state can be verified.

### Flow Continues After an Unsuccessful Recovery

Add an explicit verification step after recovery.

### Repeated Recovery Causes a Loop

Set a reasonable limit on retries or recovery attempts and use an escalation path after the limit is reached.

## Best Practices

- Recover only from known and safe failure states.
- Verify the application state after recovery.
- Keep recovery actions simple and deterministic.
- Limit repeated recovery attempts.
- Escalate failures that cannot be safely recovered.
- Do not hide failures by continuing without validation.

## Security and Data Considerations

Recovery actions may interact with applications containing sensitive information.

Ensure that:

- Recovery logs do not expose secrets.
- Screenshots or diagnostic files do not contain confidential information.
- Notifications are sent only to authorized recipients.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

- [Error Handling](README.md)
- [Get Last Error](GetLastError.md)
- [Retry Policy Examples](RetryPolicyExamples.md)
- [Try/Catch Pattern](TryCatchPattern.md)

## Notes

The original resource defines this topic as recovery and escalation patterns. This article expands that concept into a practical Desktop Flow approach. fileciteturn108file0L2-L6