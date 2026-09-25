# Excel Data Automation

## Overview

Power Automate can work with Excel tables to read, create, update, and summarize business data.

## Typical Pattern

```text
Trigger
  ↓
Read Excel Table
  ↓
Filter / Transform
  ↓
Update or Create Rows
  ↓
Notify / Report
```

## Prerequisites

Use an Excel workbook stored in a supported cloud location and structure business data as a table.

## Best Practices

- Use stable table and column names.
- Validate data types.
- Avoid duplicate records.
- Consider concurrency when multiple flows update the same workbook.
- Keep workbooks appropriately sized for the scenario.

## Testing

Test empty tables, multiple rows, missing values, duplicate keys, and concurrent updates.
