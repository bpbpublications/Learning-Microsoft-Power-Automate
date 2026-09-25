# Weekly Planner Summary

## Overview

This example demonstrates how to build a **Scheduled Cloud Flow** that runs every Friday and sends a summary of completed Microsoft Planner tasks by email.

The scenario shows how scheduled automation can be used to collect task information and provide a recurring status update without requiring a user to start the flow manually.

## Business Scenario

A team uses Microsoft Planner to manage its weekly work.

At the end of each week, a summary of completed tasks is useful for reviewing progress and communicating the team's status.

Instead of manually preparing the summary, Power Automate can run the process automatically every Friday.

The basic process is:

```text
Scheduled Trigger
       ↓
Retrieve Planner Tasks
       ↓
Identify Completed Tasks
       ↓
Build Summary
       ↓
Send Email
```

## Flow Type

**Scheduled Cloud Flow**

The flow runs automatically according to a defined schedule.

The current example is defined to run:

```text
Every Friday
```

The exact execution time should be configured according to the exercise requirements in the book.

## Trigger

Use the scheduled trigger:

```text
Recurrence
```

Configure the recurrence to run weekly on Friday.

Typical settings include:

| Setting   | Example                     |
| --------- | --------------------------- |
| Frequency | Week                        |
| Interval  | 1                           |
| Day       | Friday                      |
| Time      | As required by the exercise |
| Time zone | Appropriate local time zone |

> **Note:** The exact schedule should follow the configuration described in the corresponding Chapter 3 exercise.

## Retrieve Planner Tasks

Use the Microsoft Planner connector to retrieve the tasks required for the weekly summary.

The implementation should identify the appropriate:

* Group or plan
* Tasks
* Task status
* Completion information

The exact Planner configuration depends on the environment used for the exercise.

## Identify Completed Tasks

The summary should include tasks that have been completed during the reporting period.

A completed task can be represented as:

```text
Task: Prepare weekly report
Status: Completed
```

The filtering approach should follow the implementation described in the chapter.

## Build the Summary

The flow prepares the retrieved information into a format suitable for an email.

For example:

```text
Weekly Planner Summary

Completed Tasks

1. Prepare weekly report
2. Review customer requests
3. Complete project documentation

Total Completed: 3
```

The actual task names and total will depend on the data returned from Microsoft Planner.

## Send Email

After preparing the summary, add an email action.

The email can contain:

**Subject**

```text
Weekly Planner Summary
```

**Body**

```text
Hello Team,

Here is the weekly summary of completed Planner tasks.

Completed Tasks:
- Prepare weekly report
- Review customer requests
- Complete project documentation

Total Completed: 3

Regards,
Automation
```

The email format can be customized based on the requirements of the exercise.

## Logical Flow

```text
Recurrence
    ↓
List / Retrieve Planner Tasks
    ↓
Filter Completed Tasks
    ↓
Build Summary
    ↓
Send Email
```

## Example Scenario

Assume the Planner contains the following tasks:

| Task                     | Status      |
| ------------------------ | ----------- |
| Prepare weekly report    | Completed   |
| Review customer requests | Completed   |
| Update project tracker   | In Progress |
| Prepare presentation     | Completed   |

The weekly email should summarize the completed tasks:

```text
Prepare weekly report
Review customer requests
Prepare presentation
```

and exclude the task that is still in progress.

## Using the Sample Data

The Chapter 3 repository provides:

```text
SampleData/PlannerTasks.csv
```

This file is intended to support the Planner-related exercise in the chapter.

Use it as sample input or reference data where applicable. The actual Microsoft Planner connector configuration should follow the implementation described in the book.

## Testing

### Test 1 – Completed Tasks Available

Create or use Planner tasks that contain completed items.

Expected result:

```text
Friday
  ↓
Tasks retrieved
  ↓
Completed tasks identified
  ↓
Summary generated
  ↓
Email sent
```

### Test 2 – No Completed Tasks

Run the flow when there are no completed tasks for the reporting period.

The flow should handle the situation without failing and should produce an appropriate summary.

For example:

```text
Weekly Planner Summary

No completed tasks found for this reporting period.
```

### Test 3 – Multiple Completed Tasks

Use several completed tasks.

Verify that:

* All applicable completed tasks are included.
* Tasks that are not completed are excluded.
* The total count is correct.
* The email contains the expected information.

## Expected Result

Every Friday, the scheduled flow should:

1. Start automatically.
2. Retrieve the relevant Planner task information.
3. Identify completed tasks.
4. Build the weekly summary.
5. Send the summary by email.

The flow run history should show successful execution of each step.

## Validation Checklist

After building the flow, verify:

* [ ] The recurrence is configured for Friday.
* [ ] The correct Planner plan is selected.
* [ ] Tasks are retrieved successfully.
* [ ] Completed tasks are identified correctly.
* [ ] Incomplete tasks are excluded from the summary.
* [ ] The summary is generated correctly.
* [ ] The email is sent successfully.
* [ ] The flow completes without errors.

## Common Issues

### Flow Does Not Run on Friday

Check:

* The flow is turned on.
* The recurrence interval is correct.
* Friday is selected as the required day.
* The time zone is configured correctly.

### Planner Tasks Are Not Retrieved

Check:

* The Planner connection.
* The selected plan or group.
* User permissions.
* The task retrieval action configuration.

### Incomplete Tasks Appear in the Summary

Check the filtering logic used to identify completed tasks.

### Email Is Not Sent

Check:

* The email connection.
* Recipient addresses.
* Required email fields.
* The output of the summary-building step.

## Performance Considerations

For larger Planner plans, avoid unnecessary processing of tasks.

Consider:

* Retrieving only the tasks required by the report.
* Filtering data before building the summary.
* Keeping the email content focused on the reporting requirement.

## Security and Data Considerations

The weekly report may contain information about team activities.

Review:

* Who receives the summary email.
* Who can access the Planner plan.
* Whether task information contains sensitive business data.
* Data retention requirements.

Do not store passwords, API keys, connection secrets, or other sensitive information in this repository.

## Related Resources

* [Chapter 3 – Building Cloud, Desktop and Business Flows](../README.md)
* [Sample Data](../SampleData/)
* [Automated Flows](../AutomatedFlows/)
* [Instant Flows](../InstantFlows/)

## Notes

This example is intended to be used together with the corresponding section of Chapter 3 in *Learning Microsoft Power Automate*.

The current repository defines this example as a flow that **runs every Friday and emails a summary of completed tasks**.

The exact Planner plan, task fields, email recipients, and recurrence time should follow the implementation described in the book.

Microsoft Power Automate and Planner features and their user interfaces may change over time. Refer to the latest Microsoft documentation when the current product experience differs from the version described in the book.
