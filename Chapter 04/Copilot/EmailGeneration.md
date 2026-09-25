# Email Generation with Copilot

## Overview

This example demonstrates how **Copilot** can help generate professional follow-up emails from business information.

Instead of writing every follow-up email manually, Copilot can help create a draft based on the context, key details, and intended outcome.

## Scenario

Consider a business process where a user needs to send follow-up emails after a meeting, customer interaction, request, or business activity.

A typical process can be represented as:

```text
Business Information
       ↓
Copilot
       ↓
Generate Email Draft
       ↓
Review and Edit
       ↓
Send Email
```

## What Email Generation Provides

Copilot can help transform business information into a structured email draft.

The generated email can include:

- A suitable subject
- Greeting
- Summary of the discussion or request
- Required follow-up actions
- Next steps
- Professional closing

The exact output depends on the information provided and the Copilot capability used in the exercise.

## Exercise

### Step 1 – Prepare the Information

Provide the information required to create the follow-up email.

For example:

```text
Customer: ABC Industries
Meeting: Project Status Review
Discussion: Project delivery is delayed by one week.
Action: Customer will provide the remaining requirements.
Next Step: Schedule a follow-up meeting next week.
```

The actual information should follow the example used in the corresponding Chapter 4 exercise.

### Step 2 – Provide the Context to Copilot

Use the Copilot capability described in the chapter to provide the relevant business information.

For example:

```text
Create a professional follow-up email based on the information provided.
Summarize the discussion, mention the agreed action,
and include the next step.
```

### Step 3 – Review the Generated Draft

Review the generated email before sending it.

Conceptually:

```text
Business Information
       ↓
Copilot
       ↓
Email Draft
       ↓
Human Review
```

Check that the draft accurately represents the original information.

### Step 4 – Edit and Send

Make any required corrections or additions before sending the email.

The final process is:

```text
Generated Draft
       ↓
Review
       ↓
Edit if Required
       ↓
Send Email
```

## Example

Suppose the business information is:

```text
Customer: ABC Industries
Meeting: Project Status Review

Discussion:
Project delivery is delayed by one week.

Action:
Customer will provide the remaining requirements.

Next Step:
Schedule a follow-up meeting next week.
```

Copilot can generate a professional follow-up email based on this information.

A possible structure is:

```text
Subject: Follow-Up – Project Status Review

Hello Team,

Thank you for the discussion during the project status review.

As discussed, the project delivery is expected to be delayed by one week.
The remaining requirements will be provided by the customer.

We will schedule a follow-up meeting next week to review the progress.

Regards,
[Name]
```

The generated content should always be reviewed before it is sent.

## Improving the Prompt

A more specific request can improve the generated email.

For example:

```text
Create a professional and concise follow-up email.
Mention the project delay, the agreed customer action,
and the next meeting. Keep the tone polite and business-focused.
```

The request can specify:

- Tone
- Length
- Audience
- Important information
- Required actions
- Next steps

## Validation

A Copilot-generated email should be reviewed before sending.

Check:

- The recipient is correct.
- The subject accurately describes the message.
- Business facts are correct.
- Dates and actions are correct.
- No unsupported information has been added.
- The tone is appropriate for the recipient.

A simple process is:

```text
Generated Email
       ↓
Check Facts
       ↓
Check Recipients
       ↓
Check Tone
       ↓
Approve → Send
Review → Edit
```

## Testing

### Test 1 – Standard Follow-Up

Provide normal business meeting information.

Expected result:

Copilot generates a professional follow-up email containing the important discussion points and next steps.

### Test 2 – Short Input

Provide only a small amount of business information.

Expected result:

Copilot generates a concise draft, but the result should be reviewed to ensure important details are not missing.

### Test 3 – Multiple Actions

Provide several agreed actions.

Expected result:

The generated email should clearly communicate the relevant actions and responsibilities.

## Common Issues

### Email Is Too General

Provide more context in the request.

For example:

```text
Create a concise follow-up email.
Include the project name, agreed action,
responsible party, and next meeting date.
```

### Important Information Is Missing

Review the source information and refine the prompt to explicitly identify what must be included.

### Email Contains Incorrect Information

Compare the generated draft with the original business information.

Correct any unsupported or inaccurate statements before sending.

### Tone Is Not Appropriate

Specify the desired tone.

For example:

```text
Use a professional, polite, and concise tone.
```

## Design Considerations

When using Copilot for email generation:

- Provide sufficient context.
- Specify the intended audience.
- Define the desired tone.
- Identify mandatory information.
- Review the generated content before sending.
- Keep the original business information available for verification.

## Security and Data Considerations

Business emails may contain customer, employee, or confidential information.

Review:

- Who provides the source information.
- Who can view the generated draft.
- Whether sensitive information is included.
- Who is authorized to send the final email.

Do not include passwords, API keys, credentials, or other secrets in prompts or repository files.

## Related Resources

- [Chapter 4 – Intelligent Automation, AI Builder and Copilot](../README.md)
- [Data Summarization with Copilot](DataSummarization.md)
- [Form Processing with AI Builder](../AIBuilder/FormProcessing.md)
- [Sentiment Analysis](../AIBuilder/SentimentAnalysis.md)

## Notes

This example is intended to accompany the Copilot email-generation section of Chapter 4 in *Learning Microsoft Power Automate*.

The current repository defines this topic as **generating professional follow-up emails**.

The exact Copilot capability, source information, prompt, and email-sending implementation should follow the corresponding implementation described in the book.