# Timeout and Performance Issues

## Overview

A flow can fail or appear unreliable when an action or process takes longer than expected.

## Diagnostic Pattern

```text
Slow or Timed-Out Run
        ↓
Review Run Duration
        ↓
Find Slow Action
        ↓
Check Data Volume / Dependency
        ↓
Optimize or Adjust Design
        ↓
Retest
```

## Common Causes

- Large data volumes
- Unnecessary loops
- Repeated connector calls
- Slow external services
- Excessive retries
- Sequential processing where parallel processing is appropriate

## Investigation

Compare normal and abnormal runs.

Look for:

- Actions with unusually long durations
- Sudden increases in data volume
- Repeated retries
- External-service latency

## Design Improvements

Where appropriate:

- Reduce unnecessary data retrieval.
- Filter data as early as practical.
- Avoid unnecessary repeated calls.
- Process only the records required.
- Review retry behavior.

Changes should be tested carefully because reducing calls or changing concurrency can affect business behavior.

## Testing

Test with representative data volumes rather than only a small development sample.

## Related Resources

- [Troubleshooting](README.md)
- [Flow Run History](../Monitoring/FlowRunHistory.md)
- [Monitoring Dashboard](../Monitoring/MonitoringDashboard.md)
