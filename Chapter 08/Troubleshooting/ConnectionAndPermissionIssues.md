# Connection and Permission Issues

## Overview

Authentication and authorization problems are common causes of Power Automate failures.

## Diagnostic Pattern

```text
Failure
 ↓
Check Connection
 ↓
Check Identity
 ↓
Check Permission
 ↓
Check Target Resource
 ↓
Retest
```

## Connection Problems

Check whether:

- The connection is enabled.
- Authentication is still valid.
- The connection points to the expected environment or resource.
- The connector is available to the user or solution.

## Permission Problems

Verify:

- User or service identity.
- Required role or permission.
- Scope of the permission.
- Access to the underlying data source.

## Flow Works for the Owner but Not Another User

Do not assume that sharing the flow automatically grants access to every dependent resource.

Review flow access, connection access, and target-resource permissions separately.

## Security

Do not solve an authorization problem by sharing passwords or secrets. Use supported identity and permission mechanisms.

## Related Resources

- [Troubleshooting](README.md)
- [Permission Models](../Sharing/PermissionModels.md)
- [Connection Sharing](../Sharing/ConnectionSharing.md)
