# Data Extraction

## Overview

This example demonstrates how Power Automate for desktop can extract data from **Windows applications and web pages**.

Extracted data can then be stored, transformed, validated, or passed to downstream actions.

## Scenario

Suppose a business process needs to collect information from a browser page or Windows application and use the results in another step.

A typical process is:

```text
Open Application / Web Page
          ↓
Identify Data
          ↓
Extract Data
          ↓
Validate Result
          ↓
Store / Process Data
```

## Exercise

### Step 1 – Open the Source

Launch or attach to the application or browser containing the data to be extracted.

### Step 2 – Identify the Data

Determine whether the required information is exposed as a UI element, table, text, or other supported data structure.

Capture the relevant UI elements or configure the appropriate extraction action.

### Step 3 – Extract the Data

Use the appropriate Power Automate for desktop action to retrieve the information.

For example:

```text
Web Page
   ↓
Extract Table / Text
   ↓
Data Variable
```

The exact action depends on the application and data format used by the exercise.

### Step 4 – Validate the Result

Check that the extracted data is complete and matches the expected structure.

### Step 5 – Use the Data

The extracted values can be:

- Written to a file.
- Stored in a database or business application.
- Used in conditions.
- Passed to another flow action.
- Used to create a report.

## Example

Suppose a website displays a table containing:

```text
Order ID | Customer | Status | Amount
1001     | Contoso  | Open   | 2500
1002     | Fabrikam | Closed | 1800
```

The Desktop Flow can extract the table and process the resulting data.

```text
Web Table
    ↓
Extract Data
    ↓
Data Table
    ↓
Filter / Validate
    ↓
Export / Process
```

## Web UI Elements vs. Desktop UI Elements

Use the appropriate element type for the source.

| Source | Typical Automation Target |
|---|---|
| Web page | Web UI Element |
| Browser chrome | Desktop UI Element |
| Windows application | Desktop UI Element |

Choosing the correct element type helps the automation interact with the intended control or data.

## Handling Dynamic Content

Web pages and applications may generate changing values.

Use stable selectors or dynamic-selector techniques where appropriate.

See:

- [Dynamic Selectors](../DynamicSelectors/README.md)
- [Selector Patterns](../DynamicSelectors/SelectorPatterns.md)

## Testing

### Test 1 – Data Available

Run the flow against a page or application containing the expected data.

**Expected result:** The required data is extracted successfully.

### Test 2 – Data Changes

Run the flow with different values or records.

**Expected result:** The extraction logic continues to identify the intended information.

### Test 3 – Data Missing

Run the flow when the expected data is unavailable.

**Expected result:** The flow detects the condition and follows its exception or validation path.

## Common Issues

### Data Cannot Be Extracted

Check:

- The page or application is fully loaded.
- The correct UI elements were captured.
- The target data is accessible to the automation technology.
- The extraction action supports the target structure.

### Incorrect Data Is Extracted

Check:

- Selector specificity.
- Table structure or page layout.
- Dynamic content.
- Whether multiple similar elements match.

### Extraction Fails After a Website Change

Review the affected selectors and re-capture or update them as necessary.

## Best Practices

- Prefer structured extraction when the page exposes data in a supported table or element structure.
- Use stable selectors.
- Validate important data before downstream processing.
- Keep extraction logic separate from business-processing logic where practical.
- Handle empty or missing results explicitly.
- Avoid extracting more information than the process requires.

## Security Considerations

Extracted data may contain customer, employee, financial, or other sensitive information.

Protect the source and extracted data according to the organization's access and retention requirements.

Do not store passwords, tokens, or other secrets in the repository.

## Related Resources

- [Web Automation](README.md)
- [Launch Browser](LaunchBrowser.md)
- [Form Filling](FormFilling.md)
- [Web Scraping Pattern](WebScrapingPattern.md)
- [Dynamic Selectors](../DynamicSelectors/README.md)

## Notes

The current repository defines this resource as **extracting data from Windows applications and web pages**. The exact extraction action and source structure should follow the corresponding Chapter 5 exercise.