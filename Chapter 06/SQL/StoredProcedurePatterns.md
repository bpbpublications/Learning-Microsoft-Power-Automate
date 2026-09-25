# Stored Procedure Patterns

Stored procedures can encapsulate database logic and provide a controlled interface for Power Automate to execute business operations.

## Pattern

```text
Power Automate
      ↓
Database connector
      ↓
Stored procedure
      ↓
Validate inputs
      ↓
Database operation
      ↓
Predictable result
```

## Good practice

- Use explicit parameters.
- Validate inputs.
- Return predictable results.
- Document expected error conditions.
- Keep transaction behavior clear.
- Consider duplicate and retry behavior.
- Avoid unnecessary database round trips.

## Why use a stored procedure

A stored procedure can keep database-side business rules in one controlled location. This can be useful when several automations or applications need the same operation.

## Security

Use least-privilege permissions and approved connection mechanisms. Never store database passwords or connection strings in source files.
