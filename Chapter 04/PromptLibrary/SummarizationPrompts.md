# Summarization Prompts

## Overview

This prompt library provides reusable examples for summarizing **documents, meeting notes, operational updates, and business reports** with Copilot.

The prompts focus on producing concise summaries while keeping important information visible for review and follow-up.

## Summarize a Document

Use this prompt when a document needs a concise summary.

```text
Summarize the document provided.
Highlight the main points, important decisions,
and information that may require follow-up.
Keep the summary concise and factual.
```

## Summarize Meeting Notes

```text
Summarize these meeting notes.
Identify the key discussion points, decisions,
action items, responsible parties, and next steps.
Do not add information that is not present in the notes.
```

## Executive Summary

```text
Create an executive summary of the information provided.
Focus on the most important outcomes, risks, decisions,
and actions that require management attention.
Keep the summary concise and business-focused.
```

## Operational Summary

```text
Summarize the operational data provided.
Highlight completed items, work in progress,
and items that require attention.
Focus on information that may require follow-up.
```

## Customer Interaction Summary

```text
Summarize the customer interaction.
Include the main issue or request, important discussion points,
agreed actions, and next steps.
Keep the summary professional and concise.
```

## Summary with a Specific Format

The expected output can be defined explicitly.

For example:

```text
Summarize the information using these sections:

Overview
Key Points
Decisions
Action Items
Next Steps

Keep each section concise.
Use only information present in the source.
```

## Prompt Guidelines

A stronger summarization prompt usually specifies:

- What should be summarized.
- The intended audience.
- The important information to highlight.
- The required output format.
- Desired length or level of detail.
- Whether unsupported information should be excluded.

For example:

```text
Summarize the operational report for a management audience.
Highlight completed work, delays, risks, and actions requiring attention.
Use concise bullet points and do not add information not present in the report.
```

## Review the Generated Summary

Generated summaries should be reviewed before they are used for important communication or decisions.

Check:

- The summary accurately reflects the source.
- Important information has not been omitted.
- No unsupported conclusions were introduced.
- Dates, figures, and actions are correct.

## Related Resources

- [Data Summarization with Copilot](../Copilot/DataSummarization.md)
- [Email Generation with Copilot](../Copilot/EmailGeneration.md)
- [Extraction Prompts](ExtractionPrompts.md)

## Notes

These prompts are examples for the Chapter 4 exercises. Adapt the wording and output structure to the business scenario and Copilot capability used in the book.