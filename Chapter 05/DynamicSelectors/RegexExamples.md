# Regex Examples for Dynamic Selectors

## Overview

This example demonstrates how regular expressions can be used to match dynamic values in selectors when simpler matching patterns are not sufficient.

The current example focuses on a pattern such as:

```text
 document:eq(\d+)
```

The `\d+` portion represents one or more digits.

## Scenario

Suppose an application contains identifiers such as:

```text
Document:EQ123
Document:EQ456
Document:EQ789
```

A fixed selector would match only one specific identifier.

A regular expression can be used when the numeric portion changes between executions.

## Exercise

### Step 1 – Identify the Dynamic Pattern

Separate the stable portion from the changing portion.

For example:

```text
EQ123
EQ456
EQ789
```

The letters remain consistent while the numbers change.

### Step 2 – Define the Regular Expression

A pattern such as:

```regex
EQ\d+
```

can represent the changing numeric identifier.

Here:

| Pattern | Meaning |
|---|---|
| `EQ` | Matches the literal text `EQ` |
| `\d` | Matches a digit |
| `+` | Matches one or more occurrences |

### Step 3 – Apply the Pattern

Use the regular-expression matching option supported by the selector editor for the target attribute.

Conceptually:

```text
Dynamic Attribute
       ↓
Regex Pattern
       ↓
Matching UI Element
```

The exact selector syntax depends on the application and selector technology used in the exercise.

## Example

Suppose the value is:

```text
EQ456
```

The pattern:

```regex
EQ\d+
```

matches the value because it starts with `EQ` and is followed by one or more digits.

The same pattern can also match:

```text
EQ123
EQ789
EQ10001
```

## More Regex Examples

### Match Digits Only

```regex
\d+
```

Matches one or more digits.

Examples:

```text
123
4567
10001
```

### Match a Fixed Prefix and Digits

```regex
INV-\d+
```

Matches invoice identifiers such as:

```text
INV-1001
INV-2500
INV-99999
```

### Match a Case Identifier

```regex
CASE-\d+
```

Matches values such as:

```text
CASE-1001
CASE-2050
```

## Testing

### Test 1 – Matching Value

Provide a value that follows the expected pattern.

Expected result:

The selector identifies the intended element.

### Test 2 – Different Numeric Value

Change the numeric portion while keeping the pattern consistent.

Expected result:

The same regex continues to match the target.

### Test 3 – Non-Matching Value

Provide a value that does not match the pattern.

Example:

```text
ABC456
```

Expected result:

The regex does not match, and the flow should handle the missing target appropriately.

## Regex vs Simple Matching

Use the simplest selector strategy that reliably satisfies the requirement.

```text
Exact Match
     ↓
Contains / StartsWith
     ↓
Regex
```

Regular expressions are powerful, but they can make selectors harder to understand and maintain.

## Common Issues

### Regex Matches Too Much

Make the expression more specific.

For example, instead of:

```regex
\d+
```

use:

```regex
INV-\d+
```

when the expected value must begin with `INV-`.

### Regex Does Not Match

Check:

- The actual attribute value.
- Escaping of special characters.
- Whether the selector editor expects a regex or plain text pattern.
- Whether the target application exposes the expected attribute.

## Best Practices

- Use exact matching when the value is stable.
- Use `Contains` or `StartsWith` for simple dynamic text.
- Use regex when the changing pattern has a predictable structure.
- Keep expressions as simple as possible.
- Test matching and non-matching values.
- Document complex patterns for maintainability.

## Related Resources

- [Dynamic Selectors](README.md)
- [Dynamic Variables](DynamicVariables.md)
- [Selector Patterns](SelectorPatterns.md)

## Notes

The current resource contains a `document:eq(\d+)` regex example. This article expands that concept into practical regex patterns for dynamic selector matching. fileciteturn93file0L2-L6