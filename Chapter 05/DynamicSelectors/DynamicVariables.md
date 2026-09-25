# Dynamic Variables in Selectors

## Overview

This example demonstrates how runtime variables can be used when working with dynamic selectors in **Power Automate for desktop**.

Dynamic values are useful when an application property changes between runs, such as a window title, document number, customer identifier, or other runtime value.

The example focuses on using a value such as `%WindowName%` as part of a selector strategy.

## Scenario

Suppose an application window contains a runtime value in its title:

```text
Invoice - INV-1001
Invoice - INV-1002
Invoice - INV-1003
```

A selector that contains a fixed invoice number may work for only one run.

Instead, the flow can use a runtime variable to represent the changing value.

```text
Runtime Value
     ↓
Variable
     ↓
Dynamic Selector
     ↓
Target UI Element
```

## Exercise

### Step 1 – Create the Runtime Variable

Create or obtain a variable containing the value that changes between executions.

For example:

```text
%WindowName%
```

The actual variable name should match the Desktop Flow implementation.

### Step 2 – Identify the Stable Selector Attribute

Capture the target UI Element and identify the attribute that remains useful for locating the intended element.

Separate stable information from the portion that changes at runtime.

For example:

```text
Invoice - INV-1001
Invoice - INV-1002
Invoice - INV-1003
```

The invoice number is dynamic, while the surrounding title text remains consistent.

### Step 3 – Build the Dynamic Selector

Use the runtime variable in the selector where the value changes.

Conceptually:

```text
Stable Attribute + Runtime Variable
                ↓
        Dynamic Selector
                ↓
         Target Element
```

The exact selector syntax should follow the selector editor and application used in the exercise.

### Step 4 – Test Multiple Runtime Values

Run the Desktop Flow using different values.

For example:

```text
INV-1001
INV-1002
INV-1003
```

The selector should continue to identify the intended element when the dynamic value changes.

## Example

Suppose the target window title is stored in:

```text
%WindowName%
```

and the value changes between executions.

The flow can use the variable as part of the selector strategy rather than creating a separate selector for every possible title.

## Why Use Dynamic Variables?

Dynamic variables can make selectors more reusable when values are not known until runtime.

They can be useful for:

- Window titles.
- Document numbers.
- Customer IDs.
- Order numbers.
- Case numbers.
- Other generated identifiers.

## Testing

### Test 1 – First Runtime Value

Use one valid runtime value.

Expected result:

The selector identifies the intended UI Element.

### Test 2 – Different Runtime Value

Change the runtime value and rerun the flow.

Expected result:

The same selector strategy identifies the corresponding target.

### Test 3 – Invalid Runtime Value

Provide a value that does not correspond to an available target.

Expected result:

The selector should fail to identify the target, and the flow should handle the condition appropriately.

## Common Issues

### Selector Works Only for One Value

Check whether the selector still contains a hard-coded dynamic value.

Replace the changing portion with the appropriate runtime variable or matching strategy.

### Variable Value Is Not Available

Check:

- The variable is initialized before the selector is used.
- The variable contains the expected value.
- The variable name is correct.

### Multiple Elements Match

Make the selector more specific by combining the dynamic value with stable attributes.

## Best Practices

- Use variables only for values that genuinely change.
- Keep stable selector attributes unchanged.
- Test more than one runtime value.
- Make selectors specific enough to identify the intended element.
- Avoid replacing the entire selector with a dynamic expression when only one attribute needs to change.

## Related Resources

- [Dynamic Selectors](README.md)
- [Selector Patterns](SelectorPatterns.md)
- [Regex Examples](RegexExamples.md)

## Notes

The current resource introduces the use of `%WindowName%` and runtime variables in selectors. This article expands that concept into a practical Desktop Flow exercise. fileciteturn92file0L2-L6