# Connector, Database, and Python Integration Pattern

A cloud flow can orchestrate multiple integration components while keeping each responsibility separate.

```text
Power Automate Cloud Flow
        ↓
Custom Connector ──→ External API
        ↓
SQL Database
        ↓
Python Processing
        ↓
Business Decision
        ↓
Microsoft 365 / Application Output
```

## Design guidance

Do not combine unrelated responsibilities into one opaque step. Define clear interfaces and validate the output of each integration point.

## Example

1. Trigger from a business request.
2. Validate the input.
3. Call a custom connector to obtain external data.
4. Retrieve authoritative business data from SQL.
5. Send only the required fields to a Python service.
6. Validate the transformed result.
7. Apply business rules.
8. Notify or update the target application.

## Failure handling

Each external dependency should have an identified failure path and appropriate recovery or escalation behavior.
