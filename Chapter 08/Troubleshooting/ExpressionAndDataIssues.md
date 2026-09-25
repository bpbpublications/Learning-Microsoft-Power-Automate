# Expression and Data Issues

## Overview

Incorrect data types, missing values, and expression errors can cause a flow to fail even when connections are working correctly.

## Diagnostic Pattern

```text
Action Failure
    ↓
Inspect Input
    ↓
Check Data Type
    ↓
Check Expression
    ↓
Validate Source Data
    ↓
Retest
```

## Common Problems

### Missing Value

A property may not exist or may be empty when the expression expects a value.

### Incorrect Data Type

A number, string, Boolean, array, and object should be handled according to the type expected by the action or expression.

### Unexpected Source Data

Source systems may return blank, duplicate, malformed, or unexpected values.

## Troubleshooting Approach

Use a controlled test value to determine whether the problem is in the expression or the source data.

Compare:

```text
Expected Input
     vs.
Actual Input
```

Then review the expression and its output.

## Prevention

- Validate required data before processing.
- Keep expressions readable.
- Use clear variable names.
- Handle expected empty or exceptional cases.
- Test representative data variations.

## Security

Avoid exposing sensitive source values in logs or troubleshooting documentation.

## Related Resources

- [Troubleshooting](README.md)
- [Run History Diagnosis](RunHistoryDiagnosis.md)
