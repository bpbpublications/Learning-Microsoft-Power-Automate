# Outlook Email Automation

## Overview

Power Automate can automate common Outlook email activities such as sending notifications, processing incoming messages, and creating follow-up tasks.

## Typical Pattern

```text
Trigger
  ↓
Read Email Information
  ↓
Apply Conditions
  ↓
Perform Action
  ↓
Log or Notify
```

## Common Scenarios

- Send an approval notification.
- Process incoming emails.
- Send scheduled reminders.
- Create follow-up tasks from messages.
- Route messages based on subject or sender.

## Best Practices

- Validate recipients before sending.
- Avoid accidental duplicate emails.
- Use clear subjects and meaningful message content.
- Protect sensitive information.
- Test with controlled recipients before production use.

## Security

Use approved Outlook connections and appropriate permissions. Never place passwords, tokens, or secrets in email content or repository samples.
