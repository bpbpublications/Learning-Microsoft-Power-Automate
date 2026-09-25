# Form Filling

## Overview

This example demonstrates how Power Automate for desktop can automate **desktop and web form filling**.

The flow can locate fields, enter values, select options, and submit the form through the application's user interface.

## Scenario

Suppose a business process requires repeatedly entering customer or request information into a browser-based form.

A Desktop Flow can automate the repetitive interaction:

```text
Start Desktop Flow
       ↓
Open Web Page
       ↓
Identify Form Fields
       ↓
Enter Values
       ↓
Select Options
       ↓
Submit Form
       ↓
Validate Result
```

## Exercise

### Step 1 – Open the Form

Launch or attach to the browser and navigate to the form used in the exercise.

### Step 2 – Capture the Form Controls

Capture the required web UI elements, such as:

- Text fields
- Drop-down lists
- Check boxes
- Radio buttons
- Submit buttons

Use stable attributes and selectors where possible.

### Step 3 – Enter Text Values

Use browser automation actions to populate the required text fields.

For example:

```text
Customer Name → CustomerName variable
Request ID    → RequestId variable
Email         → Email variable
```

### Step 4 – Select Options

Choose the required values from drop-down lists or other selectable controls.

### Step 5 – Submit the Form

Select the submit or continue control after all required values have been entered.

### Step 6 – Validate the Result

Verify that the expected confirmation, result page, or status is displayed.

## Example

Suppose a request form requires:

```text
Customer Name: ABC Industries
Request Type: Access Request
Priority: High
Email: user@example.com
```

The Desktop Flow can populate the form and submit it:

```text
Read Input Data
      ↓
Populate Customer Name
      ↓
Select Request Type
      ↓
Select Priority
      ↓
Enter Email
      ↓
Submit
      ↓
Validate Confirmation
```

## Handling Dynamic Forms

Web pages may change between executions.

Use dynamic selectors and stable web UI attributes when possible.

Refer to:

- [Dynamic Selectors](../DynamicSelectors/README.md)
- [Selector Patterns](../DynamicSelectors/SelectorPatterns.md)

## Testing

### Test 1 – Valid Form

Provide valid values for all required fields.

**Expected result:** The form is populated and submitted successfully.

### Test 2 – Missing Required Field

Leave a required field empty.

**Expected result:** The website displays the expected validation message and the flow handles the condition appropriately.

### Test 3 – Invalid Value

Provide an invalid value such as an incorrectly formatted email address.

**Expected result:** The website rejects the input or displays a validation message, which the flow can detect and handle.

## Common Issues

### Field Cannot Be Found

Check:

- The page is fully loaded.
- The correct web UI element was captured.
- The selector remains valid.
- The target is inside an iframe or other page structure that requires appropriate handling.

### Value Is Entered but Not Accepted

Check:

- Expected format.
- Whether the control requires a specific interaction method.
- Whether client-side validation has completed.

### Submit Does Not Work

Check:

- Required fields.
- Button selector.
- Page state.
- Validation messages.

## Best Practices

- Use web UI elements instead of screen coordinates when possible.
- Wait for the page and controls to become available.
- Keep input values separate from UI interaction logic.
- Validate successful submission.
- Handle required-field and validation errors.
- Use dynamic selectors when values or controls change between runs.

## Security Considerations

Form automation can handle personal or confidential information.

Do not hard-code passwords or other secrets in the flow or repository. Use approved credential-management mechanisms for secured applications.

## Related Resources

- [Web Automation](README.md)
- [Launch Browser](LaunchBrowser.md)
- [Data Extraction](DataExtraction.md)
- [Web Scraping Pattern](WebScrapingPattern.md)
- [Dynamic Selectors](../DynamicSelectors/README.md)

## Notes

The current repository defines this resource as **desktop and web form filling examples**. The exact controls and field values should follow the corresponding Chapter 5 exercise. fileciteturn131file0L2-L6