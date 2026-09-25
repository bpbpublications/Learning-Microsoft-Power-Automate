# Common Collection Expressions in Power Automate

Collection functions help work with arrays, lists, and collections of data.

---

## Create Array

Creates an array with multiple values.

```text
createArray(
 'Power Automate',
 'Power Apps',
 'Power BI'
)
```

Output

```json
[
  "Power Automate",
  "Power Apps",
  "Power BI"
]
```

---

## First

Returns the first item in an array.

```text
first(
 createArray(
   'Power Automate',
   'Power Apps',
   'Power BI'
 )
)
```

Output

```text
Power Automate
```

---

## Last

Returns the last item in an array.

```text
last(
 createArray(
   'Power Automate',
   'Power Apps',
   'Power BI'
 )
)
```

Output

```text
Power BI
```

---

## Length

Returns the number of items in an array.

```text
length(
 createArray(
   'A',
   'B',
   'C'
 )
)
```

Output

```text
3
```

---

## Union

Combines arrays and removes duplicates.

```text
union(
 createArray('A','B','C'),
 createArray('B','C','D')
)
```

Output

```json
[
  "A",
  "B",
  "C",
  "D"
]
```

---

## Intersection

Returns only common values.

```text
intersection(
 createArray('A','B','C'),
 createArray('B','C','D')
)
```

Output

```json
[
  "B",
  "C"
]
```

---

## Join

Converts an array into a string.

```text
join(
 createArray(
   'Power',
   'Automate',
   'Book'
 ),
 ' '
)
```

Output

```text
Power Automate Book
```

---

## Split

Converts a string into an array.

