# OpenAPI Contract for Custom Connectors

An OpenAPI definition describes the contract between a connector and the API it calls.

## Contract checklist

A useful contract makes the following explicit:

- HTTP method.
- Endpoint path.
- Required and optional parameters.
- Request body schema.
- Response schema.
- Authentication approach.
- Expected error responses.

## Example operation

```yaml
paths:
  /customers/{id}:
    get:
      operationId: GetCustomer
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Customer returned
```

The example is intentionally incomplete. A production contract should also define the actual server, response content, security requirements, and error behavior required by the API.

## Contract design principle

Treat OpenAPI as a stable interface. Define business-meaningful operations rather than exposing every internal API detail. Keep schemas aligned with the actual API response.

## Security

Do not place client secrets, API keys, passwords, access tokens, or private keys in the OpenAPI document.
