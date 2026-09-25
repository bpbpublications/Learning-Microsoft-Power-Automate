# OneDrive File Automation

## Overview

OneDrive can be used as a document source or destination in Power Automate scenarios.

## Typical Pattern

```text
File Created / Changed
       ↓
Validate File
       ↓
Process / Move / Copy
       ↓
Update or Notify
```

## Common Scenarios

- Organize files.
- Notify users when files arrive.
- Copy files to controlled locations.
- Process uploaded documents.

## Best Practices

- Define supported file types.
- Handle duplicate names.
- Validate source and destination permissions.
- Avoid unnecessary file copies.
- Protect confidential documents.
