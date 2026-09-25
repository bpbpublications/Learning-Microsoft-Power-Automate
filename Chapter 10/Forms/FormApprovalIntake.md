# Forms Approval Intake

## Overview

Forms can collect structured requests that Power Automate routes into an approval process.

## Pattern

```text
Form Submission
      ↓
Validate Request
      ↓
Create Approval
      ↓
Approval Decision
      ↓
Update Record
      ↓
Notify Requester
```

## Design Considerations

- Validate required information before approval.
- Identify the correct approver.
- Handle rejection and timeout scenarios.
- Record the final decision.
- Avoid duplicate approval requests.
