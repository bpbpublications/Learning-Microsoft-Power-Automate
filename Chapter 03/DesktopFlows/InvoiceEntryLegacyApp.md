# Invoice Entry – Legacy Application

## Overview

This example demonstrates how to use **Power Automate for desktop** to read invoice information and enter it into a legacy Windows application.

The exercise represents a common business automation scenario where information is received in a structured file and then entered into an application that does not provide a modern API.

The Desktop Flow performs the interaction through the application's user interface.

## Business Scenario

An operations team receives invoice information in a file.

The invoice data must then be entered into a legacy application manually.

The manual process can be represented as:

```text
Invoice Data
     ↓
Read Invoice Information
     ↓
Open Legacy Application
     ↓
Enter Invoice Details
     ↓
Save Invoice
```

Power Automate for desktop can automate these repetitive UI interactions.

## Sample Data

The Chapter 3 repository provides:

```text
SampleData/InvoiceData.csv
```

The sample file is used as the source of invoice information for this exercise.

Before building the flow, review the columns and values in the sample file so that the application fields can be mapped correctly.

## Exercise

### Step 1 – Create a Desktop Flow

Open **Power Automate for desktop** and create a new Desktop Flow.

Use a meaningful name such as:

```text
Invoice Entry – Legacy Application
```

### Step 2 – Read the Invoice Data

Use the appropriate file-handling actions to read the invoice information from:

```text
SampleData/InvoiceData.csv
```

The flow should make the invoice values available as variables that can be used later in the automation.

Typical invoice information may include:

* Invoice number
* Invoice date
* Vendor
* Amount
* Other fields included in the sample data

> **Important:** Use the actual columns provided in `InvoiceData.csv` when building the exercise. Do not assume additional fields that are not present in the sample file.

### Step 3 – Open the Legacy Application

Launch the target legacy application using the appropriate Desktop Flow action.

The application may require:

* A specific executable.
* A desktop shortcut.
* A configured environment.
* Existing application access.

The exact application configuration should follow the corresponding example described in the book.

### Step 4 – Identify the Application Fields

Use Power Automate for desktop UI Elements to identify the fields where invoice information must be entered.

For example:

```text
Invoice Number
Invoice Date
Vendor
Amount
```

The actual fields depend on the legacy application used in the exercise.

### Step 5 – Enter the Invoice Information

Map the values read from the invoice data to the corresponding application fields.

The logical sequence is:

```text
Read Invoice Number
        ↓
Enter Invoice Number

Read Invoice Date
        ↓
Enter Invoice Date

Read Vendor
        ↓
Enter Vendor

Read Amount
        ↓
Enter Amount
```

Use UI automation actions to interact with the application.

### Step 6 – Save the Invoice

After all required information has been entered, use the application's save or submit operation.

The expected sequence is:

```text
Enter Invoice Data
       ↓
Validate Fields
       ↓
Save / Submit
```

## End-to-End Flow

The complete Desktop Flow can be represented as:

```text
Start Desktop Flow
       ↓
Read InvoiceData.csv
       ↓
Launch Legacy Application
       ↓
Capture / Use UI Elements
       ↓
Enter Invoice Information
       ↓
Save Invoice
       ↓
Complete
```

## Example

Suppose the source data contains an invoice record such as:

```text
Invoice Number: INV-1001
Invoice Date: 2026-08-01
Vendor: ABC Supplies
Amount: 25000
```

The Desktop Flow should read the values and enter them into the corresponding fields in the legacy application.

The exact values and field names should come from the sample data and application used in the exercise.

## Testing

### Test 1 – Valid Invoice

Use a valid invoice record from `InvoiceData.csv`.

Expected result:

```text
Invoice data is read
        ↓
Legacy application opens
        ↓
Invoice fields are populated
        ↓
Invoice is saved successfully
```

### Test 2 – Multiple Invoice Records

If the sample file contains multiple records, process them according to the exercise requirements.

Verify that each record is entered correctly.

### Test 3 – Invalid or Missing Data

Test a record containing missing or unexpected data, where applicable.

The flow should identify the problem rather than entering incorrect information into the application.

## Validation

After running the automation, verify:

* [ ] The invoice file is read successfully.
* [ ] The legacy application opens.
* [ ] The correct UI elements are identified.
* [ ] Invoice values are entered into the intended fields.
* [ ] Required fields are completed.
* [ ] The invoice is saved successfully.
* [ ] The flow completes without unexpected errors.

## Troubleshooting

### Invoice Data Cannot Be Read

Check:

* The `InvoiceData.csv` file exists.
* The file path is correct.
* The file format is valid.
* The flow has access to the file.

### Legacy Application Does Not Open

Check:

* The application is installed.
* The configured application path is correct.
* The user has permission to launch the application.
* Any required application dependencies are available.

### UI Element Cannot Be Found

Check:

* The application is fully loaded before interacting with it.
* The correct UI Element was captured.
* The selector is still valid.
* The appropriate selector technology is being used.

For selector guidance, see:

[UI Automation Selectors](UIAutomationSelectors.md)

### Data Is Entered Into the Wrong Field

Review the captured UI Elements and verify that each source value is mapped to the correct destination field.

### Save Operation Fails

Check:

* Required fields.
* Application validation messages.
* Button or control selectors.
* Application permissions.
* Whether the application has finished processing the entered data.

## Reliability Considerations

Legacy applications can be sensitive to timing and UI changes.

For more reliable automation:

* Wait for the application or window to become available before interacting with it.
* Use reliable UI Elements instead of screen coordinates where possible.
* Avoid unnecessary fixed delays.
* Validate important fields before saving.
* Handle unexpected application states.
* Use stable selectors for critical controls.

## Relationship to UI Automation Selectors

This exercise demonstrates why selector design matters in Desktop Flows.

The automation needs to identify application controls such as:

```text
Invoice Number Field
Invoice Date Field
Vendor Field
Amount Field
Save Button
```

The selector strategy described in `UIAutomationSelectors.md` can be applied to these controls.

## Security and Data Considerations

Invoice information may contain sensitive business or financial data.

Review:

* Access to the source file.
* Access to the legacy application.
* Permissions for the Desktop Flow.
* Storage and retention requirements.
* Handling of sensitive invoice information.

Do not store passwords, application credentials, API keys, or other secrets in this repository.

## Related Resources

* [Chapter 3 – Building Cloud, Desktop and Business Flows](../README.md)
* [Sample Data](../SampleData/)
* [Run Application – Notepad](RunApplication-Notepad.md)
* [UI Automation Selectors](UIAutomationSelectors.md)

## Notes

This example is intended to be used together with the corresponding Desktop Flow section of Chapter 3 in *Learning Microsoft Power Automate*.

The current repository defines this example as a Desktop Flow that **reads invoice data and enters it into a legacy application**.

The exact source columns, legacy application fields, executable path, and UI elements should follow the implementation described in the book and the environment used for the exercise.
