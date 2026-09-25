# OpenAPI Basics

OpenAPI definitions describe API endpoints, parameters, request bodies, responses, and authentication requirements.

## Document formats

OpenAPI definitions can be represented as JSON or YAML.

## Core structure

```text
OpenAPI document
├── info
├── servers
├── paths
│   └── operation
├── components
│   └── schemas
└── security
```

## Minimal example

```yaml
openapi: 3.0.1
info:
  title: Sample Order API
  version: 1.0.0
servers:
  - url: https://api.example.com
paths:
  /orders/{id}:
    get:
      summary: Get order by ID
      parameters:
        - name: id
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: object
                properties:
                  orderId:
                    type: string
                  status:
                    type: string
```

This example maps the API host to `servers`, the endpoint to `paths`, the HTTP method to `get`, the input to a required path parameter, and the result to a JSON response schema.

## Validation

Validate the OpenAPI definition before importing it into a connector. Then test each operation against a controlled endpoint.
