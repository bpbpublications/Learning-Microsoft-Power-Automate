# Input and Output Variables

## Overview

This example demonstrates how data can be passed between a **Cloud Flow** and a **Desktop Flow** in Power Automate.

A Cloud Flow can provide input values to a Desktop Flow, and the Desktop Flow can return output values after completing its work.

This allows the two types of automation to work together as part of a single end-to-end process.

## Business Scenario

Consider a process where a Cloud Flow receives information and then needs a Windows application to perform an action.

The Cloud Flow can:

1. Receive or prepare the required information.
2. Start the Desktop Flow.
3. Pass values to the Desktop Flow.
4. Wait for the Desktop Flow to complete.
5. Receive output values from the Desktop Flow.
6. Continue the cloud-based process.

The overall flow can be represented as:

```text
Cloud Flow
    ↓
Input Values
    ↓
Desktop Flow
    ↓
Process Data
    ↓
Output Values
    ↓
Cloud Flow
```

## Why Use Input and Output Variables?

Input and output variables allow cloud and desktop automation to exchange information.

For example:

* A Cloud Flow can send an invoice number to a Desktop Flow.
* A Desktop Flow can use that value in a legacy application.
* The Desktop Flow can return a processing status.
* The Cloud Flow can use that status in a later action.

This creates a bridge between cloud-based orchestration and Windows-based execution.

## Input Variables

An **input variable** is a value provided to the Desktop Flow when the flow starts.

Examples include:

```text
Invoice Number
Customer Name
File Path
Transaction ID
User ID
```

For example:

```text
Invoice Number = INV-1001
```

The Desktop Flow receives the value and can use it during execution.

## Output Variables

An **output variable** is a value returned by the Desktop Flow after processing is completed.

Examples include:

```text
Processing Status
Processed Invoice Number
Result Message
Output File Path
Error Information
```

For example:

```text
Processing Status = Success
```

The Cloud Flow can use the returned value in subsequent actions.

## Example

Consider the following scenario:

```text
Cloud Flow
    ↓
Send Invoice Number
    ↓
Desktop Flow
    ↓
Open Legacy Application
    ↓
Process Invoice
    ↓
Return Processing Status
    ↓
Cloud Flow
    ↓
Send Notification
```

### Input

The Cloud Flow passes:

```text
Invoice Number:
INV-1001
```

### Desktop Processing

The Desktop Flow uses the invoice number while interacting with the target Windows application.

### Output

After completing the operation, the Desktop Flow returns:

```text
Processing Status:
Success
```

The Cloud Flow can then use the returned status to determine the next action.

## Creating the Integration

The exact configuration depends on the Power Automate environment and the Desktop Flow implementation used in the chapter.

The general process is:

### Step 1 – Create the Desktop Flow

Create a Desktop Flow that accepts the values required by the automation.

For example:

```text
Input:
Invoice Number
```

### Step 2 – Use the Input in the Desktop Flow

Use the input variable in the Desktop Flow actions.

For example, the invoice number can be entered into a field in a legacy application.

```text
Input Variable
      ↓
Application Field
```

### Step 3 – Produce an Output

After processing, create an output value.

For example:

```text
Processing Status
```

Possible values could include:

```text
Success
Failed
Requires Review
```

The exact values should match the implementation used in the exercise.

### Step 4 – Run the Desktop Flow from the Cloud Flow

The Cloud Flow invokes the Desktop Flow and provides the required input values.

The Desktop Flow performs the required work and returns its output values.

### Step 5 – Use the Output in the Cloud Flow

The Cloud Flow can use the returned value for subsequent processing.

For example:

```text
Desktop Flow Output
        ↓
Check Processing Status
        ↓
Success → Continue
Failed  → Handle Error
```

## Data Flow Example

The data exchange can be represented as:

```text
                 CLOUD FLOW
                     │
                     │ Input
                     ▼
              ┌──────────────┐
              │ Desktop Flow │
              └──────────────┘
                     │
                     │ Output
                     ▼
                 CLOUD FLOW
```

## Testing

### Test 1 – Successful Processing

Send a valid input to the Desktop Flow.

Example:

```text
Invoice Number: INV-1001
```

Expected result:

```text
Desktop Flow processes the invoice
        ↓
Processing Status = Success
        ↓
Cloud Flow continues
```

### Test 2 – Invalid Input

Provide an invalid or unexpected value.

Expected result:

The Desktop Flow should handle the condition according to the implementation and return an appropriate output.

For example:

```text
Processing Status = Failed
```

The Cloud Flow can then apply the appropriate error-handling logic.

### Test 3 – Output Used by Cloud Flow

Verify that the Cloud Flow can access and use the Desktop Flow output.

For example:

```text
Success → Send completion notification
Failed  → Send exception notification
```

## Validation Checklist

* [ ] The Desktop Flow accepts the required input.
* [ ] The input value is available inside the Desktop Flow.
* [ ] The Desktop Flow processes the input correctly.
* [ ] An output value is generated.
* [ ] The Cloud Flow receives the output.
* [ ] The output can be used by subsequent Cloud Flow actions.
* [ ] Success and failure scenarios are handled appropriately.

## Common Issues

### Input Value Is Not Available

Check:

* The input variable was configured correctly.
* The Cloud Flow provides the expected value.
* The Desktop Flow is invoked using the correct configuration.

### Output Value Is Not Returned

Check:

* The output variable is defined.
* The Desktop Flow assigns a value before completion.
* The Cloud Flow is configured to receive the output.

### Incorrect Value Is Passed

Verify:

* The input mapping.
* Variable names.
* Data types.
* The value being supplied by the Cloud Flow.

## Design Considerations

When designing cloud-to-desktop integrations:

* Keep input values clearly defined.
* Use meaningful variable names.
* Validate input before processing.
* Return useful output values.
* Define how failures are communicated.
* Avoid passing unnecessary data.
* Keep sensitive information out of logs and sample files.

## Security Considerations

Input and output variables may contain business or personal information.

Review:

* Who can trigger the Cloud Flow.
* Who can run the Desktop Flow.
* Permissions on connected applications.
* Whether sensitive values are exposed in flow history or logs.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

* [Chapter 3 – Building Cloud, Desktop and Business Flows](../README.md)
* [Invoice Entry – Legacy Application](../DesktopFlows/InvoiceEntryLegacyApp.md)
* [UI Automation Selectors](../DesktopFlows/UIAutomationSelectors.md)
* [Sample Data](../SampleData/)

## Notes

This example is intended to be used together with the corresponding Cloud and Desktop Integration section of Chapter 3 in *Learning Microsoft Power Automate*.

The current repository defines this resource as an example of **passing data between cloud and desktop flows**.

The exact input and output variables, connectors, and Desktop Flow implementation should follow the implementation described in the book.
