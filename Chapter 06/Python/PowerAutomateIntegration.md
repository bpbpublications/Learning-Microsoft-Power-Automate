# Python and Power Automate Integration

Power Automate does not execute arbitrary Python code directly. Instead, the automation can call a Python component exposed through an appropriate execution environment or HTTP service.

## Conceptual pattern

```text
Power Automate
      ↓
Input data
      ↓
Python processing
      ↓
Validated JSON result
      ↓
Continue flow
```

## Cloud flow

A cloud flow can call an HTTP-accessible Python service and use the returned JSON in Dataverse, Teams, Excel, SharePoint, or another downstream action.

## Desktop flow

Power Automate Desktop can use **Invoke web service** to call a Python HTTP service and save the response into a PAD variable. The manuscript uses `%RawApiResponse%` as the request body and `%PythonResponse%` as an example variable for the returned result.

## Interface design

Define:

- Input format.
- Output format.
- Validation rules.
- Failure behavior.
- Dependencies.
- Authentication requirements.

## Security

Protect HTTP endpoints with an appropriate authentication mechanism. Use HTTPS for cloud services and apply network controls to internal services. Do not put tokens or credentials in flow definitions or source code.
