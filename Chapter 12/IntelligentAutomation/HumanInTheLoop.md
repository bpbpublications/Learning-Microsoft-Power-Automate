# Human-in-the-Loop Automation

## Overview

Human-in-the-loop automation combines automated processing with human review at points where judgment, exception handling, or approval is required.

## Pattern

```text
Automated Processing
        ↓
Confidence / Business Rule
        ↓
Meets Criteria? ── Yes ──→ Continue Automation
        │
        No
        ↓
Human Review
        ↓
Decision
        ↓
Continue or Escalate
```

## Suitable Scenarios

- AI extraction requiring validation
- Sensitive business decisions
- Exceptions that cannot be resolved automatically
- Approvals
- Low-confidence classifications

## Design Considerations

Define who reviews the item, what information is presented, what decision is required, and what happens if the reviewer does not respond.

## Related Resources

- [Intelligent Automation](README.md)
- [Responsible AI](../ResponsibleAI/README.md)
