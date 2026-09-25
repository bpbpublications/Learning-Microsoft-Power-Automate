# Permission Models for Power Automate

## Overview

Power Automate solutions should provide users with only the access required for their responsibilities.

## Access Areas

Review access to:

- The flow
- Connections
- Data sources
- Environment resources
- Supporting applications

## Least Privilege

Use the smallest practical permission scope.

```text
Business Need
     ↓
Required Access
     ↓
Minimum Permission
     ↓
Periodic Review
```

## Common Access Considerations

Before sharing a flow, determine:

- Who needs to view it.
- Who needs to edit it.
- Who needs to run it.
- Who manages its connections.
- Whether the underlying data source has separate permissions.

## Testing

Verify that:

1. Authorized users can perform their intended task.
2. Users without the required permission cannot perform restricted actions.
3. Connection permissions work as expected.
4. Access remains appropriate after ownership changes.

## Governance

Review permissions periodically and remove access that is no longer required.

Document exceptions for business-critical processes.

## Security

Do not use shared passwords or expose connection secrets to users merely to make a flow work.

## Related Resources

- [Sharing](README.md)
- [Ownership and Co-Ownership](OwnershipAndCoownership.md)
- [Troubleshooting](../Troubleshooting/README.md)
