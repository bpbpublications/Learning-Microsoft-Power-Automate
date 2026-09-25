# Choosing the Python Integration Approach

Azure Functions and direct Python APIs both extend Power Automate with capabilities that are better implemented in code. The right choice depends on where the flow runs, the required scale, security model, and existing services.

| Approach | Best fit in the chapter | Key characteristics |
|---|---|---|
| Azure Functions + Cloud Flow | Enterprise cloud workloads | Serverless execution, scalable processing, cloud-native integration. |
| Azure Functions + Desktop Flow | Hybrid automation | PAD remains the desktop layer while Python processing runs in the cloud. |
| Direct Flask/FastAPI + Cloud Flow | Existing Python services and lightweight scenarios | Reuses an existing API without adding a serverless layer. |
| Local Python API + Desktop Flow | On-premises and legacy automation | Low-latency local integration close to desktop applications or databases. |

## Decision questions

Ask:

1. Does the workload need cloud-native scale and resilience?
2. Is a Python service already operated by the organization?
3. Does the automation need to stay close to an on-premises system?
4. What authentication and network controls are required?
5. Who owns deployment, monitoring, and support?
6. Is the service reusable across multiple automations?

## Security across all approaches

- Use HTTPS for cloud endpoints.
- Protect internal services with appropriate network controls.
- Use function keys, Entra ID, OAuth, tokens, or API keys as appropriate to the service.
- Keep secrets out of source code and flow definitions.
- Validate input and output at the integration boundary.

The goal is not simply to make Python work. Choose an integration pattern that fits the operational context in which the automation will run.
