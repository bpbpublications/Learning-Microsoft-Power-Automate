# Monitoring, Sharing, and Troubleshooting

## Overview

This folder contains the companion resources for Chapter 8 of *Learning Microsoft Power Automate*.

The chapter focuses on keeping Power Automate solutions observable, shareable, supportable, and easier to troubleshoot in day-to-day operations.

## What You Will Learn

By working through this chapter, you will learn how to:

- Monitor flow executions and identify failures.
- Review run details and operational information.
- Share automation resources with appropriate users and owners.
- Diagnose common configuration, connection, and execution issues.
- Apply a structured troubleshooting process.
- Use operational practices that make support and maintenance easier.

## Chapter Resources

| Folder | Purpose |
|---|---|
| `Monitoring/` | Monitoring and operational-observability concepts |
| `Sharing/` | Sharing, ownership, access, and collaboration concepts |
| `Troubleshooting/` | Diagnosing and resolving common Power Automate issues |
| `CloudFlows/` | Cloud-flow assets associated with the chapter |
| `SampleData/` | Sample files used by chapter exercises |

## Recommended Learning Order

```text
Build / Run Flow
      ↓
Monitor Execution
      ↓
Share with Appropriate Users
      ↓
Troubleshoot Issues
      ↓
Document and Improve
```

Start with monitoring so you can understand what happened during a run. Then review sharing and access considerations before moving into structured troubleshooting.

## Folder Structure

```text
Chapter08-Monitoring-Sharing-Troubleshooting/
├── README.md
├── Monitoring/
│   └── README.md
├── Sharing/
│   └── README.md
├── Troubleshooting/
│   └── README.md
├── CloudFlows/
└── SampleData/
```

The structure shown above reflects the chapter documentation and supporting folders currently committed in the repository.

## Monitoring

Use the `Monitoring/` resources to understand how to observe flow execution, identify failures, and review recurring operational issues.

[Open Monitoring Resources](Monitoring/README.md)

## Sharing

Use the `Sharing/` resources to understand ownership, access, collaboration, and the security considerations involved when an automation is shared with other users.

[Open Sharing Resources](Sharing/README.md)

## Troubleshooting

Use the `Troubleshooting/` resources to follow a consistent process for identifying failing steps, checking inputs and dependencies, applying a fix, and validating the result.

[Open Troubleshooting Resources](Troubleshooting/README.md)

## Prerequisites

Before working through the exercises, make sure you have:

- Access to Microsoft Power Automate.
- The appropriate license for the features used in the chapter.
- Access to any services, connections, or environments required by an exercise.
- Permission to create, run, or share the relevant automation resources.

> **Note:** Licensing and feature availability can change over time. Refer to the latest Microsoft documentation for requirements that apply to your environment.

## Import and Setup

When a chapter exercise includes an importable asset:

1. Review the corresponding section in the book.
2. Download the required asset from this chapter.
3. Configure connections and environment-specific settings.
4. Verify ownership and permissions before sharing.
5. Run the flow and review the result.

> **Important:** Do not commit passwords, API keys, connection secrets, tokens, or other sensitive information to this repository.

## Operational Best Practices

- Monitor important flows regularly.
- Review failed runs and recurring errors.
- Keep ownership and access current.
- Document known issues and resolutions.
- Use least-privilege access where practical.
- Separate troubleshooting from production changes when possible.
- Validate any fix with a controlled test before considering the issue resolved.

## Additional Resources

For current product documentation and learning resources, refer to the official Microsoft Power Automate resources:

- [Microsoft Power Automate documentation](https://learn.microsoft.com/power-automate/)
- [Power Automate learning resources](https://learn.microsoft.com/training/powerplatform/power-automate/)

Microsoft product capabilities, interfaces, and licensing can change over time. Use the latest Microsoft documentation when the current product differs from the version described in the book.

## Related Book Section

Use this repository together with the corresponding sections of Chapter 8 in *Learning Microsoft Power Automate*.

The book provides the concepts and step-by-step guidance, while this repository provides supporting assets and reference material for the exercises.

## Notes

- This README is the entry point for Chapter 8 repository resources.
- Additional assets can be added as the chapter materials are finalized.
- Keep this README synchronized with the actual folder contents as the repository evolves.