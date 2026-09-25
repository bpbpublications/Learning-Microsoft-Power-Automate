# Flow Run History and Monitoring

## Overview

Flow run history is one of the first places to investigate when a cloud flow does not behave as expected.

It helps you review the trigger, actions, inputs, outputs, duration, and failure information for individual runs.

## Monitoring Flow Runs

A typical investigation starts with:

```text
Flow
 ↓
Run History
 ↓
Select Run
 ↓
Review Trigger and Actions
 ↓
Identify Failure or Delay
```

## What to Review

For a failed or unexpected run, review:

- Trigger status
- Trigger inputs and outputs
- Action status
- Action inputs and outputs
- Error messages
- Run duration
- Retry behavior
- The point at which processing stopped

## Failed Runs

When an action fails, start with the first meaningful failure rather than only the final error.

```text
Trigger
  ↓
Action 1 ✓
  ↓
Action 2 ✓
  ↓
Action 3 ✗  ← Investigate
  ↓
Subsequent actions skipped
```

## Performance Review

Use run history to identify flows that consistently take longer than expected.

Look for:

- Long-running actions
- Repeated retries
- Large data operations
- Unnecessary loops
- Slow external services

## Good Monitoring Practice

Define what normal behavior looks like for the flow before investigating an anomaly.

Record useful operational information such as:

- Flow name
- Environment
- Run identifier
- Start and end time
- Outcome
- Error category

## Security

Run history may contain business data and connector responses.

Follow your organization's data-access and retention policies, and avoid exposing secrets in action inputs, outputs, or logging.

## Related Resources

- [Monitoring](README.md)
- [Troubleshooting](../Troubleshooting/README.md)
- [Sharing](../Sharing/README.md)
