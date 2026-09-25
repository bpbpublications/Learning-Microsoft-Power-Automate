# SQL Integration Patterns

Power Automate can use database connectivity to read, create, update, validate, and route structured business data.

## Common operations

- Read records.
- Insert records.
- Update records.
- Filter records.
- Validate data.
- Trigger downstream processing.

## Pattern

```text
Flow
 ↓
Validate input
 ↓
Database operation
 ↓
Validate result
 ↓
Continue / handle error
```

## Example

An invoice flow can validate an invoice number, retrieve the corresponding database record, compare the submitted amount, and route exceptions for review.

## Design considerations

Consider connection security, least privilege, transaction behavior, duplicate handling, timeout behavior, and retry safety.

For on-premises databases, use the approved gateway architecture. For database business rules that should remain centralized, consider a parameterized stored procedure.

## Security

Never commit database passwords, production connection strings, tokens, or production extracts to the repository.
