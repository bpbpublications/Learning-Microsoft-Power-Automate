# Sentiment Analysis

## Overview

This example demonstrates how sentiment analysis can be used to evaluate **customer feedback** and identify whether the feedback expresses a positive, negative, or other sentiment.

Sentiment analysis can help organizations process large amounts of customer feedback and use the results to support follow-up actions.

## Scenario

Consider a business that receives customer feedback through forms, emails, surveys, or other channels.

Manually reading every response can be time-consuming when the volume of feedback is high.

Sentiment analysis can be incorporated into a Power Automate process:

```text
Customer Feedback
       ↓
Sentiment Analysis
       ↓
Determine Sentiment
       ↓
Use Result in Business Process
```

## What Sentiment Analysis Does

Sentiment analysis evaluates text and provides an indication of the sentiment expressed in the content.

For example, customer feedback may contain:

```text
"The service was excellent and the issue was resolved quickly."
```

The analysis can identify the feedback as positive.

Another example:

```text
"I am unhappy with the delay and the support I received."
```

The analysis can identify the feedback as negative.

The exact output and confidence information depend on the sentiment-analysis capability and configuration used in the exercise.

## Exercise

### Step 1 – Prepare Customer Feedback

Provide sample customer feedback for analysis.

Examples include:

```text
The support team was very helpful.
```

```text
The issue took too long to resolve.
```

```text
The product is acceptable, but delivery could be faster.
```

### Step 2 – Add Sentiment Analysis

In the Power Automate flow, configure the appropriate sentiment-analysis capability used in the chapter exercise.

Provide the customer feedback text as the input.

The exact action and configuration should follow the implementation described in the corresponding Chapter 4 section.

### Step 3 – Analyze the Feedback

Run the sentiment-analysis action.

Conceptually:

```text
Customer Feedback
       ↓
Sentiment Analysis
       ↓
Sentiment Result
```

The result can then be used by subsequent Power Automate actions.

### Step 4 – Use the Result

The sentiment result can be used to determine the next step in the process.

For example:

```text
Sentiment Result
       ↓
Positive → Record Feedback
Negative → Create Follow-Up
Other    → Review Feedback
```

The actual business logic should follow the scenario implemented in the chapter.

## Example

Consider the following customer feedback:

```text
Customer Feedback:
"The support team was very helpful and resolved my issue quickly."
```

The sentiment-analysis capability processes the text and returns a sentiment result.

The flow can then use that result to:

- Store the feedback.
- Notify a team.
- Update a customer record.
- Trigger a follow-up process.

## Example: Negative Feedback

Suppose the feedback is:

```text
Customer Feedback:
"I am disappointed with the service and the delay in resolving my issue."
```

The sentiment result can be used to route the feedback for follow-up.

For example:

```text
Negative Sentiment
       ↓
Create Follow-Up Task
       ↓
Notify Support Team
```

## Validation

Sentiment analysis should be treated as an input to the business process rather than an unquestionable decision.

Consider validating:

- Whether the feedback contains enough text for meaningful analysis.
- Whether the sentiment result is appropriate for the business scenario.
- Whether negative or uncertain feedback requires human review.

A simple process can be:

```text
Sentiment Result
       ↓
Validate Result
       ↓
Accept → Continue
Review → Human Assessment
```

## Testing

### Test 1 – Positive Feedback

Input:

```text
The support team was excellent and solved my problem quickly.
```

Expected result:

The analysis identifies the feedback as positive or otherwise reflects a favorable sentiment.

### Test 2 – Negative Feedback

Input:

```text
I am unhappy with the service and the long delay.
```

Expected result:

The analysis identifies the feedback as negative or otherwise reflects an unfavorable sentiment.

### Test 3 – Mixed Feedback

Input:

```text
The product is good, but the delivery experience was disappointing.
```

Expected result:

The analysis should return the sentiment result provided by the configured capability. Review the result before using it for important business decisions.

## Common Issues

### Sentiment Is Not Returned

Check:

- The feedback text is available.
- The correct sentiment-analysis capability is configured.
- The input is passed correctly to the analysis action.

### Result Does Not Match Expectations

Consider:

- The wording and context of the feedback.
- Whether the feedback contains mixed opinions.
- Whether additional business rules are required.
- Whether human review is appropriate.

### Very Short Feedback

Very short responses such as:

```text
Good
```

or:

```text
Bad
```

may provide less context for downstream interpretation.

Define business rules for handling short or ambiguous feedback where necessary.

## Design Considerations

When using sentiment analysis:

- Define how positive and negative feedback should be handled.
- Provide an exception path for uncertain or mixed feedback.
- Avoid using sentiment alone for high-impact decisions.
- Combine sentiment with other business information where appropriate.
- Keep human review available when the outcome requires judgment.

## Security and Data Considerations

Customer feedback may contain personal or sensitive business information.

Review:

- Who can submit feedback.
- Who can access the feedback.
- Who can access the sentiment result.
- Where the original feedback and analysis results are stored.
- Applicable retention requirements.

Do not store passwords, API keys, credentials, or other secrets in this repository.

## Related Resources

- [Chapter 4 – Intelligent Automation, AI Builder and Copilot](../README.md)
- [Form Processing with AI Builder](FormProcessing.md)
- [Invoice Processing with AI Builder](InvoiceProcessing.md)
- [OCR Examples](OCRExamples.md)

## Notes

This example is intended to accompany the sentiment-analysis section of Chapter 4 in *Learning Microsoft Power Automate*.

The current repository defines this topic as **analyzing customer feedback sentiment**.

The exact sentiment-analysis capability, action, input source, and downstream processing should follow the implementation described in the book.