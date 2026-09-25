# Python Integration

Python can complement Power Automate when a task benefits from code-based processing, reusable business logic, specialized libraries, or data transformation that would otherwise make a flow difficult to maintain.

## Typical pattern

```text
Power Automate
      ↓
Input data
      ↓
Python processing
      ↓
Validated result
      ↓
Continue automation
```

## Common uses

- Data transformation.
- Text processing.
- Calculations.
- Validation.
- File processing.
- Preparing structured output for a flow.
- Specialized logic or model inference.

## Resources

- [Python Fundamentals](PythonFundamentals.md)
- [Data Transformation](DataTransformation.md)
- [Error Handling](ErrorHandling.md)
- [Power Automate Integration](PowerAutomateIntegration.md)
- [Flask Transformation Service](FlaskTransformService.md)
- [Azure Functions Integration](AzureFunctionsIntegration.md)
- [Direct HTTP API Integration](DirectHttpApiIntegration.md)
- [Choosing an Integration Approach](IntegrationApproach.md)

## Design principle

Use Python where it provides a clear advantage. Keep the interface between Power Automate and Python explicit, predictable, and testable.

Never hard-code passwords, tokens, connection strings, or production data in Python source files.
