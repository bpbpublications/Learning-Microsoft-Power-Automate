# Environment Configuration Data

## Overview

The same solution may require different configuration values in each environment.

Examples include:

- Service URLs
- Site or list names
- Mailbox addresses
- Feature flags
- Business-specific settings

## Configuration Principle

Keep environment-specific values separate from the solution logic whenever the platform design supports it.

```text
Solution Logic
      +
Environment Configuration
      ↓
Target Environment
```

## Deployment Checklist

Before deployment, identify:

- Which values differ between environments.
- Who owns the values.
- Which values are sensitive.
- How values are supplied during deployment.
- How values are validated after deployment.

## Security

Do not store passwords, API keys, or other secrets as ordinary configuration values.

Use appropriate secret-management capabilities for sensitive information.
