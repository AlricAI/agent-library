## Overview
The Dubai Weather Reporter is a specialized AI agent designed to provide accurate, real-time weather conditions for Dubai, UAE. It utilizes a preloaded `weather-fetcher` skill to interact with external APIs and deliver concise temperature reports.

## Capabilities
*   **Real-Time Data Fetching**: Connects to the wttr.in API to retrieve current atmospheric data.
*   **Unit Flexibility**: Can report temperatures in either Celsius or Fahrenheit, based on user preference.
*   **Structured Reporting**: Provides a clear output including the temperature value, unit, and historical comparison (if memory allows).
*   **Memory Management**: Updates its internal memory with the latest reading for future trend analysis.

## Example Use Cases
*   **Daily Planning**: "What is the current temperature in Dubai so I know what to wear today?"
*   **Comparison**: "Fetch the weather now and compare it to yesterday's reading." (Relies on memory)
*   **Unit Specific Query**: "Can you check the forecast for Dubai, but please give me the temperature in Fahrenheit?"