# Console Logging

## Overview

This example demonstrates how to use the **Log message** action in Power Automate for desktop to record useful runtime information during a flow execution.

Console-style logging is useful for development and troubleshooting because it provides a simple way to observe what the Desktop Flow is doing.

## Scenario

Suppose a Desktop Flow processes several steps and the developer needs visibility into the current stage.

A simple logging pattern is:

```text
Start Flow
   ↓
Log: Flow Started
   ↓
Process Data
   ↓
Log: Data Processed
   ↓
Complete
```

## Exercise

### Step 1 – Add a Log Message Action

Add the **Log message** action at an important point in the Desktop Flow.

Use a meaningful message that explains what the flow is doing.

For example:

```text
Starting invoice processing
```

### Step 2 – Log Business Milestones

Add messages around important processing stages.

For example:

```text
Invoice received
Invoice data extracted
Invoice validated
Invoice submitted
Invoice processing completed
```

### Step 3 – Include Runtime Information

Where useful, include variable values in the log message.

For example:

```text
Processing invoice: %InvoiceNumber%
```

Only include values that are appropriate for the log output.

## Example

A simple execution sequence could be:

```text
Log: Flow Started
      ↓
Read Invoice
      ↓
Log: Invoice Read
      ↓
Validate Invoice
      ↓
Log: Validation Completed
      ↓
Submit Invoice
      ↓
Log: Flow Completed
```

## Logging Errors

Log useful information when an error is detected.

For example:

```text
Status: Error
Message: Invoice validation failed
```

Pair the message with the error-handling approach used by the solution when more detailed diagnostics are required.

## Testing

### Test 1 – Normal Execution

Run the Desktop Flow successfully.

Expected result:

The configured log messages are written at the expected processing stages.

### Test 2 – Failure Path

Introduce a test failure.

Expected result:

The appropriate error-related log message is produced and the flow handles the failure according to its error-handling design.

### Test 3 – Runtime Variable

Include a non-sensitive runtime value in a message.

Expected result:

The log output contains the expected value.

## Common Issues

### Message Is Not Useful

Replace generic messages such as:

```text
Step completed
```

with more informative messages such as:

```text
Invoice validation completed for transaction INV-1001
```

### Too Many Messages

Avoid logging every low-level action. Focus on milestones, state changes, warnings, and errors that help with troubleshooting.

### Sensitive Data Appears in Logs

Review the message and any inserted variables. Do not log passwords, tokens, credentials, or unnecessary personal or confidential information.

## Best Practices

- Use clear and consistent messages.
- Log important business and technical milestones.
- Include a transaction or correlation identifier where useful.
- Keep messages concise.
- Avoid excessive logging.
- Do not log secrets or sensitive values.
- Combine console logging with structured or centralized logging when production monitoring requires it.

## When to Use Console Logging

Console-style messages are most useful for:

- Development.
- Testing.
- Troubleshooting.
- Understanding flow progress.

For long-term production monitoring, consider structured file logging or centralized telemetry.

## Related Resources

- [Logging](README.md)
- [CSV Logging](CSVLogging.md)
- [Application Insights](AppInsights.md)
- [Error Handling](../ErrorHandling/README.md)

## Notes

The current resource defines this topic as **Log message action usage**. This version expands it into a practical logging exercise.