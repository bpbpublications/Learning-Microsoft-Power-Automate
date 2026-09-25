# Microsoft 365 Integration

## Overview

This chapter contains companion resources for integrating Power Automate with common Microsoft 365 services.

The resources focus on practical automation patterns using Outlook, SharePoint, Excel, Teams, OneDrive, Planner, and Microsoft Forms, with Office Scripts included for advanced Excel automation.

## What You Will Learn

By completing this chapter, you will learn how to:

- Automate email and calendar processes with Outlook.
- Process SharePoint files, lists, and document libraries.
- Read and update Excel data and extend workbook automation with Office Scripts.
- Send Teams notifications, approvals, and collaboration messages.
- Automate files and folders in OneDrive.
- Create and manage Planner tasks.
- Capture structured input from Microsoft Forms and trigger workflows.
- Combine multiple Microsoft 365 services into end-to-end business processes.

## Chapter Structure

```text
Chapter10-Microsoft-365-Integration/
├── README.md
├── Outlook/
├── SharePoint/
├── Excel/
├── Teams/
├── OneDrive/
├── Planner/
├── Forms/
├── OfficeScripts/
└── SampleData/
```

## Recommended Learning Order

```text
Microsoft Forms
      ↓
Outlook
      ↓
SharePoint
      ↓
OneDrive
      ↓
Excel
      ↓
Teams
      ↓
Planner
      ↓
Office Scripts
```

Start with event and input-driven automation, then move into document and data processing before combining services into broader business workflows.

## Typical Microsoft 365 Automation Pattern

```text
Business Event
      ↓
Microsoft 365 Trigger
      ↓
Get Data
      ↓
Validate / Transform
      ↓
Business Logic
      ↓
Create / Update / Notify
      ↓
Record Outcome
```

## Prerequisites

Before working through the exercises, make sure you have:

- Access to Power Automate.
- The Microsoft 365 services required by the specific exercise.
- Appropriate permissions and connections for the services being used.
- An Office environment that supports the Office Scripts exercises where applicable.

> Licensing, connector availability, and feature behavior can vary by environment and product version. Check current Microsoft documentation for the requirements that apply to your environment.

## Security and Governance

Microsoft 365 integrations can process business, customer, and personal information.

- Use least-privilege access.
- Do not store passwords, tokens, API keys, or other secrets in the repository.
- Review connector permissions and connection ownership.
- Protect sensitive information in flow inputs, outputs, and notifications.
- Follow organizational data-retention and sharing policies.

## Related Resources

- [Chapter 9 – Deployment Pipelines and Governance](../Chapter09-Deployment-Pipelines-Governance/README.md)
- [Chapter 8 – Monitoring, Sharing and Troubleshooting](../Chapter08-Monitoring-Sharing-Troubleshooting/README.md)
- [Office Scripts](OfficeScripts/)

## Notes

These resources are intended to accompany the Microsoft 365 integration section of *Learning Microsoft Power Automate*.

The exact connector actions, permissions, interface, and available features may change over time. Use the implementation described in the book together with the latest Microsoft documentation when configuring the exercises.