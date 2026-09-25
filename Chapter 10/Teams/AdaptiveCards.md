# Teams Adaptive Cards

## Overview

Adaptive Cards can present structured information and user actions in Teams.

## Typical Pattern

```text
Flow Event
   ↓
Build Card Data
   ↓
Send Adaptive Card
   ↓
User Action
   ↓
Process Response
```

## Common Scenarios

- Approval requests
- Data confirmation
- Task assignment
- Status updates
- Simple interactive forms

## Design Guidance

Keep cards focused on the action the user needs to take. Validate user responses before updating business records.

## Security

Do not put passwords, access tokens, or unnecessary sensitive information in card payloads. Ensure the response is authorized before performing the requested business action.
