# Office Scripts Basics

## Overview

Office Scripts provide reusable workbook automation logic for Excel on the web.

## Core Concepts

A script can work with workbook objects such as worksheets, ranges, and tables.

Keep scripts focused on one business responsibility.

## Example Pattern

```text
Receive Workbook
      ↓
Read Data
      ↓
Apply Logic
      ↓
Update Workbook
      ↓
Return Result
```

## Best Practices

- Use clear variable and function names.
- Avoid unnecessary hard-coded ranges.
- Validate expected worksheets and tables.
- Keep reusable logic small and testable.
- Document expected inputs and outputs.
