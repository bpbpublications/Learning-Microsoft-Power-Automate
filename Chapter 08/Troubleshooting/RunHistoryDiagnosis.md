# Diagnosing Flow Failures from Run History

## Overview

Run history provides the evidence needed to diagnose many cloud-flow failures.

## Diagnosis Pattern

```text
Failed Run
   ↓
Find First Meaningful Failure
   ↓
Review Inputs and Outputs
   ↓
Identify Root Cause
   ↓
Correct Configuration or Data
   ↓
Retest
```

## What to Check

Review:

- Trigger result
- Failed action
- Inputs
- Outputs
- Error message
- Retry information
- Dependent actions

## Common Categories

### Authentication

The connection may be expired, unauthorized, or incorrectly configured.

### Permissions

The identity may not have permission to access the target resource.

### Data

Required fields may be missing, malformed, or contain unexpected values.

### Expression

An expression may reference a missing or incorrectly typed value.

### External Service

A downstream service may be unavailable, throttled, or returning an error.

## Retest

After applying a correction, test with representative data and confirm that the original failure no longer occurs.

## Evidence

Record the relevant error category, time, run identifier, and corrective action for recurring production issues.

Do not copy sensitive payloads into tickets or documentation unless they are approved for that purpose.

## Related Resources

- [Troubleshooting](README.md)
- [Flow Run History](../Monitoring/FlowRunHistory.md)
- [Alerts and Notifications](../Monitoring/AlertsAndNotifications.md)
