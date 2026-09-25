# Power Fx Variables

## Overview

This resource provides practical examples of creating, reading, updating, and using variables in **Power Fx**.

Variables allow values to be stored and reused throughout an expression or application.

## Set a Variable

Use `Set` to create or update a variable.

For example:

```powerfx
Set(
    CustomerName,
    "Balaji"
)
```

A numeric value can also be stored:

```powerfx
Set(
    OrderAmount,
    2500
)
```

A Boolean value can be stored as well:

```powerfx
Set(
    IsApproved,
    true
)
```

## Read Variables

Once a variable has been created, reference its name to use its value.

```powerfx
CustomerName
```

```powerfx
OrderAmount
```

```powerfx
IsApproved
```

For example, if:

```powerfx
Set(
    CustomerName,
    "Balaji"
)
```

then:

```powerfx
CustomerName
```

returns:

```text
Balaji
```

## Update a Variable

The same `Set` function can be used to update an existing variable.

For example:

```powerfx
Set(
    OrderAmount,
    OrderAmount + 500
)
```

If `OrderAmount` is initially `2500`, the updated value becomes:

```text
3000
```

## Use Variables in Conditional Logic

Variables can be used with Power Fx functions such as `If`.

```powerfx
If(
    IsApproved,
    "Approved",
    "Pending"
)
```

If `IsApproved` is `true`, the result is:

```text
Approved
```

Otherwise, the result is:

```text
Pending
```

## Store the Current Date

A variable can also store a date value.

```powerfx
Set(
    CurrentDate,
    Today()
)
```

The variable can then be referenced later:

```powerfx
CurrentDate
```

## Concatenate Variables

Variables can be combined with text using the `&` operator.

```powerfx
Set(
    WelcomeMessage,
    "Welcome " & CustomerName
)
```

For example, when:

```text
CustomerName = "Balaji"
```

the resulting value is:

```text
Welcome Balaji
```

## Perform Numeric Calculations

Variables can be used in calculations.

```powerfx
Set(
    TotalAmount,
    OrderAmount * 1.18
)
```

For example, if:

```text
OrderAmount = 2500
```

then:

```text
TotalAmount = 2950
```

The calculation can be used wherever the resulting value is required.

## Global Variable Example

`Set` can also be used to store information about the current user.

```powerfx
Set(
    CurrentUser,
    User().FullName
)
```

The stored value can then be referenced with:

```powerfx
CurrentUser
```

This can be useful when an application needs to reuse the current user's name.

## Example: Combining Variables

The following example combines several variable concepts:

```powerfx
Set(
    CustomerName,
    "Balaji"
);

Set(
    OrderAmount,
    2500
);

Set(
    IsApproved,
    true
);

Set(
    TotalAmount,
    OrderAmount * 1.18
);

Set(
    WelcomeMessage,
    "Welcome " & CustomerName
)
```

The variables can then be referenced independently:

```powerfx
CustomerName
```

```powerfx
OrderAmount
```

```powerfx
TotalAmount
```

```powerfx
WelcomeMessage
```

and used in conditional logic:

```powerfx
If(
    IsApproved,
    "Approved",
    "Pending"
)
```

## Common Variable Operations

| Requirement | Example |
|---|---|
| Create a variable | `Set(CustomerName, "Balaji")` |
| Store a number | `Set(OrderAmount, 2500)` |
| Store a Boolean | `Set(IsApproved, true)` |
| Read a variable | `CustomerName` |
| Update a variable | `Set(OrderAmount, OrderAmount + 500)` |
| Store a date | `Set(CurrentDate, Today())` |
| Combine values | `"Welcome " & CustomerName` |
| Calculate a value | `OrderAmount * 1.18` |
| Store current user | `User().FullName` |

## Practice Examples

Try changing the initial values and observe the results.

For example:

```powerfx
Set(
    OrderAmount,
    5000
)
```

Then update the value:

```powerfx
Set(
    OrderAmount,
    OrderAmount + 1000
)
```

The resulting value is:

```text
6000
```

You can also change the approval state:

```powerfx
Set(
    IsApproved,
    false
)
```

and test:

```powerfx
If(
    IsApproved,
    "Approved",
    "Pending"
)
```

## Notes

These examples are intended to accompany the Power Fx sections of Chapter 2 in *Learning Microsoft Power Automate*.

The examples in this resource cover:

- Setting variables with `Set`
- Reading variables
- Updating variables
- Using variables in conditional logic
- Storing dates
- Concatenating values
- Numeric calculations
- Storing the current user's name

The examples are based on the variable content currently present in the repository.