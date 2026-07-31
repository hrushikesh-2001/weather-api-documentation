# Authentication API

This document describes the authentication endpoints used to register users, authenticate requests, manage sessions, and reset passwords. 

---

## Base URL

```http
https://api.weatherexample.com/v1
```

---

## Authentication Flow 

1. Register a new user.
2. Log in using email and password.
3. Receive an access token and refresh token.
4. Include the access token in the Authorization header for protected endpoints.
5. Refresh the access token when it expires.
6. Log out to invalidate the current session.

---

# POST /auth/register

Creates a new user account.

## URL 

```http
POST https://api.weatherexample.com/v1/auth/register

```
---
## Request Body

| Field    | Type   | Required | Description        |
| -------- | ------ | -------- | ------------------ |
| name     | string | Yes      | User's full name   |
| email    | string | Yes      | User email address |
| password | string | Yes      | User password      |

---

## cURL

```bash
curl -X POST "https://api.weatherexample.com/v1/auth/register" \
-H "Content-type: application/json" \
-d '{
    "name": "Hrushi S",
    "email":"h@example.com",
    "password": "Yourpass&123"
}'
```
---

## Success Response

```json
{
    "success": true,
    "message": "User registered successfully.",
    "data": { 
        "userId": "user001"
     }
}
```
---
## Response Field

| Field       | Type    | Description                                  |
| ----------- | ------- | -------------------------------------------- |
| success     | boolean | Indicates whether the registration succeeded |
| message     | string  | Success message                              |
| data.userId | string  | Unique identifier of the new user            |

---

## Status Code 

| Code | Meaning               |
| ---- | --------------------- |
| 201  | User created          |
| 400  | Invalid request       |
| 409  | Email already exists  |
| 500  | Internal server error |

---
## Security Notes

- Always use HTTPS to protect user credentials during transmission.
- Never store user passwords in plain text. Passwords should be securely hashed before storage.
- Enforce a strong password policy, including minimum length and complexity requirements.
- Validate and sanitize user input before processing registration requests.
- Do not expose sensitive information in API responses or error messages.
- Prevent duplicate account registration using the same email address.
- Apply rate limiting to prevent automated registration abuse.
- Never log passwords or other sensitive authentication data.

---


# POST /auth/login

Authenticates a user and returns an access token and refresh token.

## URL

```http
POST https://api.weatherexample.com/v1/auth/login
```
---

## Request Body 

| Field    | Type   | Required | Description |
|----|----|----|----|
| username | string | Yes   | registered Username |
| password | string | Yes      | User password |

---

## cURL

```bash
curl -X POST https://api.weatherexample.com/v1/auth/login \
-H "Content-Type: application/json" \
-d '{
     "username":"User001",
     "password": "Yourpass@123"
     }'

```
## Success Response

```json
{
    "success": true,
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "tokenType": "Bearer",
    "refreshToken": "qwerty345",
    "expiresIn": 900
}
```
---
## Response Fields

| Field        | Type    | Description                                    |
| ------------ | ------- | ---------------------------------------------- |
| success      | boolean | Indicates whether authentication succeeded     |
| accessToken  | string  | JWT access token                               |
| refreshToken | string  | Refresh token used to obtain new access tokens |
| tokenType    | string  | Authentication scheme (Bearer)                 |
| expiresIn    | integer | Access token lifetime in seconds               |


## Status Code 

| Code | Meaning               |
| ---- | --------------------- |
| 200  | Authentication successful |
| 400  | Invalid request       |
| 401  | Authentication failed |
| 404  | Resource not found    |
| 500  | Internal server error |

---
## Security Notes

- Always use HTTPS to protect usernames, passwords, and authentication tokens during transmission.
- Never log or expose user passwords in application logs, error messages, or API responses.
- Implement rate limiting to prevent brute-force and credential-stuffing attacks.
- Use a secure password-hashing algorithm when storing user passwords.
- Return generic authentication errors to avoid revealing whether a username or email address exists.
- Use short-lived access tokens to reduce the impact of token theft.
- Store refresh tokens securely and revoke them when necessary.
- Never include access tokens or refresh tokens in URLs.
- Validate user credentials on the server before issuing authentication tokens.

---
# POST /auth/forgot-password

Requests a password-reset link for a registered user.

## URL 
```http
POST https://api.weatherexample.com/v1/auth/forgot-password
```

---

## Request Body 

| Field | Type | Required | Description |
|------|------|----------|-------------|
| email | string | Yes | Email address associated with the user account |

---

## cURL Example

```bash
curl -X POST "https://api.weatherexample.com/v1/auth/forgot-password" \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com"
}'
```

## Success Response

```json
{
  "success": true,
  "message": "Password reset link sent successfully."
}
```
---

## Response Fields

| Field | Type | Description |
|------|------|-------------|
| success | boolean | Indicates whether the request was processed successfully |
| message | string | Provides information about the password-reset request |

---

## Status Code 

| Code | Meaning |
|------|---------|
| 200 | Password reset request processed successfully |
| 400 | Invalid email address |
| 429 | Too many requests |
| 500 | Internal server error |

---

## Security Notes

- Do not expose whether an email address is registered.
- Password reset links should expire after a limited period.
- Password reset tokens should be single-use.
- Apply rate limiting to password reset requests.
- Never include passwords in API requests other than over HTTPS.

---

# POST /auth/reset-password

Resets a user's password using a valid password-reset token.

## URL

```http
POST https://api.weatherexample.com/v1/auth/reset-password
```
---
## Request Body

| Field | Type | Required | Description |
|------|------|----------|-------------|
| token | string | Yes | Password-reset token received through the reset link |
| newPassword | string | Yes | New password for the user account |

---

## cURL Example

```bash
{
  curl -X POST "https://api.weatherexample.com/v1/auth/reset-password" \
-H "Content-Type: application/json" \
-d '{
  "token": "reset_token_0021",
  "newPassword": "NewSecurePassword@123"
}'
}
```
---

## Success Response

```json
{
  "success": true,
  "message": "Password updated successfully."
}
```

---

## Response Fields

| Field | Type | Description |
|------|------|-------------|
| success | boolean | Indicates whether the password was updated successfully |
| message | string | Provides the result of the password-reset request |

---

## Status Codes

| Code | Meaning |
|------|---------|
| 200 | Password updated successfully |
| 400 | Invalid request or password format |
| 401 | Invalid or expired reset token |
| 429 | Too many requests |
| 500 | Internal server error |

---

## Security Notes

- Password-reset tokens should expire after a limited period.
- Password-reset tokens should be single-use.
- Always use HTTPS when transmitting reset tokens and passwords.
- Never log passwords or password-reset tokens.
- Require passwords to meet the application's password policy.
- Invalidate existing sessions after a successful password reset when appropriate.

---

# POST /auth/refresh

Generates a new access token using a valid refresh token.

## URL

```http
POST https://api.weatherexample.com/v1/auth/refresh
```

---
## Authentication

A valid refresh token is required.

## Request Body

| Field | Type | Required | Description |
|------|------|----------|-------------|
| refreshToken | string | Yes | Valid refresh token used to generate a new access token |

## cURL

```bash
curl -X POST "https://api.weatherexample.com/v1/auth/refresh" \
-H "Content-Type: application/json" \
-d '{
  "refreshToken": "qwerty345"
}'
```
---

## Success Response
```json
{
  "success": true,
  "accessToken": "eyJhbGciOiJIUzI1NiIs...",
  "tokenType": "Bearer",
  "expiresIn": 900
}
```

---
## Response Fields

| Field | Type | Description |
|------|------|-------------|
| success | boolean | Indicates whether the token refresh succeeded |
| accessToken | string | New JWT access token |
| tokenType | string | Authentication scheme used with the access token |
| expiresIn | integer | Access token lifetime in seconds |

---

## Status Codes

| Code | Meaning |
|------|---------|
| 200 | Access token generated successfully |
| 400 | Invalid request |
| 401 | Invalid or expired refresh token |
| 429 | Too many requests |
| 500 | Internal server error |

---

## Security Notes

- Never expose refresh tokens in URLs.
- Always use HTTPS.
- Store refresh tokens securely.
- Do not log refresh tokens.
- Reject expired or revoked refresh tokens.
- Rotate refresh tokens when appropriate.

---

# POST /auth/logout

Logs out the authenticated user and invalidates the current session.

---
## URL

```http
POST https://api.weatherexample.com/v1/auth/logout
```
---
## Authentication

A valid access token is required.

Include the access token in the Authorization header.

---

## cURL

```bash
curl -X POST "https://api.weatherexample.com/v1/auth/logout" \
-H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

---

## Success Response

```json
{
  "success": true,
  "message": "User logged out successfully."
}
```
---
## Response Fields

| Field | Type | Description |
|------|------|-------------|
| success | boolean | Indicates whether the logout operation succeeded |
| message | string | Provides the result of the logout operation |

---

## Status Codes

| Code | Meaning |
|------|---------|
| 200 | User logged out successfully |
| 401 | Invalid or expired access token |
| 429 | Too many requests |
| 500 | Internal server error |

---

## Security Notes

- Always use HTTPS.
- Never expose access tokens in URLs.
- Do not log access tokens.
- Invalidate the user's session when logout is successful.
- Revoke the refresh token when appropriate.