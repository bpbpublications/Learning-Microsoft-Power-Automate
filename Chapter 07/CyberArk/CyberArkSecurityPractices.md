# CyberArk Security Practices

## Overview

Secure CyberArk integration requires controls across access, authentication, credential retrieval, monitoring, rotation, and recovery.

## Recommended Practices

- Use least privilege for Safe permissions.
- Prefer certificate-based authentication where supported by the integration architecture.
- Use API key or OAuth only where suitable and governed.
- Monitor CCP usage, authentication failures, and retrieval failures.
- Rotate credentials according to enterprise policy.
- Coordinate password rotation with Power Automate retry and validation patterns.
- Review Safe membership regularly.
- Keep production secrets and certificate material outside source control.

## Operational Controls

```text
Monitor CCP health
      ↓
Track certificate expiry
      ↓
Review Safe membership
      ↓
Audit credential retrievals
      ↓
Validate rotation success
      ↓
Review failures and exceptions
```

## Credential Protection

Retrieved credentials should be treated as sensitive data throughout the automation.

Avoid:

- Writing passwords to logs.
- Including secrets in screenshots.
- Sending credentials in notifications.
- Saving credentials to ordinary text or CSV files.
- Committing credentials to GitHub.

## Access Review

Periodically review:

- Application identities.
- Safe membership.
- Account permissions.
- Connector authentication configuration.
- Certificate and API-key lifecycle.

Remove permissions that are no longer required.

## Rotation Coordination

Credential rotation should be coordinated with consuming automations.

A safe sequence is:

```text
Create / Rotate Credential
        ↓
Validate Credential
        ↓
Update or Refresh Consumer
        ↓
Run Smoke Test
        ↓
Monitor
        ↓
Retire Previous Credential
```

## Incident Handling

When a credential or integration is suspected to be compromised:

1. Restrict or disable the affected credential according to enterprise procedures.
2. Investigate access and retrieval activity.
3. Rotate the affected credential.
4. Validate all consuming automations.
5. Restore service using the approved recovery process.

## Notes

The exact CyberArk security controls depend on the enterprise deployment, authentication architecture, and governance model. These examples provide implementation guidance for the Chapter 7 exercises and should be adapted to the organization's approved security standards.