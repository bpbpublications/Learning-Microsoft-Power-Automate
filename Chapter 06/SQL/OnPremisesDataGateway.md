# On-Premises Data Gateway

Many enterprise databases remain on internal networks. The On-Premises Data Gateway provides a bridge between supported internal data sources and Power Platform services.

## Capabilities highlighted in the chapter

- Run SQL queries against on-premises databases.
- Execute stored procedures.
- Insert, update, or delete rows.
- Pass dynamic values such as CustomerID through parameters.
- Filter or paginate large result sets.

## Common scenarios

### Trigger from data changes

A new employee record in SQL Server can start a flow that provisions an account or notifies HR.

### Legacy integration

An automation can read Oracle data and use the result to send a Teams notification.

## Advanced patterns

### Parameterized queries

Pass dynamic values rather than constructing unsafe SQL strings.

```sql
SELECT *
FROM Employees
WHERE CustomerID = @CustomerID;
```

### Stored procedures

Use stored procedures when business rules belong in the database and the flow should call a controlled database operation.

### Transaction integrity

Keep related updates inside an appropriate transaction so partial updates do not leave the system in an inconsistent state.

## Security

- Use least-privilege database accounts.
- Store credentials in approved connection or credential-management mechanisms.
- Use TLS/SSL where supported and required.
- Rotate credentials according to policy.
- Do not place production connection details in source control.
