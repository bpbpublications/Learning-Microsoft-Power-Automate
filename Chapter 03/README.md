# Building Your First Cloud, Desktop and Business Flows

## Overview

This folder contains the companion resources for Chapter 3 of *Learning Microsoft Power Automate*.

This chapter moves from the concepts introduced in earlier chapters to building practical automation solutions using the three primary flow types covered in the chapter:

* Cloud Flows
* Desktop Flows (Power Automate Desktop)
* Business Process Flows (BPF)

The chapter also demonstrates how cloud and desktop automation can work together to support end-to-end business scenarios.

## What You Will Learn

By completing this chapter, you will learn how to:

* Understand the differences between Cloud Flows and Desktop Flows.
* Choose an appropriate flow type for a business requirement.
* Create Automated, Instant, and Scheduled Flows.
* Configure flow triggers.
* Implement common Power Automate actions.
* Build basic Desktop Flow automations.
* Design Business Process Flows.
* Connect Cloud Flows with Desktop Flows.
* Exchange data between cloud and desktop automations.
* Apply trigger conditions to control when a flow runs.
* Test, troubleshoot, and monitor automations.

## Chapter Resources

The resources for this chapter are organized into the following folders:

| Folder                     | Description                                                     |
| -------------------------- | --------------------------------------------------------------- |
| `AutomatedFlows/`          | Resources for event-driven automated flows.                     |
| `InstantFlows/`            | Resources for manually triggered flows.                         |
| `ScheduledFlows/`          | Resources for scheduled and recurring flows.                    |
| `DesktopFlows/`            | Resources for Power Automate Desktop examples.                  |
| `BusinessProcessFlows/`    | Resources related to Business Process Flows.                    |
| `CloudDesktopIntegration/` | Resources for scenarios combining cloud and desktop automation. |
| `Expressions/`             | Expressions used by the flows demonstrated in this chapter.     |
| `SampleData/`              | Sample files used by the chapter exercises.                     |

## Prerequisites

Before working through the exercises, make sure you have:

### Required

* A Microsoft 365 account.
* Access to Microsoft Power Automate.
* An appropriate Power Automate environment.
* Appropriate licensing for the features used in the exercises.

### Desktop Flow Scenarios

* Windows 10 or Windows 11.
* Power Automate for desktop installed and configured.

### Optional Services

Depending on the exercise, you may also need access to:

* SharePoint Online
* Microsoft Teams
* Microsoft Forms
* Microsoft Planner
* Microsoft Dataverse

> **Note:** Licensing and feature availability can vary by environment and Microsoft plan. Refer to the latest Microsoft documentation when required.

## How to Use These Resources

For the best learning experience:

1. Read the corresponding section of Chapter 3 in *Learning Microsoft Power Automate*.
2. Open the folder associated with the exercise.
3. Review the sample data required by the exercise.
4. Recreate the flow by following the steps in the book.
5. Run and test the automation.
6. Review the run history and troubleshoot any issues.
7. Modify the example to explore how the automation behaves with different inputs.

The book provides the concepts and step-by-step instructions, while this repository provides the supporting files and sample data.

## Repository Structure

```text
Chapter03-Building-Cloud-Desktop-Business-Flows/
│
├── README.md
├── AutomatedFlows/
├── InstantFlows/
├── ScheduledFlows/
├── DesktopFlows/
├── BusinessProcessFlows/
├── CloudDesktopIntegration/
├── Expressions/
└── SampleData/
```

## Automated Flows

Automated Flows run automatically when a defined event occurs.

Examples covered in this chapter include:

* Email Attachment to SharePoint
* Microsoft Forms to Teams Notification
* SharePoint Item Creation

Resources:

```text
AutomatedFlows/
```

## Instant Flows

Instant Flows are manually triggered by a user.

Examples covered in this chapter include:

* Field Technician Status Logging
* On-Demand Data Collection
* Manual Approval Requests

Resources:

```text
InstantFlows/
```

## Scheduled Flows

Scheduled Flows run at predefined times or intervals.

Examples covered in this chapter include:

* Weekly Planner Summary
* Recurring Notifications
* Periodic Reporting

Resources:

```text
ScheduledFlows/
```

## Desktop Flows

Desktop Flows automate Windows applications and user-interface interactions using Power Automate for desktop.

The chapter includes examples such as:

* Launching applications
* UI automation
* Invoice entry into legacy applications
* File processing automation

Resources:

```text
DesktopFlows/
```

## Business Process Flows

Business Process Flows help users follow structured stages within a business process.

Examples covered in this chapter include:

* Lead Qualification
* Multi-Stage Approvals
* Service Management Workflows
* Compliance Tracking

Resources:

```text
BusinessProcessFlows/
```

## Cloud and Desktop Integration

Cloud and Desktop Integration demonstrates hybrid automation scenarios in which a Cloud Flow orchestrates work and a Desktop Flow performs actions on a Windows machine.

Examples covered in this chapter include:

* Email-to-OCR processing
* Cloud-triggered Desktop Automation
* Input and output variables
* File-based data exchange

Resources:

```text
CloudDesktopIntegration/
```

## Key Examples

### Email Attachment to SharePoint

**Trigger**

```text
When a new email arrives
```

**Actions**

```text
Get Attachment
Create File in SharePoint
Send Confirmation
```

This example demonstrates an event-driven Cloud Flow that processes an email attachment and stores the resulting file in SharePoint.

### Field Technician Equipment Logging

**Trigger**

```text
Manually Trigger a Flow
```

**Inputs**

```text
Equipment ID
Status
Notes
```

**Actions**

```text
Create SharePoint Item
Send Confirmation Email
```

This example demonstrates how an Instant Flow can collect user-provided information and store it in SharePoint.

### Weekly Planner Summary

**Trigger**

```text
Recurrence
```

**Example schedule**

```text
Every Friday at 5 PM
```

**Actions**

```text
List Planner Tasks
Build Summary
Send Email
```

This example demonstrates scheduled automation and periodic reporting.

### Invoice Entry Automation

The Desktop Flow example demonstrates a typical legacy-application automation sequence:

```text
Open Application
Read Invoice Data
Enter Data into Legacy System
Save Results
```

The supporting invoice data is available in the `SampleData/` folder.

## Trigger Conditions

This chapter introduces Trigger Conditions to control when a Cloud Flow should run.

For example:

```text
@contains(
    triggerOutputs()?['body/subject'],
    'New Ticket'
)
```

This condition allows the flow to run only when the relevant trigger output contains the text:

```text
New Ticket
```

When using this example, follow the corresponding instructions in the book for adding the expression under the trigger's **Settings → Trigger Conditions**.

## Sample Data

The `SampleData/` folder contains files used by the exercises in this chapter.

| File                 | Purpose                                                                        |
| -------------------- | ------------------------------------------------------------------------------ |
| `InvoiceData.csv`    | Used for Desktop Flow and legacy-application entry examples.                   |
| `TechnicianLogs.csv` | Used for Instant Flow logging and SharePoint integration.                      |
| `PlannerTasks.csv`   | Used for scheduled reporting examples.                                         |
| `sample.txt`         | Used by Power Automate Desktop application and file-processing demonstrations. |

Use the sample files with the corresponding exercises described in the book.

## Testing and Monitoring

This chapter introduces tools and techniques for validating and monitoring automations, including:

* Run History
* Test Mode
* Flow Checker
* Debug options
* Selector validation
* Desktop Flow activity monitoring
* Automation Center

Use these capabilities to identify configuration issues, validate flow behavior, and improve automation reliability.

## Import and Setup

If an exercise provides an exported Power Automate solution or Power Automate Desktop package:

1. Review the corresponding instructions in the book.
2. Import or open the resource in the appropriate environment.
3. Configure required connections and connection references.
4. Verify environment-specific settings.
5. Test the automation before using it with production data.

> **Important:** Never commit passwords, API keys, connection secrets, personal data, or other sensitive information to this repository.

Where a resource is not yet available, follow the exercise instructions in the book to build the example manually.

## Additional Resources

For the latest Microsoft documentation, refer to:

* [Microsoft Power Automate documentation](https://learn.microsoft.com/power-automate/)
* [Power Automate for desktop documentation](https://learn.microsoft.com/power-automate/desktop-flows/)
* [Power Automate training](https://learn.microsoft.com/training/powerplatform/power-automate/)

Microsoft product capabilities, licensing, and user-interface experiences may change over time. Refer to the latest Microsoft documentation when the current product experience differs from the version described in the book.

## Related Chapters

* [Chapter 2 – Expressions and Power Fx](../Chapter02-Expressions-PowerFx/)
* [Chapter 4 – AI Builder and Copilot](../Chapter04-AI-Builder-Copilot/)

## Notes

* Keep resources in their respective chapter folders to maintain a consistent repository structure.
* Additional examples and completed automation packages may be added as the companion resources are finalized.
* The resources in this folder are intended to be used together with Chapter 3 of *Learning Microsoft Power Automate*.

## Author

**Balaji Venugopal**

Companion repository for the BPB Publications book:

**Learning Microsoft Power Automate**
