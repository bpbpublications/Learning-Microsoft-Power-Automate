# Dynamic Selector Patterns

## Overview

This example demonstrates common matching patterns that can make selectors more flexible in **Power Automate for desktop**.

The resource covers `Contains`, `StartsWith`, and regular-expression selector patterns. 

## Scenario

Suppose an application contains values that change between executions, such as:

```text
Invoice - INV-1001
Invoice - INV-1002
Invoice - INV-1003
```

An exact-match selector can become difficult to maintain when the dynamic portion changes.

Matching patterns can allow the selector to identify the target without requiring a separate selector for every value.

## `Contains`

Use `Contains` when a stable portion of the attribute value is known.

For example, given:

```text
Invoice - INV-1001
```

an appropriate `Contains` match could target:

```text
Invoice -
```

Conceptually:

```text
Full Attribute Value
        ↓
Contains stable text
        ↓
Target UI Element
```

### When to Use `Contains`

`Contains` is useful when only part of the attribute value is stable and that text is sufficient to identify the intended element.

## `StartsWith`

Use `StartsWith` when the beginning of an attribute remains stable.

For example:

```text
Invoice - INV-1001
Invoice - INV-1002
Invoice - INV-1003
```

The common prefix is:

```text
Invoice -
```

The selector can use the stable beginning of the value while allowing the invoice number to change.

### When to Use `StartsWith`

Use this pattern when the target attribute consistently begins with the same text.

## Regular Expressions

Use a regular expression when the dynamic portion follows a predictable pattern.

For example:

```regex
INV-\d+
```

can match:

```text
INV-1001
INV-1002
INV-99999
```

Regex is covered in more detail in [Regex Examples](RegexExamples.md).

## Comparing the Patterns

| Pattern | Best Use |
|---|---|
| Exact Match | Entire value is stable |
| `Contains` | A known portion appears somewhere in the value |
| `StartsWith` | The beginning of the value is stable |
| Regex | The dynamic value follows a predictable pattern |

Use the simplest pattern that reliably identifies the target.

## Exercise

### Step 1 – Identify the Dynamic Value

Identify which portion of the selector value changes between runs.

For example:

```text
Invoice - INV-1001
Invoice - INV-1002
```

The invoice number is dynamic.

### Step 2 – Identify the Stable Portion

Determine which part remains unchanged.

In this example:

```text
Invoice -
```

is stable.

### Step 3 – Choose the Matching Pattern

Choose the appropriate strategy:

```text
Stable Full Value
       ↓
   Exact Match

Partial Stable Text
       ↓
     Contains

Stable Prefix
       ↓
    StartsWith

Predictable Pattern
       ↓
       Regex
```

### Step 4 – Test the Selector

Test the selector with multiple values rather than a single example.

## Example

Consider these window titles:

```text
Customer - CUST-1001
Customer - CUST-1002
Customer - CUST-1003
```

Possible strategies include:

```text
Contains:    Customer
StartsWith:  Customer -
Regex:       CUST-\d+
```

The correct choice depends on the selector attribute and how uniquely it identifies the target element.

## Testing

### Test 1 – Matching Value

Provide a value that contains the expected stable text.

**Expected result:** The selector identifies the intended element.

### Test 2 – Different Dynamic Value

Change the dynamic portion and run the flow again.

**Expected result:** The same matching strategy continues to identify the intended target.

### Test 3 – Similar but Incorrect Value

Provide another element with similar text.

**Expected result:** The selector remains specific enough to avoid selecting the wrong element.

## Common Issues

### Too Many Elements Match

Make the selector more specific by combining the matching pattern with another stable attribute.

### `Contains` Is Too Broad

Replace it with `StartsWith`, an exact match, or a more specific regex where appropriate.

### Regex Is Too Complex

Simplify the expression if a basic `Contains` or `StartsWith` pattern is sufficient.

## Best Practices

- Start with the simplest reliable matching method.
- Prefer stable attributes.
- Use `Contains` only when broad matching is appropriate.
- Use `StartsWith` when a stable prefix exists.
- Use regex for predictable dynamic structures.
- Test against multiple runtime values.
- Avoid selectors that can match multiple unintended elements.

## Related Resources

- [Dynamic Selectors](README.md)
- [Dynamic Variables](DynamicVariables.md)
- [Regex Examples](RegexExamples.md)

## Notes

The exact selector syntax and matching options available can vary depending on the Power Automate for desktop version and the application being automated.