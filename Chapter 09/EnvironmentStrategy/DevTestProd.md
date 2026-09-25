# Development, Test, and Production Environments

## Overview

Separating development, test, and production environments reduces deployment risk and gives each stage a clear purpose.

## Environment Responsibilities

| Environment | Primary Purpose |
|---|---|
| Development | Build and unit test changes |
| Test / QA | Functional and regression testing |
| Production | Run approved business processes |

## Key Principle

Developers should not use production as a development or experimentation environment.

## Promotion

```text
Develop
  ↓
Test
  ↓
Approve
  ↓
Production
```

Each transition should have appropriate validation and access controls.

## Governance

Define:

- Environment owners
- Supported workloads
- Access model
- Deployment process
- Backup and recovery expectations
- Monitoring responsibilities
