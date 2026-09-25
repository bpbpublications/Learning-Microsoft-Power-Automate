# Power Fx Dates

## Overview

This resource provides practical examples of working with dates and times in **Power Fx**.

Date functions are useful for calculating due dates, comparing dates, formatting values, and building time-based business logic.

## Current Date

Use `Today()` to return the current date.

```powerfx
Today()
```

This returns the current date without a time component.

## Current Date and Time

Use `Now()` to return the current date and time.

```powerfx
Now()
```

This is useful when both the date and time are required.

## Add Days

Use `DateAdd` to add days to a date.

```powerfx
DateAdd(
    Today(),
    7,
    Days
)
```

This returns the date seven days from today.

## Add Months

You can also add months using `DateAdd`.

```powerfx
DateAdd(
    Today(),
    1,
    Months
)
```

This returns the date one month from today.

## Add Years

To add years:

```powerfx
DateAdd(
    Today(),
    1,
    Years
)
```

This returns the date one year from today.

## Difference Between Dates

Use `DateDiff` to calculate the difference between two dates.

```powerfx
DateDiff(
    DateValue("01-Aug-2026"),
    DateValue("13-Aug-2026"),
    Days
)
```

This calculates the difference between the two dates in days.

## Format a Date

Use `Text` to display a date in a specific format.

```powerfx
Text(
    Today(),
    "dd-mmm-yyyy"
)
```

Example output:

```text
13-Aug-2026
```

## Format Date and Time

`Text` can also be used to format a date and time.

```powerfx
Text(
    Now(),
    "dd-mmm-yyyy hh:mm AM/PM"
)
```

Example output:

```text
13-Aug-2026 10:30 AM
```

The actual output depends on the current date and time.

## Get the Month Name

To display the full month name:

```powerfx
Text(
    Today(),
    "mmmm"
)
```

Example:

```text
August
```

## Financial Reporting Month

For reporting scenarios, you can combine the month and year:

```powerfx
Text(
    Today(),
    "mmmm yyyy"
)
```

Example:

```text
August 2026
```

This can be useful when creating monthly reports or summaries.

## Calculate a Due Date

A common business requirement is to calculate a due date a fixed number of days from today.

For example:

```powerfx
DateAdd(
    Today(),
    30,
    Days
)
```

This returns a date 30 days from today.

## Find the End of the Current Month

The following expression calculates the last day of the current month:

```powerfx
DateAdd(
    Date(
        Year(Today()),
        Month(Today()) + 1,
        1
    ),
    -1,
    Days
)
```

The expression first creates the first day of the next month and then subtracts one day.

## Get the Weekday

Use `Weekday` to return the numeric weekday value for a date.

```powerfx
Weekday(
    Today()
)
```

The returned value depends on the weekday numbering convention used by the Power Fx environment.

## Common Date Operations

| Requirement | Function |
|---|---|
| Get today's date | `Today()` |
| Get current date and time | `Now()` |
| Add days, months, or years | `DateAdd()` |
| Calculate date difference | `DateDiff()` |
| Convert text to a date | `DateValue()` |
| Format a date | `Text()` |
| Get year from a date | `Year()` |
| Get month from a date | `Month()` |
| Get weekday | `Weekday()` |

## Practice Examples

Try changing the values in the examples to understand how the results change.

For example:

```powerfx
DateAdd(
    Today(),
    7,
    Days
)
```

can be changed to:

```powerfx
DateAdd(
    Today(),
    14,
    Days
)
```

You can also experiment with different date formats:

```powerfx
Text(
    Today(),
    "dd/MM/yyyy"
)
```

and:

```powerfx
Text(
    Today(),
    "yyyy-MM-dd"
)
```

## Notes

These examples are intended to accompany the Power Fx sections of Chapter 2 in *Learning Microsoft Power Automate*.

The examples in this resource cover:

- Current date
- Current date and time
- Adding days, months, and years
- Date differences
- Date formatting
- Month formatting
- Due-date calculation
- End-of-month calculation
- Weekday calculation

The examples above are based on the date-function content currently present in the repository.