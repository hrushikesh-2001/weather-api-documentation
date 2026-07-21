# API Endpoints

___

# GET /weather

Returns the current weather information for specified city.

## URL

```http
GET https://api.weatherexample.com/v1/weather
```

## Authentication 

Bearer token Required

___

## Query Parameters

| Parameter | Type | Required | Description |
|-----|-----|-----|-----|
| location | String | Yes | Name of the city |
| units | String | No | Metric or Imperial |

___

```http
GET /v1/weather?location=pune&units=metric

Authorization: Bearer YOUR_API_KEY
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

| Code | Meaning |
| -----|-----|
| 400 | Missing location parameter |
| 401 | Unauthorized |
| 404 | location not found |
| 500 | Internal Server Error |

___

## Notes

- location name is case-sensitive.
- units default to metric 

___

# GET /Forecast

Returns the weather forecast for the requested dates.

## URL 

```http
GET https://api.weatherexample.com/v1/forecast
```

## AUthentication 

Bearer token Required

___

## Query Parameters

| Parameter | Type | Required | Description |
|-----|-----|-----|-----|
| location | String | Yes | Name of the city |
| units | String | No | Metric or Imperial |
| Date | String | Yes | Date for forecast |

___

```http
GET https://api.weatherexample.com/v1/forecast?location=pune&units=metric&date=21-07-2026to23-07-2026

Authorization: Bearer YOUR_API_KEY
```
___

## Example Response 

```json
{
    "location": "pune",
    "Forecast":[
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

___

## Success Response 

| Code | Description |
| ----|-----|
| 200 | Weather forecast returned successfully |

___

## Error response 

| Code | Meaning |
| -----|-----|
| 400 | Missing location or date parameter |
| 401 | Unauthorized |
| 404 | location not found or Unsupported date range |
| 500 | Internal Server Error |

___

## Note 

- location name is case-sensitive.
- units default to metric 
- Date format : DD/MM/YY

___

# POST /alerts

Creates a new weather alert.

## URL

```http
POST https://api.weatherexample.com/v1/alerts
```

## AUthentication 

Bearer token Required

___

## Request Body 

| Field | Type | Required | Description |
|-----|-----|-----|-----|
| location | String | Yes | Name of the city |
| temperature | integer | yes | Metric or imperial |
| unit | String | yes | Metric or imperial |
| condition | String | yes | Greater than or less than |
| Notification channel | String | yes | platform where alert will be returned |
| recipient | string | yes | Recipents id |

___

```http
POST https://api.weatherexample.com/v1/alerts
Content-Type: application/json
Authorization: Bearer YOUR_API_KEY

{
  "location": "pune",
  "temperature": 35,
  "unit": "Celsius",
  "condition": "greater_than",
  "notification_channel": "email",
  "Recipient": "user@hotmail.com"
}
```
___

## Example Response 

```json
{
    "success": true,
    "message": "temperature alert created successfully."
    "data": {
        "alert id": "alt_121",
        "status": "active",
        "temperature": 35,
        "unit": "Celsius",
        "condition": "greater_than"
    }
}
```
___

## Success Response 

| Code | Description |
| ----|-----|
| 201 | temperature alert created successfully |

___

## Error response 

| Code | Meaning |
| -----|-----|
| 400 | Missing parameter or bad request |
| 401 | Unauthorized |
| 404 | location not found or out-of-range request |
| 500 | Internal Server Error |

___

# PUT /alerts

Updates an existing weather alert.

## URL

```http
PUT https://api.weatherexample.com/v1/alerts/alt_121
```

## AUthentication 

Bearer token Required

___

```http
PUT /alerts/alt_121
Content-Type: application/json
Authorization: Bearer YOUR_API_KEY

{
  "location": "pune",
  "temperature": 38,
  "unit": "Celsius",
  "condition": "greater_than",
  "notification_channel": "sms",
  "Recipient": "+91 742xxxx133" 
}
```
___

## Example Response 

```json
{
    "success": true,
    "message": "temperature alert updated successfully."
    "data": {
        "alert id": "alt_121",
        "status": "active",
        "temperature": 38,
        "unit": "Celsius",
        "condition": "greater_than",
        "notification_channel": "sms",
        "Recipient": "+91 742xxxx133"
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

| Code | Meaning |
| -----|-----|
| 400 | Missing parameter or bad request |
| 401 | Unauthorized |
| 404 | location not found or out-of-range request |
| 500 | Internal Server Error |

___

