# Python Fundamentals for Automation

Python can complement Power Automate when a task benefits from code-based processing. The goal is not to replace flow actions, but to use Python where it provides a clear advantage.

## Example

```python
customer = {"name": "Contoso", "amount": 1250}
result = {
    "customer": customer["name"],
    "amount": float(customer["amount"])
}
print(result)
```

## Clear interfaces

A Python component should have a documented input and output contract.

```text
Input → Validate → Process → Validate output → Return result
```

## Common uses in this chapter

- Transforming large or nested JSON payloads.
- Handling specialized calculations.
- Centralizing reusable processing logic.
- Preparing simplified JSON for Power Automate Desktop or cloud flows.
- Supporting advanced processing that is awkward to express as a long sequence of flow actions.

## Security

Do not embed credentials or sensitive production data in source code.
