# Frequently Asked Questions (FAQ)

### 1. How often is the weather data updated?
Current weather observations update every 10–15 minutes across major meteorological stations. High-resolution radar and satellite overlays update every 5 minutes.

### 2. How do I get an API key?
Sign up for a free developer account at developer.weatherapp.com, navigate to your Dashboard, and click **Generate API Key**.

### 3. What units of measurement are supported?
The API supports two units models passed via the `units` query parameter:
- `metric` (default): Temperature in Celsius (°C), wind speed in meters/second (m/s), pressure in hPa.
- `imperial`: Temperature in Fahrenheit (°F), wind speed in miles/hour (mph), pressure in inHg.

### 4. What happens if I exceed my monthly API allotment?
If you exceed your account tier quota, subsequent requests return an `HTTP 429 Too Many Requests` error. You can upgrade your tier instantly from the billing dashboard.

### 5. Does the API support JSON and XML formats?
The API returns responses formatted exclusively in **JSON** to ensure modern standards and fast parsing across web and mobile SDKs.