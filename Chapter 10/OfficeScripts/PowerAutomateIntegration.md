# Office Scripts and Power Automate Integration

## Overview

Power Automate can invoke Office Scripts as part of an Excel automation process.

## Integration Pattern

```text
Power Automate Trigger
        ↓
Prepare Inputs
        ↓
Run Office Script
        ↓
Receive Result
        ↓
Continue Flow
```

## Design Considerations

Define the script's expected inputs and outputs before integrating it into the flow.

Validate the workbook structure and handle script errors explicitly.

## Testing

Test the script independently and then test the complete flow with representative workbooks.

## Security

Use approved workbooks and connections. Do not store secrets in scripts or workbook cells.
