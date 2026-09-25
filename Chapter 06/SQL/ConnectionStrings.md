# Connection String Examples

The manuscript gives representative connection-string formats for different database technologies.

> These are examples only. Do not copy real credentials into source control. Use the approved connection mechanism for your environment.

## SQL Server via OLE DB

```text
Provider=SQLOLEDB;Data Source=MyServer;Initial Catalog=MyDatabase;User Id=<username>;Password=<password>;
```

## Oracle via ODBC DSN

```text
DSN=MyOracleDSN;Uid=<username>;Pwd=<password>;
```

## Access / Excel file

```text
Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Data\MyDatabase.accdb;
```

## Production guidance

- Prefer approved connection objects and managed identity or other supported identity mechanisms where available.
- Use least privilege.
- Protect credentials and rotate them according to organizational policy.
- Use encrypted connections such as TLS where supported and required.
- Keep environment-specific values outside reusable source files.
