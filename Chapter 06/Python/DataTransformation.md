# Python Data Transformation

Python is useful when an API returns a large or nested JSON response and the flow needs only a small, stable subset of the data.

## Pattern

```text
Raw API response
      ↓
Validate input
      ↓
Transform / normalize
      ↓
Validate output
      ↓
Return simplified JSON
```

## Example transformation

The manuscript's example extracts selected GitHub user fields:

```python
simplified = {
    "username": data.get("login"),
    "id": data.get("id"),
    "followers": data.get("followers"),
    "repos": data.get("public_repos")
}
```

A possible result is:

```json
{
  "username": "octocat",
  "id": 1,
  "followers": 500,
  "repos": 25
}
```

This keeps the downstream PAD flow focused on the fields it actually needs.

## Good practice

Keep transformation functions small, define expected inputs and outputs, handle missing or invalid data explicitly, and test representative edge cases.
