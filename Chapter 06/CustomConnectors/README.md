# Custom Connectors

Custom connectors expose APIs to Power Automate when a suitable built-in connector is not available.

## Topics

- Connector architecture
- Creation options
- Authentication
- OpenAPI definitions
- Actions and triggers
- Request and response schemas
- Testing
- Security and lifecycle management

## Creation options

Depending on the API and environment, the Power Automate portal can provide options such as:

- Create from blank.
- Create from an Azure service.
- Import an OpenAPI definition.
- Import an API definition or supported collection where available.

## Recommended learning order

1. Understand the target API.
2. Confirm a standard connector does not already meet the requirement.
3. Define the API contract.
4. Choose authentication.
5. Create the connector.
6. Define actions and schemas.
7. Test each operation.
8. Use the connector from a flow.
9. Apply security, governance, and lifecycle controls.

## Chapter exercises

- [Connector Architecture](ConnectorArchitecture.md)
- [Authentication Methods](AuthenticationMethods.md)
- [GitHub Users Connector](GitHubUsersConnector.md)
- [Connector Testing](ConnectorTesting.md)
