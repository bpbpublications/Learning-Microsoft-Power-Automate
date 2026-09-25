# Chapter 6 — Custom Connectors, Databases, and Python

This folder contains the companion resources for Chapter 6 of *Learning Microsoft Power Automate*.

The chapter extends Power Automate beyond built-in actions through three integration areas:

1. Custom connectors and OpenAPI-based API integration.
2. SQL and other database integration, including on-premises scenarios.
3. Python-based processing through HTTP services and Azure Functions.

## Learning path

```text
Integration requirement
        ↓
Choose connector / API pattern
        ↓
Define OpenAPI contract
        ↓
Configure authentication
        ↓
Build and test integration
        ↓
Connect to database when required
        ↓
Use Python where it adds value
        ↓
Validate, secure, and monitor
```

## Repository structure

| Folder | Purpose |
|---|---|
| `CustomConnectors/` | Architecture, authentication, GitHub connector exercise, and testing guidance. |
| `OpenAPI/` | OpenAPI structure, contracts, schemas, and best practices. |
| `SQL/` | Database connectivity, stored procedures, gateway, and end-to-end SQL scenarios. |
| `Python/` | Python fundamentals, transformation, Flask/HTTP integration, Azure Functions, and approach selection. |
| `CloudFlows/` | Cloud-flow orchestration patterns combining the integration components. |

## Important security rule

Do not commit API keys, passwords, client secrets, access tokens, database credentials, production connection strings, private keys, or sensitive business data. Use approved connection and credential-management mechanisms. Chapter 7 covers credential-management patterns.

## Companion examples

The repository mirrors the practical themes in the manuscript, including:

- A GitHub Users API custom connector.
- OpenAPI examples for an order API and reusable response schemas.
- SQL Server customer lookup and Teams notification patterns.
- On-premises Data Gateway integration concepts.
- Python transformation through a Flask HTTP service.
- Python integration through Azure Functions.
- Direct Flask/FastAPI HTTP integration.
- Selection guidance for cloud, hybrid, and desktop scenarios.

> **Note:** Power Platform screens, connector availability, licensing, authentication options, and supported capabilities can change. Use the current Microsoft documentation when following the exercises in a live environment.

## Related chapters

- Chapter 3 — Building Cloud, Desktop & Business Flows
- Chapter 5 — Advanced Power Automate Desktop
- Chapter 7 — Credential Management
- Chapter 8 — Monitoring, Sharing & Troubleshooting
- Chapter 9 — Deployment Pipelines & Governance
- Chapter 11 — Enterprise-Scale Automation
