# Common Logical Expressions in Power Automate

Logical functions are used to evaluate conditions and control flow execution.

---

## Equals

Checks whether two values are identical.

```text
equals(5,5)
```

Output

```text
true
```

Example:

```text
equals(variables('Status'),'Approved')
```

---

## Not Equals

Checks whether two values are different.

```text
not(equals(5,10))
```

Output

```text
true
```

---

## And

Returns true only when all conditions are true.

```text
and(true,true)
```

Output

```text
true
```

Example:

```text
and(
 greater(variables('Amount'),1000),
 equals(variables('Status'),'Pending')
)
```

---

## Or

Returns true when at least one condition is true.

```text
or(false,true)
```

Output

```text
true
```

Example:

```text
or(
 equals(variables('Priority'),'High'),
 equals(variables('Priority'),'Critical')
)
```

---

## Not

Reverses a Boolean value.

```text
not(false)
```

Output

```text
true
```

Example:

```text
not(empty(triggerBody()?['Email']))
```

---

## If

Returns one value when a condition is true and another when false.

```text
if(
 equals(variables('Status'),'Approved'),
 'Send Email',
 'Do Nothing'
)
```

Output

```text
Send Email
```

---

## Greater Than

Checks if the first value is greater than the second.

```text
greater(100,50)
```

Output

```text
true
```

Business Example:

```text
greater(
 variables('InvoiceAmount'),
 10000
)
```

---

## Greater Than or Equal

```text
greaterOrEquals(100,100)
```

Output

```text
true
```

---

## Less Than

```text
less(50,100)
```

Output

```text
true
```

---

## Less Than or Equal

```text
lessOrEquals(50,50)
```

Output

```text
true
```

---

## Empty

Checks whether a value is empty.

```text
empty('')
```

Output

```text
true
```

Example:

```text
empty(triggerBody()?['Comments'])
```

---

## Contains

Checks whether a string contains a value.

```text
contains(
 'Learning Power Automate',
 'Power'
)
```

Output

```text
true
```

---

## Nested IF Example

Approval routing scenario:

```text
if(
 greater(variables('Amount'),10000),
 'Director Approval',
 if(
   greater(variables('Amount'),5000),
   'Manager Approval',
   'Auto Approved'
 )
)
```

Output Examples

```text
Director Approval
```

```text
Manager Approval
```

```text
Auto Approved
```

---

## Business Scenario 1 - Expense Approval

```text
and(
 greater(variables('ExpenseAmount'),5000),
 equals(variables('ExpenseType'),'Travel')
)
```

Result:

```text
true
```

Action:

```text
Route to Finance Manager
```

---

## Business Scenario 2 - Employee Onboarding

```text
or(
 empty(triggerBody()?['Manager']),
 empty(triggerBody()?['Department'])
)
```

Result:

```text
true
```

Action:

```text
Request Missing Information
```

---

## Business Scenario 3 - Contract Renewal

```text
lessOrEquals(
 triggerBody()?['DaysToExpiry'],
 30
)
```

Result:

```text
true
```

Action:

```text
Send Renewal Reminder
```

---

## Business Scenario 4 - Customer Priority Validation

```text
contains(
 triggerBody()?['Category'],
 'Premium'
)
```

Result:

```text
true
```

Action:

```text
Route to Premium Support Team
```

---

## Key Takeaways

Logical expressions are commonly used to:

- Evaluate approvals
- Validate input data
- Route requests
- Trigger notifications
- Implement business rules
- Control flow branching
- Build dynamic automation solutions
