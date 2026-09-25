# JSON Samples

This folder contains sample JSON payloads used throughout Chapter 2.

## Customer.json

### Parse JSON

Use the contents of Customer.json as input to the Parse JSON action.

### Access Object Properties

Customer Name

```text
body('Parse_JSON')?['CustomerName']
```

Output

```text
Contoso Ltd
```

Customer Country

```text
body('Parse_JSON')?['Country']
```

Output

```text
India
```

### Access Array Elements

Get Orders Collection

```text
body('Parse_JSON')?['Orders']
```

Get First Order

```text
first(body('Parse_JSON')?['Orders'])
```

Get First Order Amount

```text
first(body('Parse_JSON')?['Orders'])?['Amount']
```

Output

```text
1500
```

### Apply to Each Example

Array Input

```text
body('Parse_JSON')?['Orders']
```

Inside Apply to Each

```text
item()?['OrderId']
```

Output

```text
ORD001
ORD002
ORD003
```

### Filter Array Example

Approved Orders

```text
item()?['Status']
```

Condition

```text
is equal to
```

```text
Approved
```

Result

```json
[
  {
    "OrderId": "ORD001",
    "Amount": 1500,
    "Status": "Approved"
  }
]
```

### Count Orders

```text
length(body('Parse_JSON')?['Orders'])
```

Output

```text
3
```

### Get Total Order Value

```text
sum(
  select(
    body('Parse_JSON')?['Orders'],
    'Amount'
  )
)
```

Business Result

```text
4950
```
