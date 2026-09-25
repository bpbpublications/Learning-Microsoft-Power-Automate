# Database Error Handling

Database operations can fail because of connectivity, permissions, validation, timeouts, locking, or data constraints.

## Handling pattern

```text
Database operation
       ↓
Success? ── Yes ──→ Continue
   │
   No
   ↓
Capture error
   ↓
Classify
   ↓
Retry / Recover / Escalate
```

## Retry carefully

Retry only failures that are safe to repeat. Be especially careful with inserts, updates, and other operations that may create duplicate effects.

## Diagnostics

Record useful diagnostic information such as operation name, timestamp, and error category without exposing credentials or sensitive data.

## PAD guidance

For desktop flows, place database actions inside appropriate error-handling scopes. The manuscript's customer example uses error handling to log the failure and send a fallback notification when the database lookup or downstream notification fails.
