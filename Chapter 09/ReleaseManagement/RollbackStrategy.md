# Rollback Strategy

## Overview

A rollback strategy defines what the team should do when a deployment causes an unacceptable problem.

## Rollback Decision

```text
Production Validation
       ↓
Issue Detected?
   ┌────┴────┐
  No        Yes
   ↓          ↓
Continue   Assess Impact
              ↓
        Rollback Required?
          ┌───┴───┐
         Yes      No
          ↓        ↓
      Rollback   Remediate
```

## Before Release

Identify:

- The previous known-good version.
- Business impact of rollback.
- Dependencies affected by rollback.
- Data considerations.
- Responsible decision maker.

## After Rollback

Validate the restored version and communicate the outcome.

A rollback should not be considered complete until the business process has been verified.

## Important Consideration

Rolling back application components does not automatically undo data changes created by a release. Data recovery must be planned separately when applicable.
