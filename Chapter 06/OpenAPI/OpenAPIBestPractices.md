# OpenAPI Best Practices for Power Automate

The manuscript identifies several practices that make OpenAPI definitions easier to use in Power Automate.

## 1. Give every operation a unique operationId

The `operationId` becomes the connector action name. Keep it unique and meaningful.

```yaml
operationId: GetCustomer
```

## 2. Add useful examples

Request and response examples help users understand what an operation expects and returns.

## 3. Reuse schemas

Use `components/schemas` for common data models instead of repeating the same structure across operations.

## 4. Define security clearly

Describe the authentication model under the appropriate security definitions and keep secrets out of the specification.

## 5. Keep operations descriptive

A flow maker should be able to understand what an action does without opening separate API documentation.

## 6. Validate before import

Check the definition before importing it into the custom connector experience. After import, test each action independently.

## 7. Design for change

Treat the OpenAPI file as a versioned contract. When the API evolves, update and validate the contract before re-importing it.
