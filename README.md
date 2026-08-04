# Weather API Documentation

> A comprehensive developer documentation project for a fictional Weather API. This project demonstrates technical writing skills by documenting REST API endpoints, authentication workflows, request/response examples, error handling, and developer onboarding.

---

## Overview

The Weather API enables developers to:

- Retrieve current weather information
- Get multi-day weather forecasts
- Create and manage weather alerts
- Authenticate users using JWT-based authentication

This repository showcases API documentation written in Markdown using industry-standard documentation practices.

---

## Documentation

| Document | Description |
|----------|-------------|
| Getting Started | Quick setup guide for first-time users |
| Authentication | JWT authentication workflow and endpoints |
| API Endpoints | Weather, Forecast, and Alert endpoints |
| Error Handling | Common HTTP status codes and troubleshooting |
| Rate Limits | API usage limits and retry recommendations |
| FAQ | Frequently asked questions |
| Changelog | Version history |

---

## API Features

- Current Weather API
- Weather Forecast API
- Weather Alert Management
- User Authentication
- Password Recovery
- Token Refresh
- Logout

---

## Authentication

This API uses **Bearer Token Authentication**.

Example:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

Most endpoints require a valid access token.

---

## Project Structure

```text
weather-api-documentation/
│
├── README.md
├── docs/
│   ├── getting-started.md
│   ├── authentication.md
│   ├── endpoints.md
│   ├── error-handling.md
│   ├── rate-limits.md
│   ├── faq.md
│   └── changelog.md
│
├── images/
│
└── examples/
```

---

## Example Request

```bash
curl -X GET "https://api.weatherexample.com/v1/weather?location=Pune&units=metric" \
-H "Authorization: Bearer YOUR_ACCESS_TOKEN"
```

---

## Example Response

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

## Technologies Used

- Markdown
- Git
- GitHub
- REST APIs
- HTTP
- JSON
- cURL
- JWT Authentication
- OpenAPI (work in progress)

---

## Author

**Hrushikesh Salekar**

