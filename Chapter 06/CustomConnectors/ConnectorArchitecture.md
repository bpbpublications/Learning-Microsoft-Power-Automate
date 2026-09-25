# Custom Connector Architecture

A custom connector provides a Power Platform interface to an external API. It acts as a reusable boundary between a flow and the service being called.

```text
Power Automate
      ↓
Custom Connector
      ↓
Authentication
      ↓
External API
      ↓
Response processing
      ↓
Structured flow data
```

## Core components

- **API wrapper layer** — formats requests, maps parameters, and exposes API responses to flows.
- **Authentication framework** — supports the authentication model required by the target API.
- **Definition engine** — describes operations, inputs, outputs, and metadata, either manually or through an API definition.
- **Response processing** — exposes JSON objects, arrays, or strings as usable flow outputs.

Custom connectors can also be reused across Power Platform experiences such as Power Apps and Copilot Studio, subject to the capabilities and configuration of the environment.

## Performance and scalability

The manuscript highlights connection pooling, caching, throttling, and telemetry as important considerations when building integrations. Design the connector so that unnecessary API calls are avoided and operational behavior can be observed.

## When to use a custom connector

Use one when:

- A required service has no suitable standard connector.
- The API is approved for integration.
- Authentication can be implemented securely.
- A reusable business-facing interface adds value.

Do not expose unnecessary internal API details. Design actions around stable business operations.

## Security

Apply least privilege. Never embed real secrets in source files or OpenAPI documents. Keep environment-specific configuration outside the connector source wherever possible.
