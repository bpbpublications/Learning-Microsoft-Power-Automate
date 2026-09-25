# Database Connectivity

Database integration depends on the target system, connector availability, environment, and security model.

## Cloud flows

A cloud flow can connect to a supported database, execute a query or stored procedure, validate the returned data, and continue with business actions.

## Power Automate Desktop

The manuscript demonstrates the following pattern:

```text
Open SQL connection
        ↓
Execute SQL statement
        ↓
Get first row from data table
        ↓
Use returned values
```

The connection can use an approved OLE DB or ODBC provider, depending on the database and environment.

## Database operations

Typical operations include:

- Read records.
- Insert records.
- Update records.
- Filter records.
- Validate data.
- Execute stored procedures.

## Security

Use least-privilege accounts and approved connection mechanisms. Do not embed database passwords in flows, scripts, Markdown, or repository files.
