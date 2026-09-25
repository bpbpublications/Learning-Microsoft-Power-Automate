# OpenAPI

OpenAPI provides a machine-readable description of an HTTP API. It can be used as the contract from which a custom connector is designed or imported.

## Core elements

```text
OpenAPI document
├── info
├── servers
├── paths
│   ├── operations
│   ├── parameters
│   ├── request bodies
│   └── responses
└── components / schemas
```

An operation should clearly define its HTTP method, relative path, required inputs, request body when applicable, expected response, and error responses.

## Why use OpenAPI

The manuscript highlights four benefits:

- **Automation** — the definition can be used to build the connector shell.
- **Accuracy** — the API definition reduces manual mapping errors.
- **Reusability** — the same contract can be shared across teams and environments.
- **Maintainability** — an updated API definition can be re-imported as the API evolves.

## Resources

- [OpenAPI Basics](OpenAPIBasics.md)
- [OpenAPI Contract](OpenAPIContract.md)
- [Request and Response Schemas](RequestResponseSchemas.md)
- [OpenAPI Best Practices](OpenAPIBestPractices.md)

Never place production secrets in an OpenAPI document committed to source control.
