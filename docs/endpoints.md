# API Endpoints

___
## Table of Contents

- [GET /weather](#get-weather)
- [GET /forecast](#get-forecast)
- [POST /alerts](#post-alerts)
- [PUT /alerts](#put-alerts)

---

# GET /weather

Returns the current weather information for specified city.

## URL

```http
GET https://api.weatherexample.com/v1/weather
```

## Authentication 

This endpoint requires Bearer token authentication.

Include the access token in the `Authorization` header.

Authorization: Bearer YOUR_API_KEY

___

## Query Parameters

| Parameter | Type | Required | Description |
|-----|-----|-----|-----|
| location | String | Yes | Name of the city |
| units | String | No | Metric or Imperial |

___
## cURL Example Request

```bash
curl -X GET "https://api.weatherexample.com/v1/weather?location=Pune&units=metric" \
-H "Authorization: Bearer YOUR_API_KEY"
```
___

## Example Response 

```json
{ 
    "location":"pune",
    "temperature": 31,
    "humidity": 62,
    "condition": "sunny",
    "wind_speed": 8
}
```

___

## Success Response 

| Code | Description |
| ----|-----|
| 200 | Weather data returned successfully |

___

## Error response 

| Status Code | Reason                       | Solution                        |
| ----------- | ---------------------------- | ------------------------------- |
| 400         | Missing required parameter   | Provide all required parameters |
| 401         | Invalid or expired API key   | Generate a new API key          |
| 403         | Access denied                | Verify account permissions      |
| 404         | Requested resource not found | Check endpoint or location name |
| 429         | Rate limit exceeded          | Wait before retrying            |
| 500         | Internal server error        | Retry later or contact support  |

___

## Best Practices

- Always use HTTPS.
- Never expose API keys in public repositories.
- Handle HTTP error responses gracefully.
- Retry temporary failures using exponential backoff.
- Validate user input before sending requests.

---

# GET /forecast

Returns weather forecast data for the specified location and date range.

## URL 

```http
GET https://api.weatherexample.com/v1/forecast
```

## AUthentication 

This endpoint requires Bearer token authentication.

Include the access token in the `Authorization` header.

Authorization: Bearer YOUR_API_KEY
___

## Query Parameters

| Parameter | Type | Required | Description |
|-----|-----|-----|-----|
| location | String | Yes | Name of the city |
| units | String | No | Metric or Imperial |
| Date | String | Yes | Date for forecast |

___

## cURL Example Request

```bash
curl -X GET "https://api.weatherexample.com/v1/forecast?location=Pune&units=metric&date=21-07-2026to23-07-2026" \
-H "Authorization: Bearer YOUR_API_KEY"
```
___

## Example Response 

```json
{
    "location": "pune",
    "forecast":[
    {
      "date": "21-07-2026",
      "day_of_week": "Tuesday",
      "temp_high": 28,
      "temp_low": 22,
      "condition": "Scattered Showers",
      "precipitation_chance_pct": 70,
      "humidity_pct": 85
    },
    {
      "date": "22-07-2026",
      "day_of_week": "Wednesday",
      "temp_high": 27,
      "temp_low": 21,
      "condition": "Moderate Rain",
      "precipitation_chance_pct": 85,
      "humidity_pct": 88
    },
    {
      "date": "23-07-2026",
      "day_of_week": "Thursday",
      "temp_high": 27,
      "temp_low": 21,
      "condition": "Moderate Rain",
      "precipitation_chance_pct": 85,
      "humidity_pct": 88
    }
    ]
}
```
---
## Response Fields

| Field   | Type    | Description |
| ------- | ------- |---------------|
| location | String| Name of the city |
| units | String | Metric or Imperial |
| Date | String | Date for forecast |
| temperature | integer | temperature in Celsius |
| humidity_pct | integer | Relative humidity (%) |
| condition | string  | Current weather condition |

---
## Success Response 

| Code | Description |
| ----|-----|
| 200 | Weather forecast returned successfully |

---

## Error response 

| Status Code | Reason                       | Solution                        |
| ----------- | ---------------------------- | ------------------------------- |
| 400         | Missing required parameter   | Provide all required parameters |
| 401         | Invalid or expired API key   | Generate a new API key          |
| 403         | Access denied                | Verify account permissions      |
| 404         | Requested resource not found | Check endpoint or location name |
| 429         | Rate limit exceeded          | Wait before retrying            |
| 500         | Internal server error        | Retry later or contact support  |

---
## Best Practices

- Always use HTTPS.
- Never expose API keys in public repositories.
- Handle HTTP error responses gracefully.
- Retry temporary failures using exponential backoff.
- Validate user input before sending requests.
---

# POST /alerts

Creates a new weather alert for the specified conditions.

## URL

```http
POST https://api.weatherexample.com/v1/alerts
```

## AUthentication 

This endpoint requires Bearer token authentication.

Include the access token in the `Authorization` header.

Authorization: Bearer YOUR_API_KEY
___
## cURL Example Request

```bash
curl -X POST "https://api.weatherexample.com/v1/alerts" \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-Type: application/json" \
-d '{
  "location": "pune",
  "temperature": 35,
  "unit": "Celsius",
  "condition": "greater_than",
  "notification_channel": "email",
  "recipient": "user@hotmail.com"
}'
```
---
## Example Response 

```json
{
    "success": true,
    "message": "temperature alert created successfully.",
    "data": {
        "alert id": "alt_121",
        "status": "active",
        "temperature": 35,
        "unit": "Celsius",
        "condition": "greater_than"
    }
}
```
---

## Response Fields 

| Field            | Type    | Description                             |
| ---------------- | ------- | --------------------------------------- |
| success          | boolean | Indicates whether the request succeeded |
| message          | string  | Success message                         |
| data.alertId     | string  | Unique identifier of the created alert  |
| data.status      | string  | Current alert status                    |
| data.temperature | integer | Configured threshold                    |
| data.unit        | string  | Temperature unit                        |



## Success Response 

| Code | Description |
| ----|-----|
| 201 | temperature alert created successfully |

___

## Error response 

| Status Code | Reason                       | Solution                        |
| ----------- | ---------------------------- | ------------------------------- |
| 400         | Missing required parameter   | Provide all required parameters |
| 401         | Invalid or expired API key   | Generate a new API key          |
| 403         | Access denied                | Verify account permissions      |
| 404         | Requested resource not found | Check endpoint or location name |
| 429         | Rate limit exceeded          | Wait before retrying            |
| 500         | Internal server error        | Retry later or contact support  |

___

## Best Practices

- Always use HTTPS.
- Never expose API keys in public repositories.
- Handle HTTP error responses gracefully.
- Retry temporary failures using exponential backoff.
- Validate user input before sending requests.

---
# PUT /alerts

Updates an existing weather alert.

## URL

```http
PUT https://api.weatherexample.com/v1/alerts/alt_121
```

## AUthentication 

This endpoint requires Bearer token authentication.

Include the access token in the `Authorization` header.

Authorization: Bearer YOUR_API_KEY

___

## cURL Example Request

```bash
curl -X PUT "https://api.weatherexample.com/v1/alerts/alt_121" \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-Type: application/json" \
-d '{
  "location": "pune",
  "temperature": 38,
  "unit": "Celsius",
  "condition": "greater_than",
  "notification_channel": "sms",
  "recipient": "+91 742xxxx133"
}'
```
___

## Example Response 

```json
{
    "success": true,
    "message": "temperature alert updated successfully.",
    "data": {
        "alert id": "alt_121",
        "status": "active",
        "temperature": 38,
        "unit": "Celsius",
        "condition": "greater_than",
        "notification_channel": "sms",
        "recipient": "+91 742xxxx133"
    }
}
```
___

## Response Fields

| Field   | Type    | Description |
| ------- | ------- |---------------|
| success | boolean | Indicates whether the request succeeded |
| message | string  | Status message                          |
| alertId | string  | Unique identifier of the alert          |
| status  | string  | Current alert status                    |
___

## Success Response 

| Code | Description |
| ----|-----|
| 200 | temperature alert updated successfully |

___

## Error response 

| Status Code | Reason                       | Solution                        |
| ----------- | ---------------------------- | ------------------------------- |
| 400         | Missing required parameter   | Provide all required parameters |
| 401         | Invalid or expired API key   | Generate a new API key          |
| 403         | Access denied                | Verify account permissions      |
| 404         | Requested resource not found | Check endpoint or location name |
| 429         | Rate limit exceeded          | Wait before retrying            |
| 500         | Internal server error        | Retry later or contact support  |

___

## Best Practices

- Always use HTTPS.
- Never expose API keys in public repositories.
- Handle HTTP error responses gracefully.
- Retry temporary failures using exponential backoff.
- Validate user input before sending requests.

---
