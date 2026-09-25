# Invoice OCR Scenario

## Overview

This example demonstrates a **hybrid automation scenario** in which a Cloud Flow receives an invoice and a Desktop Flow performs the local processing required for OCR.

The scenario shows how cloud-based orchestration and desktop automation can work together as part of a single business process.

## Business Scenario

Suppose an invoice arrives electronically and needs to be processed before its information can be entered into a business application.

The high-level process is:

```text
Invoice Received
       ↓
Cloud Flow
       ↓
Identify Invoice
       ↓
Run Desktop Flow
       ↓
Process Invoice with OCR
       ↓
Return Extracted Information
       ↓
Continue Cloud Processing
```

The Cloud Flow provides orchestration, while the Desktop Flow performs the desktop-based processing.

## Hybrid Automation Model

The scenario can be divided into two parts.

### Cloud Flow

The Cloud Flow is responsible for:

* Receiving or identifying the invoice.
* Preparing the information required by the Desktop Flow.
* Starting the Desktop Flow.
* Receiving the processing result.
* Continuing the business process.

### Desktop Flow

The Desktop Flow is responsible for:

* Receiving the invoice information or file location.
* Performing the local processing required for the OCR scenario.
* Extracting the required information.
* Returning the result to the Cloud Flow.

## End-to-End Flow

```text
Cloud Flow
    │
    │ Invoice / File Information
    ▼
Desktop Flow
    │
    │ OCR Processing
    ▼
Extracted Invoice Data
    │
    ▼
Cloud Flow
    │
    ├── Continue Processing
    └── Handle Exception
```

## Exercise

### Step 1 – Receive the Invoice

The Cloud Flow receives or identifies the invoice that needs to be processed.

The source and trigger depend on the implementation described in the corresponding Chapter 3 exercise.

The invoice may be represented as:

* An email attachment.
* A file in cloud storage.
* Another supported input source.

### Step 2 – Prepare the Desktop Flow Input

The Cloud Flow prepares the information required by the Desktop Flow.

Typical input information may include:

```text
Invoice File
Invoice File Path
Invoice Identifier
```

The actual inputs should match the implementation used in the exercise.

### Step 3 – Start the Desktop Flow

The Cloud Flow invokes the Desktop Flow and passes the required input values.

Conceptually:

```text
Invoice File
     ↓
Cloud Flow
     ↓
Run Desktop Flow
```

### Step 4 – Process the Invoice

The Desktop Flow performs the OCR-related processing required by the scenario.

The processing may include:

```text
Open Invoice
      ↓
Read Invoice Content
      ↓
Extract Required Information
      ↓
Prepare Result
```

The exact OCR technology and implementation should follow the corresponding chapter exercise.

### Step 5 – Return the Result

After processing, the Desktop Flow returns the extracted information to the Cloud Flow.

Example output:

```text
Invoice Number
Invoice Date
Vendor
Amount
Processing Status
```

The exact output fields depend on the implementation.

### Step 6 – Continue Cloud Processing

The Cloud Flow can use the returned information for the next business step.

For example:

```text
OCR Result
    ↓
Validate Data
    ↓
Store Invoice Information
    ↓
Send Notification
```

## Example

Consider an invoice with the following information:

```text
Invoice Number: INV-1001
Vendor: ABC Supplies
Amount: 25000
```

The overall automation can be:

```text
Invoice Received
      ↓
Cloud Flow
      ↓
Run Desktop Flow
      ↓
OCR Processing
      ↓
Extract Invoice Information
      ↓
Return Result
      ↓
Cloud Flow
      ↓
Store / Notify
```

## Input and Output

The Cloud Flow and Desktop Flow can exchange values through inputs and outputs.

### Example Input

```text
Invoice File:
Invoice-1001.pdf
```

### Example Output

```text
Invoice Number:
INV-1001

Processing Status:
Success
```

The returned values can then be used by subsequent Cloud Flow actions.

## Error Handling

Hybrid automations should account for both cloud and desktop failures.

Possible scenarios include:

### Invoice Not Available

```text
Cloud Flow
    ↓
Invoice Not Found
    ↓
Handle Exception
```

### OCR Processing Failure

```text
Cloud Flow
    ↓
Desktop Flow
    ↓
OCR Failure
    ↓
Return Failed Status
    ↓
Cloud Flow Handles Exception
```

### Application Processing Failure

If the Desktop Flow depends on a local application, the application may fail to start or may not respond as expected.

The Desktop Flow should return an appropriate status so that the Cloud Flow can handle the condition.

## Testing

### Test 1 – Valid Invoice

Provide a valid invoice.

Expected result:

```text
Invoice received
      ↓
Desktop Flow runs
      ↓
OCR processing completes
      ↓
Invoice information returned
      ↓
Cloud Flow continues
```

### Test 2 – Invalid Invoice

Use an invoice that cannot be processed.

Expected result:

The Desktop Flow returns an appropriate failure or review status and the Cloud Flow handles the exception.

### Test 3 – Desktop Processing Failure

Simulate or encounter a desktop-processing failure.

Expected result:

```text
Desktop Flow fails
      ↓
Failure status returned
      ↓
Cloud Flow handles the error
```

## Validation Checklist

* [ ] The Cloud Flow receives the invoice.
* [ ] The required Desktop Flow input is prepared.
* [ ] The Desktop Flow starts successfully.
* [ ] OCR processing is performed.
* [ ] Extracted information is returned.
* [ ] The Cloud Flow receives the output.
* [ ] Success and failure scenarios are handled appropriately.

## Design Considerations

When designing a cloud-to-desktop OCR process:

* Keep the Cloud Flow responsible for orchestration.
* Keep desktop-specific processing inside the Desktop Flow.
* Define clear input and output values.
* Validate extracted data before downstream processing.
* Provide clear success and failure statuses.
* Avoid exposing sensitive invoice information unnecessarily.
* Make the desktop automation resilient to application or UI changes.

## Security and Data Considerations

Invoices may contain sensitive financial or customer information.

Review:

* Who can access the invoice.
* Where the invoice is stored.
* Who can run the Desktop Flow.
* Where extracted information is stored.
* Whether invoice data appears in flow history or logs.
* Applicable retention requirements.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

* [Chapter 3 – Building Cloud, Desktop and Business Flows](../README.md)
* [Input and Output Variables](InputOutputVariables.md)
* [Invoice Entry – Legacy Application](../DesktopFlows/InvoiceEntryLegacyApp.md)
* [Sample Data](../SampleData/)

## Notes

This example is intended to be used together with the corresponding Cloud and Desktop Integration section of Chapter 3 in *Learning Microsoft Power Automate*.

The current repository defines this scenario as a **Cloud Flow receiving an invoice and a Desktop Flow processing OCR**.

The exact invoice source, OCR implementation, input fields, output fields, and destination should follow the implementation described in the book.
