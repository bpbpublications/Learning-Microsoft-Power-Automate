# Web Scraping Pattern

## Overview

This example demonstrates a repeatable **web-scraping pattern** in Power Automate for desktop.

The pattern combines browser launch, navigation, data extraction, pagination, validation, and downstream processing.

## Scenario

Suppose a website displays business records across multiple pages and the automation must collect the required information.

A typical process is:

```text
Launch Browser
      ↓
Navigate to Website
      ↓
Extract Current Page
      ↓
Validate Results
      ↓
Next Page?
   ├─ Yes → Repeat Extraction
   └─ No  → Finish
```

## Exercise

### Step 1 – Launch the Browser

Use the browser-launch approach described in [Launch Browser](LaunchBrowser.md).

### Step 2 – Navigate to the Target Page

Open the page that contains the records to be collected.

Wait for the relevant page elements to become available before attempting extraction.

### Step 3 – Extract the Data

Use web UI elements or the appropriate extraction action to retrieve the required information.

For example:

```text
Record ID
Customer
Status
Amount
```

Store the extracted result in an appropriate data structure for subsequent processing.

### Step 4 – Validate the Result

Validate that the expected records were extracted.

For example:

```text
Extracted Data
      ↓
Rows Found?
  ├─ Yes → Continue
  └─ No  → Handle Exception
```

### Step 5 – Check for the Next Page

Determine whether another page of records is available.

The page-navigation method depends on the website.

Conceptually:

```text
Current Page
    ↓
Next Page Available?
    ├─ Yes → Navigate
    │          ↓
    │      Extract Again
    └─ No  → Complete
```

### Step 6 – Process the Complete Dataset

After all pages have been processed, combine or process the extracted data.

Possible destinations include:

- CSV or Excel.
- Database.
- Business application.
- Report.
- Another Power Automate action.

## Example

Suppose a website contains three pages of customer records.

```text
Page 1 → Extract Records
   ↓
Page 2 → Extract Records
   ↓
Page 3 → Extract Records
   ↓
Combine Results
   ↓
Validate / Export
```

## Handling Pagination

Pagination can be implemented using a loop that continues while another page is available.

The logic can be expressed as:

```text
Open Page
   ↓
Extract Data
   ↓
Is Next Page Available?
   ├─ Yes → Click / Navigate Next
   │          ↓
   │       Wait for Page
   │          ↓
   │       Extract Data
   └─ No  → Exit Loop
```

Use a reliable indicator for page availability, such as a stable next-page control or a page-state condition.

## Dynamic Selectors

Pagination controls and data elements may contain dynamic values.

Use stable selectors and dynamic-selector techniques where appropriate.

See:

- [Dynamic Selectors](../DynamicSelectors/README.md)
- [Selector Patterns](../DynamicSelectors/SelectorPatterns.md)

## Testing

### Test 1 – Single Page

Use a website with only one page of data.

**Expected result:** The flow extracts the records and stops when no additional page is available.

### Test 2 – Multiple Pages

Use a website with several pages.

**Expected result:** The flow processes each page and combines the extracted records.

### Test 3 – Empty Page

Test a condition where the expected data is not present.

**Expected result:** The flow detects the condition and follows its validation or exception path.

### Test 4 – Navigation Failure

Simulate or encounter a failure while moving to the next page.

**Expected result:** The flow handles the failure without silently losing records.

## Common Issues

### Duplicate Records

Check whether records are being appended more than once during pagination.

Make sure the flow advances to the next page only after completing the current extraction.

### Infinite Pagination Loop

Use a reliable termination condition and verify that the page actually changes after navigation.

### Page Loads Slowly

Wait for the required page state or control rather than relying only on a fixed delay.

### Extracted Data Is Incomplete

Check selectors, page structure, and whether data is loaded dynamically after the page initially appears.

## Best Practices

- Define a clear pagination termination condition.
- Wait for page content before extraction.
- Validate the result from each page.
- Avoid duplicate records.
- Handle navigation failures explicitly.
- Keep the extracted dataset separate from page-navigation logic where practical.
- Prefer an API or structured data source when one is available and appropriate.

## Security Considerations

Scraped information may contain personal, customer, or business-sensitive data.

Store extracted data only in approved locations and follow organizational access and retention requirements.

Do not store credentials, session tokens, cookies, or confidential scraped data in the repository.

## Related Resources

- [Web Automation](README.md)
- [Launch Browser](LaunchBrowser.md)
- [Data Extraction](DataExtraction.md)
- [Form Filling](FormFilling.md)
- [Dynamic Selectors](../DynamicSelectors/README.md)
- [Error Handling](../ErrorHandling/README.md)

## Notes

The current repository defines this resource as a pattern covering **launch, navigate, extract, paginate, and validate**. The exact website, selectors, extraction fields, and pagination control should follow the corresponding Chapter 5 exercise. fileciteturn133file0L2-L6