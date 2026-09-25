# SharePoint Document Library Automation

## Overview

Power Automate can automate document movement, metadata updates, notifications, and approvals in SharePoint libraries.

## Pattern

```text
File Created / Modified
        ↓
Validate Metadata
        ↓
Process File
        ↓
Update Metadata
        ↓
Notify User
```

## Common Scenarios

- Route documents to folders.
- Apply metadata.
- Start document approvals.
- Notify owners when documents change.
- Archive completed documents.

## Best Practices

- Define naming conventions.
- Validate file types and metadata.
- Avoid unnecessary file moves.
- Handle duplicate names explicitly.
- Apply least-privilege access.
