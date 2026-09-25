# Excel and Office Scripts Integration

## Overview

Office Scripts can complement Power Automate when an Excel operation requires reusable workbook logic.

## Integration Pattern

```text
Power Automate
     ↓
Run Office Script
     ↓
Excel Workbook
     ↓
Return Result
     ↓
Continue Flow
```

## Suitable Scenarios

Use a script when workbook logic is easier to maintain as reusable code than as a long sequence of flow actions.

Examples include:

- Formatting a range
- Transforming workbook data
- Applying repeatable calculations
- Preparing a workbook for downstream processing

## Best Practices

- Keep scripts focused.
- Define expected inputs and outputs clearly.
- Validate workbook structure.
- Avoid hard-coded assumptions where possible.
- Test scripts independently before integrating them into a flow.
