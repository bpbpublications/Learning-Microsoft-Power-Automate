# Common Date and Time Expressions in Power Automate

## Current Date and Time

Returns the current UTC date and time.

```text
utcNow()
```

Sample Output

```text
2026-08-13T08:30:15Z
```

---

## Current Date Only

Formats the current date.

```text
formatDateTime(utcNow(),'yyyy-MM-dd')
```

Sample Output

```text
2026-08-13
```

---

## Current Time Only

Returns only the time portion.

```text
formatDateTime(utcNow(),'HH:mm:ss')
```

Sample Output

```text
08:30:15
```

---

## Add Days

Adds 7 days to the current date.

```text
addDays(utcNow(),7)
```

Sample Output

```text
2026-08-20T08:30:15Z
```

---

## Subtract Days

Subtracts 7 days from the current date.

```text
addDays(utcNow(),-7)
```

Sample Output

```text
2026-08-06T08:30:15Z
```

---

## Add Months

Adds one month to the current date.

```text
addToTime(utcNow(),1,'Month')
```

Sample Output

```text
2026-09-13T08:30:15Z
```

---

## Add Years

Adds one year.

```text
addToTime(utcNow(),1,'Year')
```

Sample Output

```text
2027-08-13T08:30:15Z
```

---

## Day of Month

Returns the day of the month.

```text
dayOfMonth(utcNow())
```

Sample Output

```text
13
```

---

## Month

Returns the month number.

```text
month(utcNow())
```

Sample Output

```text
8
```

---

## Year

Returns the year.

```text
year(utcNow())
```

Sample Output

```text
2026
```

---

## Day of Week

Returns weekday number.

```text
dayOfWeek(utcNow())
```

Sample Output

```text
4
```

> Sunday = 0, Monday = 1, Tuesday = 2, etc.

---

## Convert Time Zone

Converts UTC to India Standard Time.

```text
convertTimeZone(
 utcNow(),
 'UTC',
 'India Standard Time'
)
```

Sample Output

```text
2026-08-13T14:00:15
```

---

## Start of Day

Returns midnight of the current day.

```text
startOfDay(utcNow())
```

Sample Output

```text
2026-08-13T00:00:00Z
```

---

## Difference Between Dates

Calculates difference between two dates.

```text
dateDifference(
 '2026-08-01',
 '2026-08-13'
)
```

Sample Output

```text
12
```

---

## Last Day of Current Month

Returns the last day of the month.

```text
formatDateTime(
 addDays(
  startOfMonth(
   addToTime(utcNow(),1,'Month')
  ),
  -1
 ),
 'yyyy-MM-dd'
)
```

Sample Output

```text
2026-08-31
```

---

## Business Scenario Example

Generate a due date 5 days after request creation:

```text
addDays(
 triggerOutputs()?['body/Created'],
 5
)
```

Generate approval expiry date after 30 days:

```text
addDays(
 utcNow(),
 30
)
```

Generate financial reporting month:

```text
formatDateTime(
 utcNow(),
 'MMMM yyyy'
)
```

Sample Output

```text
August 2026
```
