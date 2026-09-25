# Direct HTTP API Integration with Flask or FastAPI

A direct Python API is an alternative to Azure Functions when an organization already operates a Python service or wants a lightweight HTTP integration.

## Architecture

```text
Power Automate
      ↓ HTTP
Flask / FastAPI service
      ↓
Python processing
      ↓
JSON response
```

## Cloud flow

1. Use an HTTP action.
2. Target the Flask or FastAPI endpoint.
3. Pass the flow input as JSON.
4. Capture and validate the response.
5. Continue with the business process.

The service may be hosted on a VM, container, or an approved internal platform.

## Desktop flow

Use **Invoke web service** in PAD to call a local or intranet-hosted service. This can be useful when the Python service is close to an on-premises application or database.

## Example scenarios from the chapter

- A SharePoint file event sends metadata to a Flask service for enrichment and writes the result back to SharePoint.
- A PAD flow extracts mainframe data, sends it to a local FastAPI service for cleansing, and returns the cleaned data to a legacy desktop system.

## Security

Protect internal services with appropriate tokens or API keys. Use HTTPS for cloud services and apply firewall or VPN controls to internal services. Where appropriate, combine secure on-premises access with the On-Premises Data Gateway.

## When this pattern fits

Use direct HTTP integration when an existing Python service is already available, when a lightweight internal service is appropriate, or when serverless hosting is not required.
