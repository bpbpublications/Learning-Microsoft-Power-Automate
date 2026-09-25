# Customer Data and Teams Notification Scenario

This end-to-end example from the manuscript demonstrates the same business requirement in cloud flow and Power Automate Desktop.

## Cloud flow

### Scenario

A support agent supplies a Customer ID. The flow retrieves customer details from SQL Server and posts the result to Microsoft Teams.

### Steps

1. **Trigger** — use a manual or Power Apps trigger with `CustomerID` as input.
2. **Query SQL Server** — execute a parameterized query such as:

```sql
SELECT CustomerName, Email, Status
FROM Customers
WHERE CustomerID = @CustomerID;
```

3. **Process the result** — use dynamic content for the returned customer fields.
4. **Notify Teams** — post the customer name, email, and status.
5. **Handle failures** — provide a fallback when no record is found or the query fails.

## Power Automate Desktop

The manuscript uses this sequence:

```text
Open SQL connection
        ↓
Execute SQL statement
        ↓
Get first row from data table
        ↓
Read CustomerName / Email / Status
        ↓
Invoke web service → Teams webhook
```

Example message body:

```json
{
  "text": "Customer Details:\nName: <CustomerName>\nEmail: <Email>\nStatus: <Status>"
}
```

Add PAD error handling around the database and notification operations. On failure, log the error and send an appropriate fallback notification.

## Security notes

- Do not put a real Teams webhook URL in this repository.
- Use parameterized database operations.
- Protect database credentials through approved connection mechanisms.
- Treat customer data as business-sensitive information.
