# Request and Response Schemas

Clear schemas make connector actions easier to configure and make returned data easier to consume in Power Automate.

## Request schema

Document:

- Required fields.
- Optional fields.
- Data types.
- Allowed values.
- Nested objects.
- Parameter location such as path, query, header, or body.

## Response schema

Define the fields the flow should receive and their expected types.

```text
API response
    ↓
Response schema
    ↓
Dynamic content
    ↓
Power Automate actions
```

## Good practice

Keep schemas aligned with the real API response. Avoid exposing unnecessary internal fields. Define error responses as well as successful responses when the API contract supports them.

Test both successful and error responses before using the connector in a production flow.
