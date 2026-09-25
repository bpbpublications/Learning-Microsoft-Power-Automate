# SQL Database Integration

Power Automate can work with relational data for read, insert, update, validation, and downstream processing scenarios.

## Common database types in the chapter

The manuscript discusses SQL Server, Azure SQL, Oracle, PostgreSQL, and MySQL, together with cloud and on-premises integration patterns.

## Integration pattern

```text
Business requirement
        ↓
Data model
        ↓
Connection
        ↓
Query / stored procedure
        ↓
Validate result
        ↓
Process in flow
```

## Design considerations

- Use least-privilege database access.
- Prefer parameterized operations.
- Keep transaction behavior clear.
- Consider duplicate and retry behavior.
- Handle timeouts, locks, permissions, and data constraints.
- Avoid unnecessary database round trips.
- Keep credentials outside flow definitions and source files.

## Resources

- [Database Connectivity](DatabaseConnectivity.md)
- [Connection Strings](ConnectionStrings.md)
- [Stored Procedure Patterns](StoredProcedurePatterns.md)
- [On-Premises Data Gateway](OnPremisesDataGateway.md)
- [Customer Notification Scenario](CustomerNotificationScenario.md)
- [Database Error Handling](DatabaseErrorHandling.md)
