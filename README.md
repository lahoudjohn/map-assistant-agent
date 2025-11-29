# Map Assistant Agent

An AI-powered map assistant agent built with OpenAI Agents SDK that provides geocoding, routing, and point-of-interest (POI) search capabilities using OpenStreetMap and OSRM services.

## Features

- **Geocoding**: Convert human-readable addresses to coordinates using OpenStreetMap Nominatim
- **Reverse Geocoding**: Convert coordinates back to human-readable addresses
- **POI Search**: Search for points of interest (restaurants, shops, etc.) in any city
- **Route Planning**: Calculate routes between addresses or coordinates
- **Travel Time Estimation**: Estimate travel times and distances using routing algorithms

## Architecture

The project consists of:

- **`agent_main.py`**: Main entry point with the MapAssistant agent and interactive REPL
- **`osm_server.py`**: OpenStreetMap integration functions (geocoding, reverse geocoding, POI search)
- **`routing_server.py`**: Routing and navigation functions using OSRM
- **`config.py`**: Configuration management for API endpoints and parameters

## Prerequisites

- Python 3.8 or higher
- OpenAI API key

## Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd Assignment5
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Create a `.env` file in the project root:
```env
OPENAI_API_KEY=your_openai_api_key_here
```

## Usage

Run the interactive map assistant:

```bash
python -m src.agent_main
```

The agent will start in interactive mode. You can ask questions like:

- "What are the coordinates of Paris, France?"
- "Find coffee shops in New York"
- "How long does it take to travel from Times Square to Central Park?"
- "Give me a route from San Francisco to Los Angeles"

Type `quit` or `exit` to close the application.

## API Functions

### OpenStreetMap Functions

- **`osm_geocode(address: str)`**: Geocode an address to coordinates
- **`osm_reverse_geocode(lat: float, lon: float)`**: Reverse geocode coordinates to an address
- **`osm_search_poi(query: str, city: str)`**: Search for points of interest in a city

### Routing Functions

- **`route_between_coords(lat1, lon1, lat2, lon2, profile="driving")`**: Get route between coordinates
- **`route_between_addresses(origin, destination, profile="driving")`**: Get route between addresses
- **`estimate_travel_time_km(lat1, lon1, lat2, lon2)`**: Estimate travel time and distance

## Configuration

Edit `src/config.py` to customize:

- OpenStreetMap base URL and user agent
- OSRM routing server base URL
- Request timeout settings

**Note**: The OpenStreetMap Nominatim service has usage policies. For production use, consider:
- Using your own Nominatim instance
- Adding rate limiting
- Implementing caching

## Testing

Run the test suite:

```bash
pytest tests/
```

Tests are available for:
- OSM geocoding functionality (`test_osm_server.py`)
- Routing and travel time estimation (`test_routing_server.py`)

## Project Structure

```
Assignment5/
├── src/
│   ├── agent_main.py          # Main agent application
│   ├── config.py              # Configuration settings
│   ├── osm_server.py          # OpenStreetMap integration
│   └── routing_server.py      # Routing and navigation
├── tests/
│   ├── test_osm_server.py     # OSM server tests
│   └── test_routing_server.py # Routing server tests
├── requirements.txt           # Python dependencies
└── README.md                  # This file
```

## Dependencies

- `openai>=1.40.0`: OpenAI SDK
- `openai-agents>=0.3.0`: OpenAI Agents framework
- `httpx>=0.27.0`: Async HTTP client
- `python-dotenv>=1.0.1`: Environment variable management
- `pytest>=8.0.0`: Testing framework

## License

This project is part of an assignment. Please refer to your course guidelines for usage rights.

## Contributing

This is an assignment project. For improvements or issues, please contact the course instructor.

## Acknowledgments

- OpenStreetMap Nominatim for geocoding services
- OSRM for routing services
- OpenAI for the Agents SDK

