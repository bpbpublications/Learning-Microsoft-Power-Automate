# Logging and Telemetry

## Overview

This folder contains practical examples for adding **logging and telemetry** to Power Automate for desktop solutions.

Logging helps an automation record useful execution information so that a developer or support team can understand what happened during a run.

## Resources

| File | Purpose |
|---|---|
| [Console Logging](ConsoleLogging.md) | Record simple runtime messages during flow execution |
| [CSV Logging](CSVLogging.md) | Write structured log information to a CSV file |
| [Application Insights](AppInsights.md) | Understand application telemetry and centralized monitoring concepts |
| [Log Template](LogTemplate.csv) | Sample structure for a CSV-based log |

## Recommended Learning Order

```text
Log Message
     ↓
CSV / File Logging
     ↓
Structured Log Data
     ↓
Centralized Telemetry
```

Start with simple messages, then move to structured logging and centralized telemetry.

## What Should Be Logged?

A useful log entry can include information such as:

- Timestamp
- Flow or process name
- Transaction or business reference
- Step or action name
- Status
- Message
- Error information when applicable
- Execution duration where useful

Keep log entries focused on information that helps with monitoring and troubleshooting.

## Logging Levels

A practical logging approach can distinguish between different kinds of messages:

| Level | Purpose |
|---|---|
| Information | Normal progress or important business milestones |
| Warning | Unexpected condition that did not stop the flow |
| Error | Failure that requires attention |
| Debug | Detailed information useful during development or troubleshooting |

Use the levels consistently across the solution.

## Best Practices

- Log meaningful business and technical events.
- Use consistent field names and message formats.
- Include a correlation or transaction identifier when practical.
- Avoid logging passwords, tokens, credentials, or sensitive personal data.
- Avoid excessive logging that makes troubleshooting harder.
- Record errors with enough context to diagnose the failure.
- Use centralized telemetry when multiple machines or processes need to be monitored.
- Define log retention and access requirements for production solutions.

## Example Execution Log

A structured log might look like:

```text
Timestamp: 2026-08-14 10:15:32
Process: Invoice Processing
TransactionId: INV-1001
Step: Extract Invoice Data
Status: Success
Message: Invoice data extracted successfully
```

The exact fields can be adapted to the solution.

## Security and Data Considerations

Logs can contain sensitive operational information.

Review:

- Who can access logs.
- Where logs are stored.
- How long logs are retained.
- Whether business or personal information is present.

Do not store passwords, API keys, authentication tokens, or other secrets in logs or repository files.

## Related Resources

- [Chapter 5 – Advanced Power Automate Desktop](../README.md)
- [Error Handling](../ErrorHandling/README.md)
- [Dynamic Selectors](../DynamicSelectors/README.md)

## Notes

These resources are intended to accompany the logging and telemetry section of Chapter 5 in *Learning Microsoft Power Automate*.

The exact logging actions, telemetry integration, and available monitoring features can vary by Power Automate for desktop version and by the environment used for the solution.