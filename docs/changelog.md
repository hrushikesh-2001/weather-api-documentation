# Changelog

All notable changes to the Weather API are documented in this file.

The format follows semantic versioning:

**Major.Minor.Patch**

- Major: Breaking changes
- Minor: New features
- Patch: Bug fixes and improvements


## [1.0.0] - 2026-08-01

### Added

- Initial release of Weather API
- Current weather endpoint
- 7-day forecast endpoint
- API key authentication
- Request validation
- Error response handling
- Rate limiting support
- Developer documentation


### Available Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /weather/current | Get current weather information |
| GET | /weather/forecast | Get weather forecast |
| POST | /alerts | Create weather alerts |


---

## [0.9.0] - 2026-07-15

### Added

- Beta version released
- Authentication service implemented
- Basic weather data retrieval


### Known Issues

- Limited city coverage
- Forecast accuracy improvements in progress


---

## Future Releases

### Planned Features

- Historical weather data API
- Severe weather notifications
- Multiple language support
- Webhook support