# Extraction Prompts

## Overview

This prompt library provides reusable examples for extracting **entities, dates, values, and other structured information** from unstructured text with Copilot.

The prompts are intended to help make extraction requirements explicit and easier to use in Power Automate scenarios.

## Extract Entities

Use this prompt when specific entities need to be identified from text.

```text
Extract the important entities from the text provided.
Return the entity name and its value.
Do not add information that is not present in the source text.
```

## Extract Dates

```text
Extract all dates mentioned in the text.
Return each date with a short description of what the date represents.
Do not infer dates that are not explicitly provided.
```

## Extract Numeric Values

```text
Extract the important numeric values from the text.
For each value, provide its label and the value exactly as stated.
Do not calculate or modify the values unless requested.
```

## Extract Customer Information

```text
Extract the customer information from the text.
Return the customer name, contact information,
reference number, and other clearly identified customer details.
Only return information that is present in the source.
```

## Extract Invoice Information

```text
Extract the following invoice information:
- Invoice Number
- Vendor
- Invoice Date
- Amount

Return the extracted values clearly.
Do not invent values for fields that are missing.
```

## Extract Action Items

```text
Extract the action items from the text.
For each action, identify the action, responsible person or team,
and any stated due date.
Do not infer responsibility or dates when they are not provided.
```

## Structured Extraction

When downstream automation requires predictable output, specify the expected structure.

For example:

```text
Extract the following information from the text:
CustomerName
RequestNumber
RequestDate
RequestType
Amount

Return the result using exactly these field names.
Use null or an empty value when a field is not present.
Do not add additional fields.
```

## Prompt Guidelines

A good extraction prompt should clearly define:

- What information to extract.
- The expected field names.
- Whether missing values should be returned as blank or null.
- Whether values should be preserved exactly as provided.
- Whether additional fields are allowed.

For example:

```text
Extract InvoiceNumber, Vendor, InvoiceDate, and Amount.
Return only these four fields.
Do not infer missing information.
Preserve the values from the source text.
```

## Review Extracted Values

Extracted information should be validated before it is used in an important business process.

Check:

- Required fields are present.
- Dates have the expected format.
- Numeric values are correct.
- Identifiers have not been altered.
- Missing values are handled appropriately.

## Related Resources

- [Form Processing with AI Builder](../AIBuilder/FormProcessing.md)
- [Invoice Processing with AI Builder](../AIBuilder/InvoiceProcessing.md)
- [OCR Examples](../AIBuilder/OCRExamples.md)
- [Invoice Response JSON](../JSONSamples/InvoiceResponse.json)

## Notes

These prompts are examples for the Chapter 4 exercises. Adapt the wording and output structure to the business scenario and Copilot capability used in the book.