# Form Processing with AI Builder

## Overview

This example demonstrates how **AI Builder form processing** can be used to extract structured information from submitted forms.

Instead of manually reading each form and copying values into another system, AI Builder can identify configured fields and make the extracted information available for downstream automation.

## Scenario

Consider a business process in which forms are submitted regularly and the information needs to be captured in a structured format.

A typical process can be represented as:

```text
Form Submitted
      ↓
AI Builder Form Processing
      ↓
Extract Structured Fields
      ↓
Validate Extracted Data
      ↓
Continue Automation
```

The extracted values can then be used by other Power Automate actions.

## What Form Processing Does

Form processing uses an AI Builder model to identify fields configured for extraction from the submitted form.

For example, a form may contain information such as:

```text
Customer Name
Request Number
Request Date
Request Type
Amount
```

The AI Builder model processes the submitted document and returns the values it identifies for the configured fields.

> **Note:** The actual fields depend on the form-processing model and the documents used in the corresponding Chapter 4 exercise.

## Exercise

### Step 1 – Prepare the Form Processing Model

Create or use the AI Builder form-processing model associated with the exercise.

The model should be configured to identify the fields required by the business scenario.

### Step 2 – Provide the Form

Provide a sample form or document for processing.

The input should contain the fields configured in the AI Builder model.

### Step 3 – Add the AI Builder Action

In the Power Automate flow, add the appropriate AI Builder action for form processing.

Configure the action with the required document or form input.

The exact action name and configuration should follow the implementation used in the corresponding chapter exercise.

### Step 4 – Extract the Fields

Run the AI Builder processing action.

The model returns the fields it identifies from the submitted form.

Conceptually:

```text
Submitted Form
      ↓
AI Builder Model
      ↓
Customer Name
Request Number
Request Date
Request Type
Amount
```

### Step 5 – Use the Extracted Values

The extracted values can be used as dynamic content in subsequent actions.

For example:

```text
AI Builder Output
      ↓
Create Record
      ↓
Send Notification
      ↓
Update Business System
```

## Example

Suppose the submitted form contains:

```text
Customer Name: ABC Industries
Request Number: REQ-1001
Request Type: Service Request
Amount: 25000
```

The form-processing model attempts to identify the configured fields and makes the extracted values available to the flow.

The downstream automation can then use those values without requiring the user to manually re-enter them.

## Validation

AI Builder output should be validated before it is used in an important business process.

Check:

- Required fields were extracted.
- Extracted values are in the expected format.
- Important values contain the expected information.
- Missing or uncertain values are handled appropriately.

A simple process can be:

```text
AI Builder Output
      ↓
Validate Required Fields
      ↓
Valid → Continue
Invalid → Review / Exception
```

## Testing

### Test 1 – Valid Form

Provide a form containing all configured fields.

Expected result:

```text
Form submitted
      ↓
AI Builder processes the form
      ↓
Configured fields are extracted
      ↓
Flow continues
```

### Test 2 – Missing Field

Provide a form where a required field is missing.

Expected result:

The flow should identify that the required information is unavailable and handle the situation according to the business process.

### Test 3 – Different Form Values

Submit forms containing different values for the configured fields.

Expected result:

The model extracts the corresponding values and makes them available to subsequent flow actions.

## Common Issues

### Fields Are Not Extracted

Check:

- The document is suitable for the configured model.
- The correct AI Builder model is selected.
- The field is included in the model configuration.
- The submitted document contains the expected information.

### Extracted Value Is Incorrect

Check:

- The quality and layout of the input document.
- The model configuration.
- The field definition used during training or setup.
- Whether additional validation is required.

### Required Information Is Missing

Do not assume that every field will always contain a usable value.

Add validation before using the extracted result in a downstream business action.

## Design Considerations

When building form-processing automation:

- Define the fields that the business process actually needs.
- Validate important extracted values.
- Design an exception path for missing or incorrect data.
- Keep human review available for cases where automated extraction is not sufficient.
- Avoid sending unnecessary sensitive information through downstream actions.

## Security and Data Considerations

Forms may contain personal, financial, or business-sensitive information.

Review:

- Who can submit the forms.
- Who can access the processed documents.
- Who can access the extracted data.
- Where the extracted information is stored.
- Data retention requirements.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

- [Chapter 4 – Intelligent Automation, AI Builder and Copilot](../README.md)
- [AI Builder Resources](../AIBuilder/)
- [Sample Data](../SampleData/)

## Notes

This example is intended to be used together with the corresponding AI Builder form-processing section of Chapter 4 in *Learning Microsoft Power Automate*.

The current repository resource defines this topic as extracting **structured fields from submitted forms**.

The exact AI Builder model, fields, input documents, and downstream actions should follow the implementation described in the book.