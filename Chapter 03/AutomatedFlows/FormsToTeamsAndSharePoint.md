# Forms to Teams and SharePoint

## Overview

This example demonstrates how to build an **Automated Cloud Flow** that processes a new Microsoft Forms response, posts a notification to Microsoft Teams, and creates a corresponding item in SharePoint.

The scenario demonstrates how information submitted through a form can be automatically distributed to collaboration and data-storage services.

## Business Scenario

Suppose a team uses Microsoft Forms to collect a request from employees.

When a new response is submitted, Power Automate processes the response and performs two actions:

```text
New Forms Response
       ↓
Get Response Details
       ↓
Post Message to Teams
       ↓
Create SharePoint Item
```

## Flow Type

**Automated Cloud Flow**

The flow starts automatically whenever a new response is submitted to the selected Microsoft Form.

## Trigger

Use the Microsoft Forms trigger:

```text
When a new response is submitted
```

Configure the trigger with the appropriate:

* Form ID

The form should contain the questions required by the business scenario.

## Action 1 – Get Response Details

After the trigger, add:

```text
Microsoft Forms → Get response details
```

Configure:

| Field       | Value                             |
| ----------- | --------------------------------- |
| Form Id     | The same form used by the trigger |
| Response Id | Response Id from the trigger      |

This action retrieves the answers submitted by the respondent.

## Action 2 – Post Message to Teams

Add a Microsoft Teams action to notify the relevant team or channel.

For example:

```text
Microsoft Teams → Post a message in a chat or channel
```

A notification can include information such as:

```text
New form response received

Submitted by: <Respondent>
Request Type: <Request Type>
Comments: <Comments>
```

Use dynamic content from **Get response details** to populate the message.

## Action 3 – Create SharePoint Item

Add:

```text
SharePoint → Create item
```

Configure:

| Field        | Example                |
| ------------ | ---------------------- |
| Site Address | Your SharePoint site   |
| List Name    | Target SharePoint list |
| Requester    | Respondent name        |
| Request Type | Form response          |
| Comments     | Form response          |
| Response ID  | Response Id            |

The exact column names depend on the SharePoint list created for the exercise.

## Logical Flow

```text
When a new response is submitted
              ↓
       Get response details
              ↓
       Post message to Teams
              ↓
       Create item in SharePoint
```

## Example Scenario

Assume an employee submits the following form:

```text
Requester: Ravi Kumar
Request Type: Access Request
Comments: Request access to the finance application
```

The flow should:

### Microsoft Teams

Post a message such as:

```text
New Access Request received from Ravi Kumar.

Request:
Request access to the finance application
```

### SharePoint

Create a list item containing the submitted information.

```text
Requester: Ravi Kumar
Request Type: Access Request
Comments: Request access to the finance application
```

## Testing

### Test 1 – Valid Form Response

Submit a new response.

Expected result:

```text
Form submitted
    ↓
Response details retrieved
    ↓
Teams message posted
    ↓
SharePoint item created
```

### Test 2 – Multiple Responses

Submit several responses.

Expected result:

```text
Each response
    ↓
Separate Teams notification
    ↓
Separate SharePoint item
```

### Test 3 – Missing Optional Information

Submit a response without completing an optional field.

Verify that the flow handles the empty value correctly and that the corresponding SharePoint field or Teams message does not cause the flow to fail.

## Expected Result

For every valid Forms response:

1. The response details are retrieved.
2. A Teams notification is posted.
3. A corresponding SharePoint item is created.

The flow run history should show successful execution of each action.

## Common Issues

### Forms Response Is Not Processed

Check:

* The correct Form ID is configured.
* The flow is turned on.
* A new response was actually submitted.

### Teams Message Fails

Check:

* The correct Team and channel are selected.
* The Teams connection is valid.
* The account has permission to post to the selected location.

### SharePoint Item Is Not Created

Check:

* Site Address.
* List Name.
* SharePoint column names.
* Required SharePoint fields.
* SharePoint connection status.

### Dynamic Content Is Empty

Check that:

* **Get response details** is configured correctly.
* The correct **Response Id** is passed from the trigger.
* The expected form question exists and contains a value.

## Security Considerations

The form may collect business or personal information.

Review:

* Microsoft Forms access permissions.
* Teams membership and channel visibility.
* SharePoint list permissions.
* Data retention requirements.
* Information classification requirements.

Do not store credentials, API keys, passwords, or other secrets in this repository.

## Related Resources

* [Chapter 3 – Building Your First Cloud, Desktop and Business Flows](../README.md)
* [Sample Data](../SampleData/)
* [Expressions](../Expressions/)

## Notes

This example is intended to be used together with the corresponding section of Chapter 3 in *Learning Microsoft Power Automate*.

The exact Microsoft Forms, Teams, SharePoint, connector actions, and interface may vary depending on the environment and current Microsoft Power Automate experience.
