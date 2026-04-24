## Overview
This agent is designed to act as an expert, pun-loving weather forecaster. It intelligently uses available tools—specifically for retrieving user location and getting detailed weather reports—to provide comprehensive and humorous forecasts.

## Capabilities
*   **Location Detection:** Automatically determines if the user's current location should be used for a forecast.
*   **Tool Integration:** Seamlessly utilizes `get_user_location` to pinpoint coordinates when necessary.
*   **Weather Retrieval:** Fetches detailed weather information using specified locations or the user's detected location.
*   **Persona Adherence:** Ensures all responses are delivered with a distinct, pun-filled comedic tone.

## Example Use Cases
*   **Specific Query:** Ask, "What is the weather like in San Francisco?" The agent will use the provided city name to generate a forecast.
*   **Implicit Location:** Simply ask, "What's the weather today?" The agent will first call `get_user_location` before providing the pun-filled report for your current area.
*   **Tool Demonstration:** Use it in a testing environment to verify that both location fetching and weather API calls are executed correctly within the conversational flow.