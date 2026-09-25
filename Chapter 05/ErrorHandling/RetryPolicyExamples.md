# Retry Policy Examples

## Overview

This example explains common retry strategies used when an automation action may fail because of a temporary condition.

The resource covers three approaches:

- Fixed retry behavior
- Exponential retry behavior
- No retry

The appropriate strategy depends on the type of failure and the operation being performed.

## Scenario

Suppose an automation interacts with a service or application that may temporarily fail or become unavailable.

A retry strategy can give the operation another chance before the flow treats the failure as final.

```text
Action
  ↓
Failure
  ↓
Retry Policy
  ├─ Retry → Try Again
  └─ Stop → Handle Failure
```

## Fixed Retry

A fixed retry strategy waits for a consistent interval between attempts.

Conceptually:

```text
Attempt 1
   ↓
Wait Fixed Interval
   ↓
Attempt 2
   ↓
Wait Fixed Interval
   ↓
Attempt 3
```

This approach can be suitable when the expected recovery time is relatively consistent.

## Exponential Retry

An exponential strategy increases the waiting time between attempts.

Conceptually:

```text
Attempt 1
   ↓
Short Wait
   ↓
Attempt 2
   ↓
Longer Wait
   ↓
Attempt 3
   ↓
Longer Wait Again
```

This can reduce repeated requests when a service needs more time to recover.

## No Retry

Some failures should not be retried.

For example, an invalid business value or a permanently unavailable resource may require correction or escalation instead.

```text
Failure
  ↓
No Retry
  ↓
Handle / Escalate
```

## Comparing the Strategies

| Strategy | Best Use |
|---|---|
| Fixed | Temporary failures with a predictable recovery interval |
| Exponential | Temporary failures where recovery time may increase |
| None | Permanent, invalid, or non-retryable failures |

## Exercise

### Step 1 – Identify the Failure Type

Determine whether the expected failure is transient or permanent.

Examples of potentially transient conditions include:

- Temporary service unavailability.
- Short connection interruptions.
- Temporary application delays.

Examples of conditions that may not benefit from retries include:

- Invalid input.
- Missing required business data.
- Authorization problems that require correction.

### Step 2 – Select a Retry Strategy

Choose the simplest retry strategy that fits the scenario.

```text
Transient + predictable → Fixed
Transient + variable    → Exponential
Permanent / invalid     → None
```

### Step 3 – Define the Limit

Retry behavior should have a reasonable limit.

Avoid retrying indefinitely.

The exact retry count and interval should be determined by the application and business requirements.

### Step 4 – Handle Final Failure

After the configured retry attempts are exhausted, the flow should follow the appropriate error-handling path.

```text
Retries Exhausted
       ↓
Capture Error
       ↓
Recover / Escalate / Stop
```

## Example

Suppose a temporary connection failure occurs while an operation is being performed.

A fixed retry strategy might be represented as:

```text
Operation
   ↓
Failure
   ↓
Wait
   ↓
Retry
   ↓
Success → Continue
Failure → Final Error Handling
```

For a service where recovery may take longer, an exponential strategy may be more suitable.

## Testing

### Test 1 – First Attempt Succeeds

Expected result:

No retry is required.

### Test 2 – Temporary Failure Then Success

Expected result:

The configured retry strategy makes another attempt and the process continues after recovery.

### Test 3 – All Attempts Fail

Expected result:

The configured retry limit is reached and the flow enters the final error-handling path.

### Test 4 – Non-Retryable Failure

Expected result:

The flow handles the failure without unnecessary retries.

## Common Issues

### Too Many Retries

Reduce the retry count or use a non-retry strategy when the failure is not transient.

### Retry Interval Is Too Short

Increase the interval when the target system requires more time to recover.

### Retry Hides a Permanent Problem

Confirm that the failure is actually transient before adding or increasing retries.

## Best Practices

- Retry only transient failures.
- Set a clear maximum retry limit.
- Use exponential behavior when recovery time is unpredictable.
- Avoid retries for invalid input or known permanent failures.
- Log the final failure after retries are exhausted.
- Consider the business impact of repeating an action.

## Important Consideration: Duplicate Operations

Retries can be risky for actions that are not idempotent.

For example, repeating an operation that creates a transaction may create duplicates if the first attempt actually succeeded but the response was lost.

Before enabling retries, consider whether repeating the action is safe.

## Related Resources

- [Error Handling](README.md)
- [Get Last Error](GetLastError.md)
- [Recovery Actions](RecoveryActions.md)
- [Try/Catch Pattern](TryCatchPattern.md)

## Notes

The original resource defines this topic as fixed, exponential, and no-retry policies. This article expands those strategies into practical examples and decision guidance. fileciteturn109file0L2-L6