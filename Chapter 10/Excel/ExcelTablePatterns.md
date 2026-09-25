# Excel Table Patterns

## Overview

Using structured Excel tables makes Power Automate integrations easier to maintain.

## Common Operations

- List rows
- Get a row
- Add a row
- Update a row
- Delete a row when appropriate

## Recommended Pattern

```text
Identify Key
    ↓
Find Row
    ↓
Validate Existing Data
    ↓
Create or Update
    ↓
Confirm Result
```

## Data Quality

Define a stable key for records where possible. Validate required columns before writing data.

## Common Issues

- Workbook or table not found
- Column name changed
- Duplicate records
- Locked or concurrently modified workbook
- Incorrect data type

Document the expected table structure alongside the exercise.
