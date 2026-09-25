# Connection References

## Overview

Connection references help solutions separate flow logic from the connections used by actions.

## Why They Matter

A flow may be promoted across environments while the target environment uses different connection instances.

The deployment process should therefore account for connection references explicitly.

## Deployment Pattern

```text
Development Connection
        ↓
Solution Reference
        ↓
Test Connection
        ↓
Production Connection
```

## Checklist

Before deployment:

- Identify all connection references.
- Confirm the target connection exists.
- Verify the target user or service identity has the required permissions.
- Test the connection after deployment.

## Security

Use dedicated service identities or approved connection ownership models where appropriate. Never distribute connection credentials through source control.
