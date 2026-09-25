# Troubleshooting

## Overview

This folder contains companion resources for diagnosing and resolving common Power Automate issues.

## Resources

| File | Purpose |
|---|---|
| [Run History Diagnosis](RunHistoryDiagnosis.md) | Diagnose failures using run history evidence |
| [Connection and Permission Issues](ConnectionAndPermissionIssues.md) | Investigate authentication and authorization problems |
| [Expression and Data Issues](ExpressionAndDataIssues.md) | Diagnose missing values, data types, and expression failures |
| [Timeout and Performance Issues](TimeoutAndPerformanceIssues.md) | Investigate slow runs, timeouts, retries, and data-volume problems |

## Troubleshooting Flow

```text
Failure Detected
      ↓
Review Run Details
      ↓
Identify First Meaningful Failure
      ↓
Check Data / Connections / Permissions
      ↓
Apply One Controlled Fix
      ↓
Retest
      ↓
Document and Monitor
```

## Best Practices

- Capture enough context to reproduce the issue.
- Check the first meaningful failure rather than only the final error.
- Validate connections, permissions, inputs, and dependencies.
- Avoid changing multiple unrelated components at the same time.
- Test with representative data.
- Document recurring issues and their resolutions.
- Avoid copying sensitive payloads into troubleshooting notes.

## Related Resources

- [Chapter 8](../README.md)
- [Monitoring](../Monitoring/README.md)
- [Sharing](../Sharing/README.md)
