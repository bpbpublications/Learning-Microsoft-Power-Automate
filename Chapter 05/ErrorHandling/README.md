# Error Handling

## Overview

This folder contains practical examples for handling errors in **Power Automate for desktop**.

Effective error handling helps a Desktop Flow identify failures, capture useful diagnostic information, recover when possible, and escalate conditions that cannot be resolved automatically.

## Resources

| File | Purpose |
|---|---|
| [Get Last Error](GetLastError.md) | Capture and process error details |
| [Retry Policy Examples](RetryPolicyExamples.md) | Understand retry strategies and when to use them |
| [Recovery Actions](RecoveryActions.md) | Recover from failures and escalate when required |
| [Try/Catch Pattern](TryCatchPattern.md) | Structure the main path, error path, and cleanup path |

## Recommended Learning Order

```text
Detect Failure
      ↓
Capture Error Details
      ↓
Retry When Appropriate
      ↓
Recover or Escalate
      ↓
Complete / Fail Gracefully
```

A practical learning sequence is:

1. Start with **Get Last Error** to understand failure information.
2. Learn **Retry Policy Examples** to distinguish transient and non-retryable failures.
3. Use **Recovery Actions** to restore a known application state when possible.
4. Apply the **Try/Catch/Finally Pattern** to organize the overall error-handling structure.

## Error Handling Strategy

A practical Desktop Flow should distinguish between different types of failures.

```text
Failure
  ↓
Can it be retried?
  ├─ Yes → Retry
  └─ No
       ↓
Can it be recovered?
  ├─ Yes → Recovery Action
  └─ No → Escalate / Stop
```

Not every error should be retried. A temporary application delay may be retryable, while invalid input may require correction instead.

## Best Practices

- Capture useful error information.
- Retry only transient failures.
- Use timeouts that match the application behavior.
- Verify that recovery actually succeeded.
- Keep recovery steps explicit.
- Avoid hiding failures by continuing without validation.
- Log enough information to support troubleshooting without exposing sensitive data.
- Test successful, failure, recovery, and final-escalation paths.

## Related Resources

- [Chapter 5 – Advanced Power Automate Desktop](../README.md)
- [Advanced UI Automation](../AdvancedUIAutomation/README.md)
- [Dynamic Selectors](../DynamicSelectors/README.md)

## Notes

The examples in this folder are intended to accompany the error-handling section of Chapter 5 in *Learning Microsoft Power Automate*.

Exact actions, error properties, and retry behavior can vary by Power Automate for desktop version and by the application being automated.