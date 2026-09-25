# Data Summarization with Copilot

## Overview

This example demonstrates how **Copilot** can help summarize operational data and business reports.

Instead of manually reviewing large amounts of information, Copilot can help produce a concise summary that highlights important information for further review or action.

## Scenario

Consider a team that receives operational data and needs a quick summary for a manager or business user.

A typical process can be represented as:

```text
Operational Data
       ↓
Copilot
       ↓
Summarize Information
       ↓
Review Summary
       ↓
Share / Act on Results
```

## What Data Summarization Provides

Data summarization converts detailed operational information into a shorter and easier-to-understand summary.

The summary can help users identify:

- Important information
- Key observations
- Trends or notable items
- Information that may require follow-up

The exact output depends on the data provided and the Copilot capability used in the exercise.

## Exercise

### Step 1 – Prepare the Operational Data

Provide the operational data or report that needs to be summarized.

The source may contain information such as:

```text
Date
Department
Task
Status
Owner
Comments
```

The actual data structure should follow the example used in the corresponding Chapter 4 exercise.

### Step 2 – Provide the Data to Copilot

Use the Copilot capability described in the chapter to provide the relevant operational information.

The objective is to ask Copilot to summarize the data rather than reproduce every individual record.

For example, a request could be:

```text
Summarize the operational data and highlight the most important items that require attention.
```

### Step 3 – Review the Summary

Review the generated summary before using it in a business process.

Conceptually:

```text
Operational Data
       ↓
Copilot
       ↓
Generated Summary
       ↓
Human Review
```

The summary should be checked for completeness, relevance, and accuracy.

### Step 4 – Use the Summary

The generated summary can then be used as part of a reporting or communication process.

For example:

```text
Generated Summary
       ↓
Review
       ↓
Send Report
       ↓
Share with Stakeholders
```

## Example

Suppose operational data contains multiple records relating to tasks and their status.

Instead of reviewing every record individually, Copilot can be asked to provide a concise summary.

For example:

```text
Summarize the following operational data.
Identify the major completed items,
items still in progress, and items
that may require attention.
```

The resulting summary can provide a high-level view of the operational status.

## Example Business Summary

A generated summary might be organized into sections such as:

```text
Completed
- Completed operational tasks

In Progress
- Tasks currently being worked on

Needs Attention
- Items that may require follow-up
```

The exact output should depend on the information contained in the source data.

## Validation

A Copilot-generated summary should be reviewed before it is used for important business communication or decisions.

Check:

- The summary accurately reflects the source data.
- Important information has not been omitted.
- The summary does not introduce unsupported conclusions.
- Items requiring attention are identified correctly.

A simple validation process is:

```text
Source Data
     ↓
Copilot Summary
     ↓
Human Review
     ↓
Approved → Use Summary
Needs Review → Recheck Source Data
```

## Testing

### Test 1 – Small Dataset

Provide a small set of operational records.

Expected result:

Copilot produces a concise summary of the supplied information.

### Test 2 – Larger Dataset

Provide a larger operational dataset.

Expected result:

The summary should focus on the important information rather than simply repeating every record.

### Test 3 – Data Requiring Attention

Include records containing items that may require follow-up.

Expected result:

The generated summary should make those items visible for review.

## Common Issues

### Summary Is Too General

Refine the request by specifying what should be included.

For example:

```text
Summarize the data and focus on
items that are overdue or require attention.
```

### Important Information Is Missing

Review the source data and refine the prompt to identify the information that must appear in the summary.

### Summary Contains an Incorrect Conclusion

Compare the generated summary with the original data and verify the underlying records.

Do not rely on a generated summary without checking important information against the source.

## Design Considerations

When using Copilot for data summarization:

- Define the purpose of the summary clearly.
- Specify the information that should be highlighted.
- Review generated content before distribution.
- Keep the original source data available for verification.
- Avoid using summaries as the sole basis for high-impact decisions.

## Security and Data Considerations

Operational reports may contain sensitive business information.

Review:

- Who can access the source data.
- Who can access the generated summary.
- Whether confidential information is included.
- Where the summary is stored or shared.
- Applicable data retention requirements.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

- [Chapter 4 – Intelligent Automation, AI Builder and Copilot](../README.md)
- [Form Processing with AI Builder](../AIBuilder/FormProcessing.md)
- [Invoice Processing with AI Builder](../AIBuilder/InvoiceProcessing.md)
- [OCR Examples](../AIBuilder/OCRExamples.md)
- [Sentiment Analysis](../AIBuilder/SentimentAnalysis.md)

## Notes

This example is intended to accompany the Copilot data-summarization section of Chapter 4 in *Learning Microsoft Power Automate*.

The current repository defines this topic as **summarizing operational data and reports**.

The exact Copilot capability, source data, prompt, and downstream process should follow the implementation described in the book.