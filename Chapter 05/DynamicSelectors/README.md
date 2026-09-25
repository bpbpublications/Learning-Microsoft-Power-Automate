# Dynamic Selectors

## Overview

This folder contains examples for building more flexible and resilient selectors in **Power Automate for desktop**.

Dynamic selectors are useful when application properties change at runtime or when a selector must adapt to values that are known only while the flow is running.

## Resources

| File | Purpose |
|---|---|
| [Dynamic Variables](DynamicVariables.md) | Use runtime variables in selectors |
| [Selector Patterns](SelectorPatterns.md) | Use `Contains`, `StartsWith`, and related matching patterns |
| [Regex Examples](RegexExamples.md) | Use regular expressions for dynamic selector matching |

## Recommended Learning Order

```text
Runtime Variables
       ↓
Selector Patterns
       ↓
Regular Expressions
       ↓
Resilient Dynamic Selectors
```

Start with runtime variables, then move to selector matching patterns and regular expressions.

## When to Use Dynamic Selectors

Dynamic selectors are useful when:

- A window title changes between runs.
- A control contains a variable identifier.
- A page contains generated or changing text.
- Multiple similar controls must be distinguished by runtime values.
- A fixed selector is too restrictive.

## Example

Suppose an application window title contains a changing value:

```text
Invoice - INV-1001
Invoice - INV-1002
Invoice - INV-1003
```

Instead of creating a separate selector for every invoice, a runtime variable can be used to build or match the selector dynamically.

## Best Practices

- Prefer stable UI attributes whenever possible.
- Use variables only for values that genuinely change.
- Keep selectors specific enough to identify the intended element.
- Prefer simple matching patterns before using regular expressions.
- Test selectors with multiple runtime values.
- Avoid relying on fragile attributes that change between executions.

## Related Resources

- [Chapter 5 – Advanced Power Automate Desktop](../README.md)
- [Advanced UI Automation](../AdvancedUIAutomation/README.md)

## Notes

These resources are intended to accompany the dynamic-selector section of Chapter 5 in *Learning Microsoft Power Automate*.

The exact selector syntax and available matching options may vary depending on the Power Automate for desktop version and the application being automated.