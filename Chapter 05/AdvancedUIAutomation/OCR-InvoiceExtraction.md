# OCR Invoice Extraction

## Overview

This example demonstrates how OCR can be used in a Power Automate for desktop scenario to extract information from a **scanned invoice PDF**.

The scenario is useful when invoice content is presented as an image rather than structured text that can be read directly.

## Scenario

A finance or operations process receives scanned invoice PDFs and needs to extract information before continuing with the automation.

The high-level process is:

```text
Scanned Invoice PDF
        ↓
Open / Access Document
        ↓
OCR Processing
        ↓
Recognized Text
        ↓
Extract Required Information
        ↓
Validate Result
```

## Exercise

### Step 1 – Prepare the Scanned Invoice

Provide a scanned invoice PDF suitable for the exercise.

The document should contain readable invoice information.

### Step 2 – Access the Document

Use Power Automate for desktop to access the invoice file or the application that displays it.

The exact file location and application configuration should follow the environment used in the book exercise.

### Step 3 – Perform OCR

Configure the OCR capability used by the Chapter 5 exercise.

The OCR process should convert the visible document content into machine-readable text.

Conceptually:

```text
Scanned PDF
     ↓
OCR
     ↓
Recognized Text
```

### Step 4 – Extract Invoice Information

Use the OCR result to identify the information required by the business process.

For example:

```text
Invoice Number
Vendor
Invoice Date
Amount
```

The exact fields depend on the invoice format and the exercise implementation.

### Step 5 – Validate the Result

Before using the extracted information downstream, verify important values against the source document.

```text
OCR Result
    ↓
Validate Fields
    ↓
Valid → Continue
Review → Exception / Human Review
```

## Example

Suppose the scanned invoice contains:

```text
Invoice Number: INV-1001
Vendor: Contoso Ltd
Invoice Date: 14-Aug-2026
Amount: 2500
```

The OCR process should recognize the visible text, after which the Desktop Flow can extract the required values.

## Testing

### Test 1 – Clear Scanned Invoice

Use a high-quality scanned PDF.

Expected result:

```text
PDF
 ↓
OCR
 ↓
Text recognized
 ↓
Invoice values extracted
```

### Test 2 – Poor-Quality Scan

Use a document with poor contrast, low resolution, or distorted text.

Expected result:

OCR may produce incomplete or incorrect text. The flow should validate important values before continuing.

### Test 3 – Different Invoice Layout

Use an invoice with a different visual layout.

Expected result:

The OCR process may still recognize text, but field extraction logic may need to account for layout differences.

## Common Issues

### OCR Does Not Recognize the Document

Check:

- The PDF is accessible.
- The pages contain readable text or images.
- The document quality is sufficient.
- The selected OCR capability is configured correctly.

### Text Is Recognized Incorrectly

Check:

- Scan quality.
- Orientation.
- Font size.
- Contrast.
- Background noise.

### Invoice Amount Is Incorrect

Verify the amount against the source invoice, including currency and decimal formatting.

Do not use OCR output directly for financial processing without validation.

## Best Practices

- Use high-quality source documents where possible.
- Validate important invoice fields.
- Keep the original document available when auditability is required.
- Provide an exception path for OCR failures.
- Avoid hard-coding assumptions about invoice layout when multiple layouts are expected.
- Prefer structured data sources when they are available and reliable.

## Security and Data Considerations

Invoices may contain sensitive financial and supplier information.

Review:

- Where invoices are stored.
- Who can access the source documents.
- Who can access OCR results.
- Whether screenshots or temporary files contain sensitive information.

Do not store real customer invoices, passwords, API keys, credentials, or other confidential data in this repository.

## Related Resources

- [Chapter 5 – Advanced Power Automate Desktop](../README.md)
- [Move Mouse to Image](MoveMouseToImage.md)
- [Wait for Image](WaitForImage.md)
- [Chapter 4 – OCR Examples](../../Chapter04-Intelligent-Automation-AI-Builder-Copilot/AIBuilder/OCRExamples.md)

## Notes

This example is intended to accompany the advanced OCR section of Chapter 5 in *Learning Microsoft Power Automate*.

The current repository defines this resource as an **OCR invoice extraction example using scanned PDFs**.