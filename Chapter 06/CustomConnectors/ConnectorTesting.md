# Connector Testing and Validation

A connector is not complete when the definition is saved. Each operation should be tested against a controlled endpoint before it is used by production flows.

## Test sequence

1. Create or select the required connection.
2. Select the connector operation.
3. Supply representative input values.
4. Run the operation.
5. Inspect the HTTP status.
6. Inspect the response headers when relevant.
7. Validate the response body and schema.
8. Test failure and invalid-input cases.

## GitHub Users API example

For `GetUserByUsername`:

```text
Input: username
        ↓
GET /users/{username}
        ↓
GitHub API
        ↓
HTTP 200 + JSON
        ↓
Power Automate dynamic content
```

The manuscript uses a GitHub username as the test input and treats a successful 200 response as confirmation that authentication and the API operation are working.

## Minimum validation checklist

- Authentication succeeds.
- Required parameters are enforced.
- Successful responses match the declared schema.
- Invalid input is handled predictably.
- Authentication and authorization failures are understood.
- Timeout behavior is understood.
- API errors have an identified recovery or escalation path.
- Sensitive values are not exposed in diagnostics.

## Before production

Test the connector in a development or test environment with synthetic or approved sample data. Confirm retry behavior, throttling behavior, permissions, and environment-specific configuration before broader deployment.
