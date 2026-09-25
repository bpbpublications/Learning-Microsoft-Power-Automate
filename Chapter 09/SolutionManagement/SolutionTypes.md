# Solution Types

## Overview

Power Platform solutions package application components so they can be moved and managed across environments.

## Managed and Unmanaged

| Type | Typical Use |
|---|---|
| Unmanaged | Development and active customization |
| Managed | Controlled downstream deployment |

## Development Pattern

```text
Unmanaged Development
        ↓
Validate
        ↓
Export Managed Package
        ↓
Test / Production
```

## Important Consideration

Choose the solution type according to the environment and ALM strategy. Avoid making direct production customizations that bypass the controlled deployment process.
