# Invoice Processing with AI Builder

## Overview

This example demonstrates how **AI Builder** can be used to extract structured information from invoices.

Instead of manually reading invoice documents and entering the values into a business system, AI Builder can identify configured invoice information and make the extracted values available to a Power Automate flow.

The example focuses on extracting:

- Invoice Number
- Vendor
- Invoice Date
- Amount

## Scenario

Consider a finance team that receives invoices regularly.

A typical manual process involves opening each invoice, reading the required information, and entering it into another system.

AI Builder can automate the extraction step:

```text
Invoice Received
      ↓
AI Builder Invoice Processing
      ↓
Extract Invoice Information
      ↓
Validate Extracted Values
      ↓
Continue Business Process
```

## Extracted Information

The example focuses on four invoice fields:

| Field | Description |
|---|---|
| Invoice Number | Identifies the invoice |
| Vendor | Identifies the supplier or vendor |
| Invoice Date | Indicates the invoice date |
| Amount | Represents the invoice amount |

## Exercise

### Step 1 – Prepare the Invoice

Provide an invoice document for processing.

The invoice should contain the information required by the exercise, including:

```text
Invoice Number
Vendor
Invoice Date
Amount
```

### Step 2 – Add the AI Builder Action

In the Power Automate flow, add the appropriate AI Builder action for invoice processing.

Provide the invoice document as the input to the AI Builder action.

The exact action name and configuration should follow the implementation used in the corresponding Chapter 4 exercise.

### Step 3 – Extract Invoice Information

Run the AI Builder processing action.

Conceptually, the process is:

```text
Invoice Document
      ↓
AI Builder
      ↓
Invoice Number
Vendor
Invoice Date
Amount
```

The extracted values can then be used as dynamic content in subsequent Power Automate actions.

### Step 4 – Use the Extracted Values

The extracted information can be passed to downstream actions.

For example:

```text
AI Builder Output
      ↓
Validate Invoice Information
      ↓
Create / Update Record
      ↓
Send Notification
```

The actual downstream actions depend on the business process implemented in the chapter.

## Example

Suppose the invoice contains:

```text
Invoice Number: INV-1001
Vendor: ABC Supplies
Invoice Date: 14-Aug-2026
Amount: 25000
```

AI Builder processes the invoice and makes the extracted values available to the Power Automate flow.

The flow can then use those values without requiring manual data entry.

## Validate the Extracted Information

Before using extracted invoice values in a business process, validate the information.

Check that:

- Invoice Number was extracted.
- Vendor was identified.
- Invoice Date contains a valid date.
- Amount contains the expected value.

A simple validation process is:

```text
AI Builder Output
      ↓
Validate Required Fields
      ↓
Valid → Continue
Invalid → Review / Exception
```

## Testing

### Test 1 – Valid Invoice

Provide an invoice containing all four required fields.

Expected result:

```text
Invoice submitted
      ↓
AI Builder processes invoice
      ↓
Invoice Number extracted
Vendor extracted
Invoice Date extracted
Amount extracted
      ↓
Flow continues
```

### Test 2 – Missing Information

Use an invoice where one of the expected values is missing or unclear.

Expected result:

The flow should identify that the required information is unavailable and handle the invoice according to the business process.

### Test 3 – Different Invoice Layout

Test another invoice with a different layout.

Expected result:

The AI Builder model should process the document according to its configured capabilities. Any uncertain or incorrect result should be validated before downstream processing.

## Common Issues

### Invoice Information Is Not Extracted

Check:

- The invoice document is suitable for the configured AI Builder model.
- The correct AI Builder action is being used.
- The invoice contains the required information.
- The document is readable.

### Extracted Value Is Incorrect

Check:

- Invoice layout and document quality.
- The AI Builder configuration.
- The extracted result before using it in a downstream action.
- Whether human review is required for uncertain information.

### Amount Is Not Correct

Treat financial values carefully.

Verify:

- Currency.
- Decimal values.
- Formatting.
- The value displayed on the original invoice.

Do not use an extracted amount for financial processing without appropriate validation.

## Design Considerations

When building invoice-processing automation:

- Extract only the information required by the business process.
- Validate important financial and identification fields.
- Provide an exception or review path for uncertain results.
- Keep human review available for invoices that cannot be processed reliably.
- Avoid unnecessary downstream processing of incomplete invoice data.

## Security and Data Considerations

Invoices may contain sensitive financial, supplier, and business information.

Review:

- Who can access the original invoice.
- Who can access extracted invoice information.
- Where invoice data is stored.
- Who can execute the flow.
- Data retention requirements.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

- [Chapter 4 – Intelligent Automation, AI Builder and Copilot](../README.md)
- [Form Processing with AI Builder](FormProcessing.md)
- [Sample Data](../SampleData/)

## Notes

This example is intended to be used together with the corresponding AI Builder invoice-processing section of Chapter 4 in *Learning Microsoft Power Automate*.

The current repository resource defines this example as extracting **invoice number, vendor, date, and amount from invoices**.

The exact AI Builder model, invoice document, action configuration, and downstream processing should follow the implementation described in the book.