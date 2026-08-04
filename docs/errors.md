# Error Handling

The Weather API uses standard HTTP status codes to indicate whether an API request was successful or failed.

When an error occurs, the API returns a JSON response containing information about the issue, including an error code, message, and additional details to help developers troubleshoot the problem.

---

# Error Response Format

All API errors follow a consistent response structure.

## Example Error Response

```json
{
  "error": {
    "code": "INVALID_API_KEY",
    "message": "The provided API key is invalid.",
    "details": "Please provide a valid API key in the Authorization header."
  }
}
```

## Error Object Fields

| Field   | Type   | Description   |
| ------- | ------ | ----------- |
| code | string | Unique identifier for the error  |
| message | string | Human-readable description of the error  |
| details | string | Additional information to help resolve the issue |

## HTTP Status Codes

The Weather API uses standard HTTP response codes.

| Status Code | Status        | Description   |
| ------| --------------------- | ------------|
| 200 | OK   | Request completed successfully      |
| 201 | Created  | Resource created successfully       |
| 400 | Bad Request | Request contains invalid parameters |
| 401 | Unauthorized  | Missing or invalid authentication credentials|
| 403 | Forbidden | User does not have permission to access the resource |
| 404 | Not Found  | Requested resource does not exist   |
| 429 | Too Many Requests     | API request limit exceeded     |
| 500 | Internal Server Error | Unexpected server-side error  |
| 503 | Service Unavailable   | API service temporarily unavailable |

---

# Common Errors

---

## 400 Bad Request

A `400 Bad Request` error occurs when the API request contains invalid or missing parameters.

### Example causes

- Missing required parameters
- Invalid parameter format
- Unsupported values

### Example Response 

```json
{
  "error": {
    "code": "INVALID_REQUEST",
    "message": "The request contains invalid parameters.",
    "details": "The city parameter is required."
  }
}
```
### How to Resolve 

- Verify all required parameters are included.
- Check parameter names and values.
- Refer to the API endpoint documentation for supported parameters.

---

## 401 Unauthorized

A `401 Unauthorized` error occurs when authentication fails.

### Example causes

- Missing API key
- Invalid API key
- Expired API key

### Example Response 

```json
{
  "error": {
    "code": "INVALID_API_KEY",
    "message": "The provided API key is invalid.",
    "details": "Include a valid API key in the Authorization header."
  }
}
```
### How to Resolve 

- Verify that your API key is correct.
- Ensure the API key is included in every request.
- Generate a new API key if the existing key has expired.

---

## 403 Forbidden

A `403 Forbidden` error occurs when authentication is successful, but the user does not have permission to access the requested resource.

### Example causes

- API plan does not support the requested feature.
- Account access restrictions.
- Insufficient permissions.

### Example Response 

```json
{
  "error": {
    "code": "ACCESS_DENIED",
    "message": "You do not have permission to access this resource.",
    "details": "Upgrade your subscription plan to access this endpoint."
  }
}
```
### How to Resolve 

- Check your API subscription plan.
- Verify account permissions.
- Contact support if access should be enabled.

---

## 404 Not Found

A `404 Not Found` error occurs when the requested resource cannot be found.

### Example causes

- Invalid endpoint URL
- Unsupported city name
- Incorrect resource identifier

### Example Response 

```json
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "The requested resource was not found.",
    "details": "No weather data found for the specified city."
  }
}
```
### How to Resolve 

- Verify the endpoint URL.
- Check spelling of city names.
- Confirm that the requested resource exists.

---

## 429 Too Many Requests

A `429 Too Many Requests` error occurs when the API request limit has been exceeded.

### Example causes

- Sending too many requests in a short period.
- Exceeding the daily request quota.

### Example Response 

```json
{
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "API request limit exceeded.",
    "details": "Please wait before sending additional requests."
  }
}
```
### How to Resolve 

- Wait until the rate limit resets.
- Reduce unnecessary API calls.
- Implement request caching.
- Use retry logic with exponential backoff.
- Upgrade your API plan for higher limits.

---

## 500 Internal Server Error 

A `500 Internal Server Error` occurs when an unexpected error happens on the server.

### Example causes

- Internal service failure
- Database issue
- Temporary processing error

### Example Response 

```json
{
  "error": {
    "code": "INTERNAL_ERROR",
    "message": "An unexpected error occurred.",
    "details": "Please try again later."
  }
}
```
### How to Resolve 

- Retry the request after a short delay.
- Check the API status page.
- Contact support if the issue continues.

---

## 503 Service Unavailable

A `503 Service Unavailable` error occurs when the API service is temporarily unavailable.

### Example causes

- Scheduled maintenance
- Temporary server overload
- Service outage

### Example Response 

```json
{
  "error": {
    "code": "SERVICE_UNAVAILABLE",
    "message": "The service is temporarily unavailable.",
    "details": "Please try again later."
  }
}
```
### How to Resolve 

- Wait and retry the request.
- Check service availability updates.
- Implement automatic retry handling.

---

# Error Handling Best Practices

Developers should follow these recommendations when handling API errors

---

## Validate Requests Before Sending

Ensure:

- Required parameters are provided.
- Parameter values are valid.
- Authentication headers are included.

---

## Implement Retry Logic

For temporary errors such as:

- 500 Internal Server Error
- 503 Service Unavailable
- 429 Too Many Requests

applications should retry requests after a delay.

---

## Log Error Details

Store the following information for debugging:

- HTTP status code
- Error code
- Timestamp
- Request endpoint
- Error message

---

## Support 

Support

If you encounter an error that cannot be resolved using this guide, contact the Weather API support team with:

- API request details
- Error response
- Timestamp of the request
- Account information

---