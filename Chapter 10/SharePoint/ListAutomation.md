# SharePoint List Automation

## Overview

SharePoint lists are commonly used as structured business data sources for Power Automate.

## Typical Pattern

```text
Create / Update Item
       ↓
Trigger Flow
       ↓
Validate Data
       ↓
Business Action
       ↓
Update Status
```

## Common Scenarios

- Notify users when an item is created.
- Route approvals.
- Update related records.
- Maintain status fields.
- Create recurring summaries.

## Best Practices

- Define clear columns and data types.
- Validate required values.
- Avoid unnecessary repeated list queries.
- Use appropriate permissions.
- Design for duplicate and concurrency scenarios.
