# Deployment Approval

## Overview

Production deployments should follow an approval process appropriate to the business risk and governance model.

## Approval Flow

```text
Release Candidate
      ↓
Testing Complete
      ↓
Approval Review
      ↓
Approved?
  ┌────┴────┐
 Yes        No
  ↓          ↓
Deploy     Remediate
```

## Approval Evidence

Capture appropriate evidence such as:

- Release version
- Change summary
- Test result
- Approver
- Approval date
- Deployment target

## Separation of Duties

Where required by organizational policy, the person who develops a change should not be the only person approving its production deployment.

## Exception Handling

Emergency changes should follow a documented exception process rather than becoming an informal bypass of governance.
