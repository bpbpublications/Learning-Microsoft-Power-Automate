# Azure Functions Integration

Azure Functions provides the cloud-hosted execution pattern described in the manuscript for running Python processing while Power Automate remains the workflow orchestrator.

## Architecture

```text
Power Automate Cloud Flow
        ↓ HTTP
Azure Function
        ↓
Python processing
        ↓
JSON result
        ↓
Power Automate
```

## Cloud flow pattern

1. Trigger the cloud flow.
2. Collect the input data.
3. Use an HTTP-capable action to call the function endpoint.
4. Send the input as JSON.
5. Capture and validate the JSON response.
6. Continue with actions such as Dataverse, Teams, or Excel.

The manuscript illustrates an endpoint shape such as:

```text
https://<function-app>.azurewebsites.net/api/<function>
```

## Example scenario

A scheduled flow can fetch sales data from Dataverse, send it to a Python Azure Function for KPI calculation, and post the resulting summary to Teams.

## Power Automate Desktop

PAD can call the Azure Function through **Invoke web service**. The response can then be parsed and used in Excel, SAP, an ERP system, or another desktop application.

## Security

The manuscript recommends protecting cloud services with appropriate mechanisms such as function keys, Microsoft Entra ID, or OAuth. Always use HTTPS and keep credentials outside source files.

## Design principles

- Define a stable JSON input contract.
- Return a predictable response.
- Validate both input and output.
- Handle function failures explicitly.
- Keep environment-specific configuration separate from code.
