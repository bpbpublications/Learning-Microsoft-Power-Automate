# OCR Examples

## Overview

This resource provides examples of using **Optical Character Recognition (OCR)** to recognize text from images and PDF documents.

OCR can convert text contained in a visual document into machine-readable information that can be used in a Power Automate process.

## Scenario

Consider a business process where information is received as an image or PDF and the text needs to be captured before further processing.

A typical process can be represented as:

```text
Image or PDF
     ↓
OCR Processing
     ↓
Recognized Text
     ↓
Validate / Transform
     ↓
Continue Automation
```

## What OCR Does

OCR identifies text contained in an image or document and returns the recognized text so that it can be used by downstream actions.

Common examples include:

- Scanned documents
- Images containing text
- PDF documents containing visible text
- Receipts
- Forms
- Labels
- Other business documents

The quality of the OCR result depends on the input document and the OCR technology being used.

## Exercise

### Step 1 – Prepare the Input

Provide an image or PDF containing readable text.

For example:

```text
Customer Name: ABC Industries
Reference: DOC-1001
Amount: 25000
```

The source can be an image file or a PDF used by the corresponding Chapter 4 exercise.

### Step 2 – Add OCR Processing

Configure the appropriate OCR capability used by the chapter exercise.

Provide the image or PDF as the input.

The exact action, connector, or AI capability should follow the implementation described in the corresponding Chapter 4 section.

### Step 3 – Recognize the Text

Run the OCR process.

Conceptually:

```text
Image / PDF
      ↓
OCR
      ↓
Recognized Text
```

The recognized text can then be passed to subsequent Power Automate actions.

### Step 4 – Use the Recognized Text

Once the text has been obtained, it can be used for further processing.

For example:

```text
Recognized Text
      ↓
Extract Required Information
      ↓
Validate Values
      ↓
Store / Notify / Continue
```

## Example

Suppose an image contains:

```text
Employee Request

Name: Ravi Kumar
Request ID: REQ-1001
Request Type: Access Request
```

OCR processes the image and returns the recognized text.

The flow can then use the text to identify the information required by the business process.

## Text Extraction and Validation

OCR output should be reviewed before it is used in an important business process.

For example:

```text
OCR Output
      ↓
Check Required Text
      ↓
Valid → Continue
Invalid → Review / Exception
```

Validation is especially important when the recognized text contains:

- Names
- Numbers
- Dates
- Reference IDs
- Financial values

## Testing

### Test 1 – Clear Image

Provide a clear image containing readable text.

Expected result:

```text
Image
  ↓
OCR
  ↓
Text recognized successfully
```

### Test 2 – PDF Document

Provide a PDF containing readable text.

Expected result:

```text
PDF
 ↓
OCR
 ↓
Text recognized
```

### Test 3 – Poor-Quality Image

Test an image with low resolution, poor contrast, or unclear text.

Expected result:

The OCR result may be incomplete or inaccurate. The flow should handle the result appropriately rather than assuming that every extracted value is correct.

## Common Issues

### Text Is Not Recognized

Check:

- The input file is accessible.
- The image or PDF contains readable text.
- The document quality is sufficient.
- The correct OCR capability is configured.

### Text Is Incorrect

Check:

- Image quality.
- Text clarity.
- Document orientation.
- Layout and formatting.
- Whether the extracted text requires validation.

### Important Values Are Incorrect

Pay particular attention to:

- Numbers
- Dates
- Amounts
- Identifiers

Do not use OCR output directly for critical business decisions without appropriate validation.

## Design Considerations

When building OCR-based automation:

- Use OCR only when text cannot be obtained directly in a structured form.
- Validate important extracted values.
- Provide an exception path for uncertain results.
- Keep human review available when required.
- Avoid unnecessary processing of sensitive documents.
- Preserve the original document when auditability is important.

## Security and Data Considerations

Images and PDFs may contain sensitive business or personal information.

Review:

- Who can upload documents.
- Who can access the original files.
- Who can access recognized text.
- Where OCR output is stored.
- Data retention requirements.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

- [Chapter 4 – Intelligent Automation, AI Builder and Copilot](../README.md)
- [Form Processing with AI Builder](FormProcessing.md)
- [Invoice Processing with AI Builder](InvoiceProcessing.md)

## Notes

This resource is intended to accompany the OCR section of Chapter 4 in *Learning Microsoft Power Automate*.

The current repository defines this topic as recognizing text from **images and PDFs**.

The exact OCR capability, action, input documents, and downstream processing should follow the implementation described in the book.