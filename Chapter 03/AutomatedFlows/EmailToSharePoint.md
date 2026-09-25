# Email to SharePoint

## Overview

This example demonstrates how to build an **Automated Cloud Flow** that monitors incoming email and saves email attachments to a SharePoint document library.

The scenario is useful when documents arrive through email and need to be stored automatically without manual downloading and uploading.

## Business Scenario

Assume a team receives documents from customers through email.

Instead of manually downloading each attachment and uploading it to SharePoint, Power Automate can automate the process:

```text
New Email
    ↓
Check for Attachment
    ↓
Get Attachment
    ↓
Create File in SharePoint
```

## Flow Type

**Automated Cloud Flow**

The flow starts automatically when a new email meeting the configured trigger conditions is received.

## Trigger

Use the Outlook trigger:

```text
When a new email arrives (V3)
```

Configure the trigger according to the requirements of the exercise.

Typical options include:

* Mail folder
* To
* CC
* From
* Subject filter
* Include attachments
* Importance

For this example, enable:

```text
Include Attachments = Yes
```

## Flow Actions

### 1. Check for Attachments

The flow should process the email only when attachments are available.

The attachment information is provided by the email trigger.

### 2. Apply to Each Attachment

Because an email can contain more than one attachment, process the attachments using an iteration:

```text
Apply to each
```

Use the attachment collection provided by the trigger.

### 3. Create File in SharePoint

Use:

```text
SharePoint → Create file
```

Configure:

| Field        | Example                        |
| ------------ | ------------------------------ |
| Site Address | Your SharePoint site           |
| Folder Path  | Target document library/folder |
| File Name    | Attachment Name                |
| File Content | Attachment Content             |

The exact SharePoint site and folder depend on the environment used for the exercise.

## Logical Flow

```text
When a new email arrives
        ↓
Is there an attachment?
        ↓
     Yes
        ↓
Apply to each attachment
        ↓
Create file in SharePoint
```

## Example Scenario

Suppose the following email is received:

```text
From: customer@example.com
Subject: Invoice Submission
Attachments:
    Invoice-1001.pdf
    Invoice-1002.pdf
```

The flow should create:

```text
SharePoint
└── Documents
    ├── Invoice-1001.pdf
    └── Invoice-1002.pdf
```

## Recommended Configuration

For a practical implementation, consider filtering the emails using conditions such as:

```text
Subject contains "Invoice"
```

or

```text
From equals "customer@example.com"
```

This prevents unrelated attachments from being stored in SharePoint.

## Preventing Duplicate Files

A production implementation should consider what happens when the same attachment is received more than once.

Possible approaches include:

* Use a unique file naming convention.
* Check whether the file already exists.
* Add the email received date to the filename.
* Store a unique identifier in a tracking list.

These approaches can be introduced after the basic flow is working.

## Testing

Test the flow using the following scenarios:

### Test 1 – Email with One Attachment

Expected result:

```text
One attachment → One SharePoint file
```

### Test 2 – Email with Multiple Attachments

Expected result:

```text
Multiple attachments → Multiple SharePoint files
```

### Test 3 – Email without Attachments

Expected result:

```text
No attachment → No SharePoint file created
```

### Test 4 – Unwanted Email

If an email does not meet the configured filter criteria:

```text
Email received → Flow does not process it
```

## Expected Result

After successful execution, every qualifying email attachment should be stored in the configured SharePoint folder.

The flow run history should show successful execution of the trigger and file-creation actions.

## Common Issues

### Attachment Not Created

Check:

* `Include Attachments` is enabled.
* The email actually contains an attachment.
* The attachment content is passed to the SharePoint **File Content** field.

### SharePoint File Creation Fails

Check:

* Site Address.
* Folder Path.
* SharePoint permissions.
* Connection status.

### Duplicate File Error

Check whether a file with the same name already exists in the target folder.

Configure the flow according to the duplicate-file behavior required by the scenario.

## Security Considerations

Do not automatically store sensitive email attachments in a broadly accessible SharePoint location.

Review:

* SharePoint permissions.
* Email sender restrictions.
* Attachment file types.
* Data classification requirements.
* Retention requirements.

Never store credentials, passwords, connection secrets, or other sensitive configuration values in this repository.

## Related Resources

* [Chapter 3 – Building Your First Cloud, Desktop and Business Flows](../README.md)
* [Sample Data](../SampleData/)
* [Expressions](../Expressions/)

## Notes

This example is intended to be used together with the corresponding section of Chapter 3 in *Learning Microsoft Power Automate*.

The exact trigger options, connector capabilities, and user interface may vary depending on the Microsoft Power Automate and Outlook experience available in your environment.
