# Forms to SharePoint Pattern

## Overview

A common Microsoft 365 automation pattern stores Microsoft Forms responses in a SharePoint list for tracking and downstream processing.

## Flow

```text
Microsoft Forms
      ↓
Get Response Details
      ↓
Validate
      ↓
Create SharePoint Item
      ↓
Notify / Continue Process
```

## Data Mapping

Define a clear mapping between form questions and SharePoint columns.

Validate required values before creating the item.

## Testing

Test valid submissions, missing values, special characters, duplicate submissions, and unexpected input.

## Security

Store only the information required for the business process and apply appropriate SharePoint permissions.
