# Common Conversion Expressions in Power Automate

Conversion functions are used to transform data from one format or type to another.

---

## int()

Converts a value to an integer.

```text
int('100')
```

Output

```text
100
```

Business Example

```text
int(triggerBody()?['Quantity'])
```

---

## float()

Converts a value to a decimal number.

```text
float('99.95')
```

Output

```text
99.95
```

Business Example

```text
float(triggerBody()?['Amount'])
```

---

## string()

Converts a value to text.

```text
string(12345)
```

Output

```text
12345
```

Business Example

```text
string(variables('InvoiceNumber'))
```

---

## bool()

Converts a value to Boolean.

```text
bool('true')
```

Output

```text
true
```

Example

```text
bool('false')
```

Output

```text
false
```

---

## json()

Converts a JSON string into a JSON object.

```text
json('{
  "Name":"Balaji",
  "Department":"IT"
}')
```

Output

```json
{
  "Name": "Balaji",
  "Department": "IT"
}
```

Business Example

```text
json(outputs('Compose'))
```

---

## xml()

Converts text into XML format.

```text
xml(
'<Employee>
   <Name>Balaji</Name>
 </Employee>'
)
```

Output

```xml
<Employee>
  <Name>Balaji</Name>
</Employee>
```

---

## base64()

Encodes a string to Base64.

```text
base64('Power Automate')
```

Output

```text
UG93ZXIgQXV0b21hdGU=
```

---

## base64ToString()

Decodes a Base64 string.

```text
base64ToString(
'UG93ZXIgQXV0b21hdGU='
)
```

Output

```text
Power Automate
```

---

## uriComponent()

Encodes special characters for URLs.

```text
uriComponent(
'Power Automate & AI'
)
```

Output

```text
Power%20Automate%20%26%20AI
```

---

## uriComponentToString()

Decodes URL encoded text.

```text
uriComponentToString(
'Power%20Automate%20%26%20AI'
)
```

Output

```text
Power Automate & AI
```

---

## Business Scenario 1 - Convert Form Input

Form response:

```json
{
  "Quantity": "25"
}
```

Expression

```text
int(triggerBody()?['Quantity'])
```

Result

```text
25
```

---

## Business Scenario 2 - Invoice Processing

Invoice Amount:

```json
{
  "Amount": "4999.99"
}
```

Expression

```text
float(triggerBody()?['Amount'])
```

Result

```text
4999.99
```

---

## Business Scenario 3 - Parse API Response

API Output:

```text
"{\"Status\":\"Approved\"}"
```

Expression

```text
json(body('HTTP'))
```

Result

```json
{
  "Status": "Approved"
}
```

---

## Business Scenario 4 - Secure Data Exchange

Encode sensitive data.

```text
base64(
variables('CustomerID')
)
```

Decode later.

```text
base64ToString(
outputs('EncodedValue')
)
```

---

## Business Scenario 5 - Build Dynamic URLs

```text
concat(
'https://contoso.com/search?q=',
uriComponent(
triggerBody()?['SearchText']
)
)
```

Search Text

```text
Power Automate & AI
```

Result

```text
https://contoso.com/search?q=Power%20Automate%20%26%20AI
```

---

## Key Takeaways

Conversion functions are commonly used to:

- Convert text to numbers
- Convert numbers to strings
- Parse JSON payloads
- Process API responses
- Work with XML data
- Encode and decode Base64 values
- Generate URL-safe strings
- Transform data between systems

These functions are essential when integrating Power Automate with SharePoint, Microsoft Teams, Outlook, Dataverse, SQL Server, REST APIs, and external applications.
