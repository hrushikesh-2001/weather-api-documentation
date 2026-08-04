# Rate Limits

Rate limits define the maximum number of API requests a client can make within a specific time period.

The Weather API uses rate limiting to ensure fair usage, maintain system stability, and provide reliable performance for all users.

When a client exceeds the allowed request limit, the API temporarily blocks additional requests and returns a `429 Too Many Requests` response.

---

# Rate Limit Overview

API requests are limited based on the subscription plan associated with your API key.

| Plan | Requests per Minute | Requests per Day |
|------|---------------------|------------------|
| Free | 60 requests/minute | 5,000 requests/day |
| Developer | 300 requests/minute | 50,000 requests/day |
| Enterprise | 1,000 requests/minute | Unlimited |

---

# How Rate Limiting Works

The Weather API tracks requests using your API key.

Each successful or failed API request counts toward your rate limit.

Once the limit is reached, additional requests will return an error until the limit resets.

---

# Rate Limit Headers

The API response includes HTTP headers that provide information about your current rate limit status.

## Example Response Headers

```http
X-RateLimit-Limit: 60

X-RateLimit-Remaining: 45

X-RateLimit-Reset: 1722500000
```

