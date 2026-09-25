# Power Fx Conditions

## Overview

This resource provides practical examples of using conditional logic in **Power Fx**.

Conditional expressions allow an application or automation to make decisions based on values, status, user input, or other conditions.

## Simple `If`

Use `If` when a condition has two possible outcomes.

```powerfx
If(
    OrderAmount > 1000,
    "Manager Approval Required",
    "Auto Approved"
)
```

This example returns:

- `Manager Approval Required` when `OrderAmount` is greater than 1000.
- `Auto Approved` otherwise.

## Multiple Conditions

`If` can also evaluate multiple conditions.

```powerfx
If(
    OrderAmount > 10000,
    "Director Approval",
    OrderAmount > 5000,
    "Manager Approval",
    "Auto Approved"
)
```

The conditions are evaluated in order:

```text
OrderAmount > 10000 → Director Approval
OrderAmount > 5000  → Manager Approval
Otherwise           → Auto Approved
```

## `Switch`

Use `Switch` when the result depends on the value of a single expression.

```powerfx
Switch(
    Status,
    "Approved", "Send Confirmation",
    "Rejected", "Notify Employee",
    "Pending", "Await Decision",
    "Unknown Status"
)
```

Example behavior:

| Status | Result |
|---|---|
| Approved | Send Confirmation |
| Rejected | Notify Employee |
| Pending | Await Decision |
| Any other value | Unknown Status |

## Checking for Blank Values

Use `IsBlank` to determine whether a value is empty.

```powerfx
If(
    IsBlank(CustomerName),
    "Customer Missing",
    "Customer Found"
)
```

This can be useful when validating form or user-input data before continuing with an operation.

## Boolean Conditions

A Boolean value can be evaluated directly.

```powerfx
If(
    IsApproved,
    "Processed",
    "Pending"
)
```

If `IsApproved` is `true`, the result is `Processed`.

If `IsApproved` is `false`, the result is `Pending`.

## Role-Based Routing

Conditional logic can also be used to control navigation or application behavior.

```powerfx
If(
    UserRole = "Admin",
    Navigate(AdminScreen),
    Navigate(HomeScreen)
)
```

This example sends administrators to `AdminScreen` and other users to `HomeScreen`.

## Error Handling with `IfError`

`IfError` can be used to handle errors that occur while evaluating an expression.

```powerfx
IfError(
    Value(TextInput1.Text),
    Notify(
        "Invalid Number",
        NotificationType.Error
    )
)
```

In this example, the text entered in `TextInput1` is converted to a numeric value.

If the conversion fails, the user receives an error notification.

## Choosing the Right Function

Use the appropriate conditional function based on the requirement:

| Requirement | Recommended Function |
|---|---|
| Two possible outcomes | `If` |
| Multiple conditions | `If` |
| Multiple outcomes based on one value | `Switch` |
| Check whether a value is empty | `IsBlank` |
| Handle an expression error | `IfError` |

## Practice Examples

Try modifying the examples with different values.

For example, change:

```powerfx
OrderAmount > 1000
```

to:

```powerfx
OrderAmount >= 1000
```

Then test how the result changes when the order amount is exactly `1000`.

You can also add additional business rules to the multiple-condition example.

## Notes

These examples are intended to accompany the Power Fx sections of Chapter 2 in *Learning Microsoft Power Automate*.

The examples in this resource cover:

- `If`
- Multiple conditions
- `Switch`
- `IsBlank`
- Boolean checks
- Role-based routing
- `IfError`
