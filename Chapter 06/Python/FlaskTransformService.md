# Flask Transformation Service

This exercise follows the manuscript's beginner-friendly example of a small Python web service that accepts JSON, transforms it, and returns simplified JSON for Power Automate.

## 1. Install Python

The manuscript uses Python 3.11 as the example baseline. Install Python from the official Python distribution and ensure Python is available on the command line.

Verify:

```text
python --version
py -m pip --version
```

## 2. Install Flask

```text
pip install flask
```

## 3. Create the service

Save a file such as `transform.py` with the following code:

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/transform", methods=["POST"])
def transform():
    data = request.get_json()

    # Keep only the important fields
    simplified = {
        "username": data.get("login"),
        "id": data.get("id"),
        "followers": data.get("followers"),
        "repos": data.get("public_repos")
    }

    return jsonify(simplified)

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

## 4. Run the service

For the manuscript's Windows example:

```text
cd C:\PythonServices
python transform.py
```

The development service listens on port 5000.

## 5. Test the endpoint

Send a POST request to:

```text
http://localhost:5000/transform
```

with a JSON body containing GitHub-style user data, for example:

```json
{
  "login": "octocat",
  "id": 1,
  "followers": 500,
  "public_repos": 25
}
```

Expected simplified result:

```json
{
  "username": "octocat",
  "id": 1,
  "followers": 500,
  "repos": 25
}
```

## 6. Call from Power Automate Desktop

Use **Invoke web service**:

- Method: `POST`
- URL: the service endpoint.
- Body: the raw JSON response.
- Save the response to a PAD variable.

The flow can then display the result or write it to Excel or another downstream application.

> This is a learning example. A production HTTP service should use an appropriate production server, authentication, HTTPS, validation, logging, and dependency-management approach.
