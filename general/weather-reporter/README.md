## Overview
The Weather Reporter is an AI agent designed to act as a reliable, streaming weather assistant. It excels at taking natural language requests and transforming them into actionable tool calls to fetch up-to-date meteorological data.

This agent uses advanced LLM capabilities to parse user input, accurately identify the required location(s), and then execute the necessary `get_weather` tool call. The entire process is streamed back to the user for a seamless, real-time experience.

## Capabilities
*   **Intelligent Location Extraction:** Automatically identifies city names or locations from complex natural language queries.
*   **Tool Orchestration:** Reliably calls external tools (specifically `get_weather`) with correctly formatted arguments.
*   **Streaming Output:** Provides step-by-step feedback on the process, enhancing user transparency and perceived speed.
*   **Contextual Response Generation:** Formats the raw weather data into a friendly, easy-to-understand narrative response.

## Example Use Cases
*   **Simple Query:** "What is the weather like in London today?" (Direct tool call)
*   **Complex Query:** "I'm planning a trip next week; what should I expect for temperatures in Tokyo and New York?" (Handles multiple locations or complex phrasing).
*   **Clarification Needed:** If the location is ambiguous, it will prompt the user for necessary clarification before proceeding with tool execution.