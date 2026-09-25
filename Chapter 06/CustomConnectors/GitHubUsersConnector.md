# GitHub Users API Custom Connector

This exercise follows the manuscript's hands-on example for creating a custom connector around the GitHub Users API.

## 1. General setup

Create a custom connector named **GitHub Users API**.

Use:

- Description: Retrieve details about a GitHub user by username.
- Scheme: HTTPS.
- Host: `api.github.com`.
- Base URL: `/`.

## 2. Security — OAuth 2.0

The manuscript configures a generic OAuth 2.0 identity provider with:

- Authorization URL: `https://github.com/login/oauth/authorize`
- Token URL: `https://github.com/login/oauth/access_token`
- Refresh URL: `https://github.com/login/oauth/access_token`
- Scopes: `read:user user:email`

Create the OAuth application in the GitHub developer settings and use the client credentials supplied for the exercise. **Never place real client secrets in this document or in Git.**

> The exact GitHub OAuth behavior and Power Platform UI can change. Verify the current provider requirements before reproducing the exercise.

## 3. Definition — GetUserByUsername

Create an action named `GetUserByUsername`.

Request:

```text
Method: GET
URL: /users/{username}
Parameter: username
Location: path
Required: yes
Type: string
```

The API returns user-profile data. A representative response is:

```json
{
  "login": "octocat",
  "id": 1,
  "name": "The Octocat",
  "company": "GitHub",
  "public_repos": 8,
  "followers": 20,
  "following": 0
}
```

The connector's request and response definitions should expose the fields required by downstream flows rather than unnecessary internal details.

## 4. Code section

The manuscript notes that the Code section can be used for request and response transformations. For this GitHub Users API example, no custom C# transformation is required.

## 5. Test

Create a connection, select `GetUserByUsername`, enter a valid GitHub username, and run the test. A successful HTTP 200 response confirms that the operation returned data.

## What this exercise teaches

- Connector metadata and host configuration.
- OAuth 2.0 configuration.
- Path parameters.
- Request and response definitions.
- Optional response transformation.
- Live connector testing.

## Security reminder

Use test credentials and approved environments. Do not commit OAuth client secrets, access tokens, or other credentials.
