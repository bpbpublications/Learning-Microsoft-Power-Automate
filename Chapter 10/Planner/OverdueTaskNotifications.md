# Planner Overdue Task Notifications

## Overview

Power Automate can identify overdue work and notify task owners or support teams.

## Pattern

```text
Scheduled Trigger
      ↓
Read Tasks
      ↓
Find Overdue Tasks
      ↓
Notify Owner
      ↓
Record / Escalate
```

## Best Practices

- Run at an appropriate frequency.
- Avoid repeatedly notifying about the same task.
- Include the task title and due date.
- Define escalation rules for critical work.
- Respect organizational communication policies.
