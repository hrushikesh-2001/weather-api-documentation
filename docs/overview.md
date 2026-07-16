# Weather API overview

## Introduction

Weather API is a RESTFUL web service that provides developers with reliable access to current weather conditions, weather forecast and weather alerts.
The API is designed for intigration with web applications, mobile applications, dashboards and Iot solutions that require weather information.
___

## Key Features 

- current weather information
- 7-Day weather forecast
- Weather alerts
- City-based weather search
- JSON response format
- Secure API authentication
- Fast and lightweightn REST endpoints

___

## Target Audience 

This API is intended for:
- software Developers
- Mobile App Developers
- Web Developers
- QA Engineers 
- Integration Engineers 
- Technical Writers

___

## User Cases

Weather API can be integrated into:
- Weather applications
- Travel applications 
- Agriculture platforms
- Logistics systems
- Fleet management software
- Smart home devices
- Iot platforms

___

## Architecture 

Client Application 

↓

HTTPS request

↓

Weather Requet

↓

Weather API

↓

Weather Database

↓

JSON Response

___

## Base URL

```Text
https://api.weatherexample.com/v1
```

___

## Supported Format

The API returns responses in JSON format.

Example:
```json
{
    "city":"Pune"
    "Temperature":31,
    "condition":"sunny"
}
```
___

## Authentication

Every request requires an API key
Example:

```http
GET /weather?city=Pune
Authorization: Bearer YOUR_API_KEY
```

___

## Versioning

Current version 
```
v1
```
Future versioning will be released without affecting existing integration whenever possible.

___

## Rate Limits

| Plan | Request |
|---|---|
| Free | 100/Day |
| pro | 1000/Day |
| Enterprise | Unlimited |

___

## Response Time 

Average response time:
- less than 300ms

___

## HTTP status Code

| code | Meaning |
|---|---|
| 200 | Success |
| 400 | Bad request | 
| 401 | Unauthorized |
| 404 | Not found |
| 429 | Too Many Request |
| 500 | Internal Server Error |

___

## Related Documents

* Authentication
* Endpoints
* Error code
* Examples 
* FAQ

