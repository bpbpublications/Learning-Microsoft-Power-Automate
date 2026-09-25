# Planner Task Assignment

## Overview

Task assignment can be automated when a business process determines who should perform the next activity.

## Assignment Pattern

```text
Business Rule
     ↓
Determine Owner
     ↓
Create / Update Task
     ↓
Notify Owner
```

## Design Considerations

- Define assignment rules clearly.
- Handle users who are unavailable or no longer members of the plan.
- Avoid assigning duplicate work.
- Keep task descriptions concise but useful.
- Validate that the target plan and bucket are correct.
