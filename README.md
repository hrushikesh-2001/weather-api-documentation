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

## Documentation

| Guide | Description |
|------|-------------|
| [Overview](docs/overview.md) | Learn about the Weather API and its features. |
| [Getting Started](docs/getting-started.md) | Make your first API request. |
| [Authentication](docs/authentication.md) | Understand JWT authentication. |
| [Authentication API](docs/auth-api.md) | Register, login, refresh, reset password, and logout endpoints. |
| [API Endpoints](docs/endpoints.md) | Weather, Forecast, and Alert endpoints. |
| [Error Handling](docs/error-handling.md) | HTTP status codes and troubleshooting. |
| [Rate Limits](docs/rate-limits.md) | Request limits and retry guidance. |
| [FAQ](docs/faq.md) | Frequently asked questions. |
| [cURL Examples](examples/curl-examples.md) | Ready-to-use API request examples. |
| [Changelog](docs/changelog.md) | API version history. |

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

## About this Project

This project is created to demonstrate my technical writing skills.

The API is fictional and was designed to practice documenting REST APIs using industry-standard documentation practices including Markdown, Git, GitHub, cURL examples, HTTP status codes, and authentication workflows.

## Author

**Hrushikesh Salekar**

