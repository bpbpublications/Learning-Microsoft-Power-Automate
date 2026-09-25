# Application Insights Telemetry

## Overview

This example introduces **Application Insights telemetry** as a centralized monitoring option for automation solutions.

Centralized telemetry can help collect and analyze execution information across multiple machines, processes, or automation components.

> **Important:** The exact integration approach depends on the Power Automate for desktop solution architecture and the Azure services available in the target environment. This article focuses on the telemetry concept rather than prescribing a single implementation.

## Scenario

Suppose a production automation runs on multiple machines and the support team needs a central view of important execution events.

A centralized telemetry pattern can be represented as:

```text
Desktop Flow
      ↓
Telemetry Event
      ↓
Central Monitoring Platform
      ↓
Query / Dashboard / Alert
```

## What Application Insights Provides

Application Insights is an Azure monitoring capability that can collect and analyze telemetry from applications and services.

For an automation solution, useful telemetry may include:

- Execution status
- Processing duration
- Transaction or correlation identifier
- Important business milestones
- Exceptions and error context
- Dependency or external-service information where applicable

The exact telemetry fields depend on how the automation is instrumented.

## Exercise

### Step 1 – Define the Events to Monitor

Identify the events that are useful for support and operations.

For example:

```text
Flow Started
Invoice Received
Invoice Processed
Invoice Failed
Flow Completed
```

### Step 2 – Define a Common Event Structure

Use a consistent structure for telemetry events.

For example:

```text
Timestamp
ProcessName
TransactionId
EventName
Status
Message
DurationMs
```

Not every event needs every field, but the structure should be consistent enough to support analysis.

### Step 3 – Send Telemetry

Implement the telemetry mechanism used by the solution to send relevant execution information to the centralized monitoring platform.

The exact Power Automate for desktop actions, Azure configuration, and integration method should follow the implementation used in the chapter exercise.

### Step 4 – Review Telemetry

Use the monitoring platform to inspect the collected events.

Conceptually:

```text
Automation Execution
       ↓
Telemetry
       ↓
Central Store
       ↓
Query / Dashboard
```

## Example Event

A successful transaction might produce telemetry similar to:

```text
ProcessName: Invoice Processing
TransactionId: INV-1001
EventName: Invoice Processed
Status: Success
DurationMs: 4200
Message: Invoice processed successfully
```

## Monitoring and Troubleshooting

Centralized telemetry can help answer questions such as:

- How many executions completed successfully?
- Which transactions failed?
- Which step took the most time?
- Are failures concentrated on a particular machine or process?
- Are execution times increasing over time?

## Testing

### Test 1 – Successful Execution

Run the automation successfully.

Expected result:

A corresponding telemetry event is available for the expected execution milestone.

### Test 2 – Failed Execution

Run a scenario that produces an error.

Expected result:

The failure information is captured according to the configured telemetry design.

### Test 3 – Multiple Transactions

Run multiple transactions with different identifiers.

Expected result:

The events can be associated with the correct transaction or execution using the chosen identifiers.

## Best Practices

- Define a consistent telemetry schema.
- Include a correlation or transaction identifier where practical.
- Log meaningful milestones rather than every low-level action.
- Record failures with enough context to support diagnosis.
- Protect sensitive information in telemetry.
- Define retention and access controls.
- Use dashboards and alerts only for signals that need operational attention.

## Common Issues

### Telemetry Is Missing

Check:

- The telemetry integration is configured correctly.
- The automation reaches the event that should generate the telemetry.
- Network and Azure connectivity are available where required.
- The event schema is valid for the target monitoring solution.

### Too Much Telemetry

Reduce low-value events and focus on business milestones, state changes, performance indicators, and errors.

### Sensitive Information Is Logged

Review the fields being sent and remove passwords, tokens, credentials, and unnecessary personal or confidential information.

## Security and Data Considerations

Telemetry can contain business and operational information.

Review:

- Who can access the telemetry data.
- What information is collected.
- How long the data is retained.
- Whether sensitive values are masked or excluded.

Never store passwords, API keys, authentication tokens, or other secrets in telemetry.

## Related Resources

- [Logging](README.md)
- [Error Handling](../ErrorHandling/README.md)
- [CSV Logging](CSVLogging.md)
- [Console Logging](ConsoleLogging.md)

## Notes

The current resource identifies **Application Insights telemetry** as the topic for this article. This version expands that topic into a practical monitoring-oriented example.

Use the current Microsoft and Azure documentation for the exact Application Insights configuration and integration steps required by the target environment.