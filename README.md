## MCP Weather - Learning MCP Weather Server

This repository is a small learning project that implements a **Weather MCP server** using the **AccuWeather API**, and exposes it as MCP tools.

### Features

- **get_location_by_coordinates**: get location info (city name + Location Key) from latitude & longitude.
- **search_location**: search a city by name and get its Location Key.
- **get_current_weather**: get current weather conditions from a Location Key.
- **get_forecast**: get a daily weather forecast (up to 5 days) from a Location Key.

### Tech Stack

- Python
- `fastmcp` (`mcp.server.fastmcp.FastMCP`)
- `httpx`
- `python-dotenv`
- AccuWeather API

### Setup & Installation

1. **Clone the repo**

   ```bash
   git clone <this-repo-url>
   cd build-mcp
   ```

2. **Create a virtualenv (optional but recommended)**

   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install fastmcp httpx python-dotenv
   ```

4. **Set the AccuWeather API key**

   Create a `.env` file at the project root:

   ```bash
   echo "ACCUWEATHER_API_KEY=YOUR_API_KEY_HERE" > .env
   ```

   Replace `YOUR_API_KEY_HERE` with your actual AccuWeather API key.

### Running the MCP Server

Run:

```bash
python main.py
```

If it works, you should see:

```text
MCP IS RUNNING
```

You can then register this MCP server in a compatible MCP client (for example, Cursor).

### Available Tools

- **get_location_by_coordinates(latitude: float, longitude: float) -> str**
  - Example: `get_location_by_coordinates(-7.2575, 112.7521)`
  - Example output: `Location: Surabaya, East Java, Indonesia. Key: 203449`

- **search_location(query: str) -> str**
  - Example: `search_location("Surabaya")`
  - Example output: `Found: Surabaya, Indonesia. Key: 203449`

- **get_current_weather(location_key: str) -> str**
  - Example: `get_current_weather("203449")`
  - Example output: `Current Weather: Mostly cloudy, Temperature: 30.7°C`

- **get_forecast(location_key: str, days: int = 5) -> str**
  - Example: `get_forecast("203449", 5)`
  - Output: multi-line text containing the headline and a list of daily forecasts.

### Learning Notes

- This project is useful for learning:
  - How to build an MCP server with `FastMCP`.
  - How to call a REST API (AccuWeather) using `httpx`.
  - How to store sensitive configuration in `.env` using `python-dotenv`.

Feel free to modify, add new tools, or change the response format to fit your own learning goals.