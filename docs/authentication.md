# Authentication 

## Overview

The Weather API uses API key authentication to authorize requests. Every request must include a valid API key in the Authorization header.
Request without a valid API key will be rejected.

___

## Authentication Method

Authentication Type:

### Bearer Token
Every request must include:
``` http
Authorization: Bearer Your_API_KEY
```

Example:
```http
GET/weather?city=pune HTTP/1.1
Host: api.weatherexample.com
Authorization: Bearer YOUR_API_KEY
```

___

## Obtaining an API key

To access the Weather API:
1. Create an account.
2. Generate an API key from the Developer Dashboard.
3. Copy the generated key.
4. Include it in every API request.

Example API Key:
```text
qw_ert_y1u3i4o12xxxxvvvaaa
```

___

## Request Header

| Header | Required | Description |
| --- | --- | --- |
| Authorization | Yes | Bearer authentication token |
| Content-Type | Yes | application/json |

___

## Example Request 

```http
GET https://api.weatherexample.com/v1/weather?city=pune

Authorization: Bearer YOUR_API_KEY
```

___

## Successful Response

```http
HTTP/1.1 200 OK
```

___

## Authentication Errors

### 401 Unauthorized 

Returned when the API key is missing or invalid.

Example:
```json
{
    "error":"Unauthorized"
    "message":"Invalid API key"
}
```

___

### 403 Forbidden

Return when the API key does not have permission to access the required resource.

Example: 
```json
{
    "error":"Forbidden"
    "message":"Access denied"
}

```

___

## Security Best Practices

- Never expose API keys in public repositories
- Rotate API keys regularly.
- Store API keys securely using environment variables.
- Use HTTPS for all requests.
- Do not share API keys with unauthorized users.

___

## Authentication Flow

Developer 

↓

Obtain API key

↓

Send API request 

↓

Weather API validates API key

↓

Request Accepted or Rejected

___

## API Key Expiration 

API keys remain valid until they are revoked or regenerated from the Developer Dashboard.
It the key is regenerated, the previous key immediately becomes invalid.

___

## Releted Documents

- Overview
- API Endpoints
- Error Codes
- Examples
