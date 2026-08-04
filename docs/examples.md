# cURL Examples

This guide provides examples of making requests to the Weather API using **cURL**.

cURL is a command-line tool used to send HTTP requests and test APIs.

Before making requests, ensure you have:

- A valid API key
- Internet connection
- cURL installed on your system

---

# Authentication

All Weather API requests require authentication using an API key.

The API key must be included in the `Authorization` header.

## Authorization Header Format

```http
Authorization: Bearer YOUR_API_KEY
```

Replace:

```
YOUR_API_KEY
```

with your actual API key.

---

# Get Current Weather

Retrieve the current weather information for a specific city.

## Endpoint

```
GET /weather/current
```

---

## Request

```bash
curl -X GET \
"https://api.weather.com/weather/current?city=Mumbai" \
-H "Authorization: Bearer YOUR_API_KEY"
```

---

## Request Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| city | string | Yes | Name of the city |

---

## Response

```json
{
  "city": "Mumbai",
  "temperature": 32,
  "humidity": 70,
  "condition": "Sunny",
  "wind_speed": 12
}
```

---

# Get Weather Forecast

Retrieve weather forecast information for multiple days.

## Endpoint

```
GET /weather/forecast
```

---

## Request

```bash
curl -X GET \
"https://api.weather.com/weather/forecast?city=Mumbai&days=7" \
-H "Authorization: Bearer YOUR_API_KEY"
```

---

## Request Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| city | string | Yes | City name |
| days | integer | No | Number of forecast days |

---

## Response

```json
{
  "city": "Mumbai",
  "forecast": [
    {
      "date": "2026-08-05",
      "temperature": 31,
      "condition": "Rain"
    },
    {
      "date": "2026-08-06",
      "temperature": 30,
      "condition": "Cloudy"
    }
  ]
}
```

---

# Create Weather Alert

Create a weather alert notification for a specific city.

## Endpoint

```
POST /alerts
```

---

## Request

```bash
curl -X POST \
"https://api.weather.com/alerts" \
-H "Authorization: Bearer YOUR_API_KEY" \
-H "Content-Type: application/json" \
-d '
{
  "city": "Mumbai",
  "alert": "Heavy Rain",
  "severity": "high"
}
'
```

---

## Request Body Parameters

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| city | string | Yes | City where alert applies |
| alert | string | Yes | Alert message |
| severity | string | Yes | Alert severity level |

---

## Response

```json
{
  "message": "Alert created successfully",
  "alert_id": "ALT12345"
}
```

---

# Using Query Parameters

Query parameters can be added directly to the API URL.

Example:

```bash
curl -X GET \
"https://api.weather.com/weather/current?city=London&units=celsius" \
-H "Authorization: Bearer YOUR_API_KEY"
```

Request:

| Parameter | Example Value |
|-----------|---------------|
| city | London |
| units | celsius |

---

# Handling API Errors

API errors return standard HTTP status codes.

Example:

```bash
curl -X GET \
"https://api.weather.com/weather/current?city=UnknownCity" \
-H "Authorization: Bearer YOUR_API_KEY"
```

Response:

```json
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "Weather data not found for the requested city."
  }
}
```

---

# Testing Without API Key

If an API key is missing, the API returns an authentication error.

## Request

```bash
curl -X GET \
"https://api.weather.com/weather/current?city=Mumbai"
```

---

## Response

```json
{
  "error": {
    "code": "INVALID_API_KEY",
    "message": "Authentication credentials are required."
  }
}
```

---

# Using cURL with Output Formatting

To display formatted JSON responses:

```bash
curl -X GET \
"https://api.weather.com/weather/current?city=Mumbai" \
-H "Authorization: Bearer YOUR_API_KEY" \
| json_pp
```

---

# Common cURL Options Used

| Option | Description |
|--------|-------------|
| `-X` | Specifies the HTTP request method |
| `-H` | Adds HTTP headers |
| `-d` | Sends request data/body |
| `-i` | Includes response headers |
| `-v` | Displays detailed request information |

---

