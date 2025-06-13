# OpenWeatherMap MCP Server

A Model Context Protocol (MCP) server that provides comprehensive weather data and forecasts through the OpenWeatherMap API. This server enables AI assistants to access real-time weather information, forecasts, air quality data, and location services.

<a href="https://glama.ai/mcp/servers/@robertn702/mcp-openweathermap">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@robertn702/mcp-openweathermap/badge" alt="OpenWeatherMap Server MCP server" />
</a>

## Features

### Weather Tools
- **Current Weather** - Get current conditions for any location
- **Weather Forecast** - 5-day weather forecast with 3-hour intervals
- **Hourly Forecast** - Detailed hourly forecasts for up to 48 hours
- **Daily Forecast** - Daily weather forecasts for up to 8 days with temperature ranges and astronomical data
- **Minutely Forecast** - Minute-by-minute precipitation forecasts for the next hour
- **Weather Alerts** - Active weather warnings and alerts with severity classification

### Air Quality & Location
- **Current Air Pollution** - Real-time air quality index and pollutant measurements
- **Location Info** - Reverse geocoding to get location details from coordinates
- **OneCall Weather** - Comprehensive weather data combining multiple forecasts
- **Air Pollution** - Historical and forecast air quality data
- **Geocoding** - Convert location names to coordinates

## Installation

### Prerequisites
- [Bun](https://bun.sh) runtime
- OpenWeatherMap API key (free at [openweathermap.org](https://openweathermap.org/api))

### Setup

1. Clone the repository:
```bash
git clone https://github.com/robertn702/mcp-openweathermap.git
cd mcp-openweathermap
```

2. Install dependencies:
```bash
bun install
```

3. Set up your environment variables:
```bash
cp .env.example .env
# Edit .env and add your OpenWeatherMap API key
```

Environment variables:
- `OPENWEATHER_API_KEY` - Your OpenWeatherMap API key (required for stdio transport only)
- `PORT` - Server port for HTTP transport (default: 3000)
- `MCP_TRANSPORT` - Transport type: `stdio` or `httpStream` (default: stdio)
- `MCP_ENDPOINT` - HTTP endpoint path (default: /stream)

## Usage

### Running the Server

**Stdio Transport (default):**
```bash
bun run src/main.ts
```

**HTTP Stream Transport:**
```bash
MCP_TRANSPORT=httpStream PORT=3000 bun run src/main.ts
```

### Claude Desktop Configuration

Add this configuration to your Claude Desktop MCP settings:

```json
{
  "mcpServers": {
    "openweathermap": {
      "command": "npx",
      "args": ["mcp-openweathermap"],
      "env": {
        "OPENWEATHER_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

## API Tools

### Weather Information
- `get-current-weather` - Current weather conditions
- `get-weather-forecast` - 5-day forecast  
- `get-hourly-forecast` - Hourly forecasts (up to 48 hours)
- `get-daily-forecast` - Daily forecasts (up to 8 days)
- `get-minutely-forecast` - Minute-by-minute precipitation

### Alerts & Air Quality  
- `get-weather-alerts` - Weather warnings and alerts
- `get-current-air-pollution` - Current air quality data
- `get-air-pollution` - Air quality forecasts and history

### Location Services
- `get-location-info` - Reverse geocoding from coordinates
- `geocode-location` - Convert addresses to coordinates
- `get-onecall-weather` - Comprehensive weather data

## Development

### Running in Development
```bash
bun run src/main.ts
```

### Testing with MCP Inspector
```bash
bun run src/main.ts
```

Then connect the MCP Inspector to test the tools interactively.

### Build
```bash
bun run build
```

## Authentication

**Stdio Transport:** Requires `OPENWEATHER_API_KEY` environment variable.

**HTTP Transport:** The OpenWeatherMap API key is passed as a bearer token in the HTTP request headers. No environment variable needed.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

- [OpenWeatherMap API Documentation](https://openweathermap.org/api)
- [openweather-api-node Library](https://github.com/loloToster/openweather-api-node) - The underlying API client
- [Model Context Protocol Documentation](https://modelcontextprotocol.io)
- [Issue Tracker](https://github.com/robertn702/mcp-openweathermap/issues)