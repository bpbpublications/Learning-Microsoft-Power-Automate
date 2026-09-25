# CyberArk Safe Configuration

## Overview

A **CyberArk Safe** is a secured container used to manage privileged accounts and credentials.

The Safe design should align with the application, environment, ownership, access requirements, and audit controls defined by the organization.

## Example Safe Design

```text
Safe Name: PA-Prod-Credentials
Purpose: Store credentials used by production Power Automate flows
Access: Least privilege only
Retention: Based on enterprise security policy
Audit: Enabled
```

Use example values such as these in learning material. Do not publish real Safe names or production account information.

## Common Permissions

Depending on the CyberArk implementation, permissions may include:

```text
List accounts
Retrieve accounts
Use accounts
View safe members
Add or update accounts
Initiate password rotation
```

Grant only the permissions required by the integration.

## Recommended Access Model

Prefer group-based access where possible:

```text
Power Automate Application Identity
          ↓
Approved CyberArk Role / Group
          ↓
Required Safe
          ↓
Required Account
```

Avoid broad access to unrelated Safes or accounts.

## Best Practices

- Grant access to groups rather than individuals where practical.
- Review Safe membership regularly.
- Avoid broad entitlements.
- Align Safe names with environment and workload.
- Separate development, test, and production credentials.
- Enable auditing according to enterprise policy.
- Coordinate Safe permissions with the consuming automation identity.

## Validation Checklist

Before integrating a Safe with Power Automate, verify:

- The application identity is approved.
- Only the required Safe is accessible.
- Only the required account can be retrieved or used.
- Retrieval is auditable.
- Rotation requirements are defined.
- No production credential values are stored in documentation or source control.

## Related Resources

- [CyberArk](README.md)
- [CCP Overview](CCPOverview.md)
- [Get Password from CyberArk](GetPasswordFromCyberArk.md)
- [CyberArk Security Practices](CyberArkSecurityPractices.md)

## Notes

Safe names, permissions, roles, and account settings vary by CyberArk deployment. Follow the organization's approved CyberArk governance model for production configuration.