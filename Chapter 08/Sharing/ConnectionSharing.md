# Connection Sharing and Dependencies

## Overview

A flow can depend on one or more connections to services such as Microsoft 365, SharePoint, Dataverse, or other connectors.

Connection ownership and access should be considered separately from flow sharing.

## Dependency Pattern

```text
Flow
 ↓
Connection
 ↓
Target Service
 ↓
Data / Action
```

A user may have access to a flow but still be unable to use it correctly if the required connection or target resource is unavailable.

## Review Checklist

For each important flow, document:

- Connector used
- Connection owner or service identity
- Target resource
- Required permissions
- Authentication method
- Recovery or replacement procedure

## Common Problems

### Connection Is Not Authorized

Check the connection status and the permissions granted to the identity used by the connection.

### Connection Owner Leaves the Team

Use an approved transition process and ensure the replacement identity or owner is configured before removing the previous dependency.

### Flow Works for One User but Not Another

Check whether the connection, data source, or underlying permissions differ between users.

## Security

Do not distribute connection credentials. Use supported authentication and enterprise credential-management practices.

## Related Resources

- [Sharing](README.md)
- [Permission Models](PermissionModels.md)
- [Troubleshooting](../Troubleshooting/README.md)
