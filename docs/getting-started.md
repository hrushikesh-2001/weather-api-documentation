# Getting Started

This guide helps you make your first request to the Weather API.

---

## Prerequisites

Before using the API, ensure you have:

- A valid user account
- An API access token (JWT)
- A REST client (Postman, cURL, or similar)
- Internet access

---

## Base URL

```http
https://api.weatherexample.com/v1
```

---

## Authentication

All protected endpoints require a Bearer token.

Include the token in the `Authorization` header.

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

For more information, see the [Authentication Guide](authentication.md).

---

## Step 1 – Register a User

Create a new account.

```http
POST /auth/register
```

Example:

```bash
curl -X POST "https://api.weatherexample.com/v1/auth/register" \
-H "Content-Type: application/json" \
-d '{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "SecurePassword123!"
}'
```

---

## Step 2 – Log In

Authenticate using your credentials.

```http
POST /auth/login
```

Example:

```bash
curl -X POST "https://api.weatherexample.com/v1/auth/login" \
-H "Content-Type: application/json" \
-d '{
  "username": "john@example.com",
  "password": "SecurePassword123!"
}'
```

Successful authentication returns an access token.

```json
{
  "success": true,
  "accessToken": "YOUR_ACCESS_TOKEN",
  "refreshToken": "YOUR_REFRESH_TOKEN",
  "tokenType": "Bearer",
  "expiresIn": 900
}
```

---

## Step 3 – Make Your First API Request

Use the access token to retrieve weather data.

```bash
curl -X GET "https://api.weatherexample.com/v1/weather?location=Pune&units=metric" \
-H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

Example response:

```json
{
  "location": "Pune",
  "temperature": 31,
  "humidity": 62,
  "condition": "Sunny",
  "wind_speed": 8
}
```

---

## Common HTTP Headers

| Header | Description |
|--------|-------------|
| Authorization | Contains the Bearer access token |
| Content-Type | Specifies the request body format (`application/json`) |
| Accept | Indicates the expected response format |

---

## Supported Response Format

All API responses are returned in JSON format.

Example:

```json
{
  "success": true,
  "data": {}
}
```

---

## Next Steps

After completing your first request, continue with the following guides:

- [Authentication](authentication.md)
- [Authentication API](auth-api.md)
- [API Endpoints](endpoints.md)
- [Error Handling](error-handling.md)
- [Rate Limits](rate-limits.md)

---

## Best Practices

- Store access tokens securely.
- Never commit API keys or tokens to Git repositories.
- Always use HTTPS.
- Handle HTTP status codes appropriately.
- Refresh expired access tokens before retrying requests.

---

**Back to:** [README](../README.md)