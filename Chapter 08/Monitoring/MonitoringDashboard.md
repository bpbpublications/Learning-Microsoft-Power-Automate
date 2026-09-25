# Monitoring Dashboard and Operational Metrics

## Overview

A monitoring dashboard provides a consolidated view of automation health and helps support teams identify recurring operational issues.

## Useful Metrics

Depending on the solution, consider tracking:

- Total runs
- Successful runs
- Failed runs
- Failure rate
- Average duration
- Long-running runs
- Retry count
- Trigger volume

## Example

```text
Automation Estate
       ↓
Operational Metrics
       ↓
Dashboard
       ↓
Identify Exceptions
       ↓
Investigate
```

## Designing a Useful Dashboard

Keep the dashboard focused on actionable information.

A useful view can include:

| Metric | Purpose |
|---|---|
| Total Runs | Understand workload |
| Success Rate | Measure reliability |
| Failure Rate | Identify instability |
| Average Duration | Identify performance changes |
| Long-Running Runs | Identify possible bottlenecks |
| Retry Count | Identify transient or recurring issues |

## Operational Thresholds

Define thresholds appropriate to the business process.

For example:

```text
Failure Rate > Threshold
        ↓
Investigate

Duration > Threshold
        ↓
Performance Review
```

Thresholds should be based on actual process behavior rather than arbitrary values.

## Review Cadence

Operational teams may review metrics daily, weekly, or according to the criticality of the automation.

Focus on trends rather than a single isolated run.

## Security and Governance

Dashboards can expose operational and business information.

Apply appropriate access controls and avoid displaying secrets or unnecessary sensitive data.

## Related Resources

- [Monitoring](README.md)
- [Flow Run History](FlowRunHistory.md)
- [Troubleshooting](../Troubleshooting/README.md)
