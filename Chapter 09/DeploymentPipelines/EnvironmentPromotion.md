# Environment Promotion

## Overview

Environment promotion is the controlled movement of a tested solution from one Power Platform environment to another.

## Promotion Path

```text
DEV
 ↓
TEST / QA
 ↓
PROD
```

## Promotion Checklist

Before promotion, verify:

- The solution version is correct.
- Required components are included.
- Dependencies are available in the target environment.
- Connection references are configured.
- Environment variables have appropriate target values.
- Testing has been completed.
- Required approvals are available.

## After Promotion

Validate the deployed solution by checking:

- Flows are enabled as intended.
- Connections work.
- Trigger behavior is correct.
- Key business scenarios complete successfully.
- Monitoring is available.

## Governance

Production deployment should be restricted to authorized users or deployment mechanisms.

## Related Resources

- [Pipeline Overview](PipelineOverview.md)
- [Deployment Validation](DeploymentValidation.md)
- [Release Management](../ReleaseManagement/README.md)
