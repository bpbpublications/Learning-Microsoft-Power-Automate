# Python Error Handling

Python components should fail predictably so the calling automation can decide whether to retry, recover, or escalate.

## Pattern

```text
Python operation
      ↓
Success? ── Yes ──→ Return result
   │
   No
   ↓
Handle expected exception
   ↓
Return controlled error
   ↓
Power Automate recovery
```

## Good practice

- Validate inputs before processing.
- Catch expected exceptions.
- Return a predictable error structure where appropriate.
- Provide useful diagnostic information without sensitive values.
- Test missing data, invalid input, dependency failures, and unexpected values.

## Flow-side handling

The Power Automate flow should validate the returned result and define the next step for failure. Do not rely on an unhandled Python exception to communicate business meaning to a flow.
