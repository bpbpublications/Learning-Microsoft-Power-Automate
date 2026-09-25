# CSV Logging

## Overview

This example demonstrates how to write structured execution information to a **CSV file** from a Power Automate for desktop solution.

CSV logging is useful for lightweight local or file-based tracking when a centralized telemetry platform is not required.

## Scenario

Suppose a Desktop Flow processes multiple business transactions and needs a simple execution log that can be opened in Excel or another analysis tool.

A typical process is:

```text
Desktop Flow
     ↓
Create Log Entry
     ↓
Append to CSV
     ↓
Continue Processing
```

## Log Structure

A consistent structure makes the CSV easier to analyze.

The provided `LogTemplate.csv` can be used as a starting point.

A practical log can contain fields such as:

```text
Timestamp
ProcessName
TransactionId
Step
Status
Message
```

Add only the fields needed by the solution.

## Exercise

### Step 1 – Prepare the Log File

Create or use the log file defined by the exercise.

The repository contains:

```text
LogTemplate.csv
```

Use the template to understand the intended column structure.

### Step 2 – Create the Log Values

Before writing a log entry, populate the values required for the current event.

For example:

```text
Timestamp: 2026-08-14 10:15:32
ProcessName: Invoice Processing
TransactionId: INV-1001
Step: Extract Invoice Data
Status: Success
Message: Invoice data extracted successfully
```

### Step 3 – Write the Entry

Use the appropriate file-handling actions to append the log entry to the CSV file.

The exact action configuration depends on the Power Automate for desktop version and the file-access approach used in the exercise.

### Step 4 – Continue Processing

After the log entry is written, continue with the next automation step.

Conceptually:

```text
Business Action
      ↓
Create Log Entry
      ↓
Append to CSV
      ↓
Next Business Action
```

## Example

A CSV log might contain:

```text
Timestamp,ProcessName,TransactionId,Step,Status,Message
2026-08-14 10:15:32,Invoice Processing,INV-1001,Extract Invoice Data,Success,Invoice data extracted successfully
```

Keep the values consistent so that the file can be filtered and analyzed easily.

## Logging Success and Failure

A CSV log can record both successful and failed events.

Example success:

```text
Status: Success
Message: Invoice processed successfully
```

Example failure:

```text
Status: Error
Message: Invoice amount could not be extracted
```

Error entries should contain enough context to support troubleshooting without exposing sensitive information.

## Testing

### Test 1 – Successful Transaction

Run a successful transaction.

Expected result:

A corresponding row is appended to the CSV log.

### Test 2 – Failed Transaction

Run a scenario that produces an error.

Expected result:

The failure is recorded with an appropriate status and message.

### Test 3 – Multiple Transactions

Process several transactions.

Expected result:

Each transaction creates its own log entry with the correct identifier and status.

## Common Issues

### CSV File Cannot Be Written

Check:

- The file path is correct.
- The folder exists.
- The flow has access to the location.
- Another process is not locking the file.

### Columns Do Not Align

Check that every log entry uses the same column order and delimiter as the template.

### Duplicate or Partial Entries

Check that the append operation is performed once per intended event and that the row is constructed consistently before writing it.

## Best Practices

- Use a consistent column structure.
- Include a transaction or correlation identifier.
- Keep log messages concise.
- Write one well-defined event per row.
- Avoid logging credentials or sensitive data.
- Rotate or archive large log files.
- Avoid using a single CSV file as the primary telemetry store for high-volume production workloads.

## When to Use CSV Logging

CSV logging is suitable when:

- The volume of log events is manageable.
- A simple local or shared-file log is sufficient.
- The log mainly supports development, troubleshooting, or lightweight operations.

For larger or centralized monitoring needs, consider a telemetry or centralized logging solution.

## Security and Data Considerations

CSV files can expose data to anyone who has access to the file location.

Review:

- File permissions.
- Storage location.
- Retention requirements.
- Whether personal or confidential information is included.

Do not store passwords, API keys, authentication tokens, or other secrets in the CSV log.

## Related Resources

- [Logging](README.md)
- [Console Logging](ConsoleLogging.md)
- [Application Insights](AppInsights.md)
- [Log Template](LogTemplate.csv)
- [Error Handling](../ErrorHandling/README.md)

## Notes

The current resource covers writing text to files and CSV logging examples. This version expands that topic into a practical structured-logging exercise.