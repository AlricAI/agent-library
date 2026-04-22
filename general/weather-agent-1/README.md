# Weather Agent

> """
Weather Agent.

A weather assistant that provides accurate weather information using tool calling.
Uses LLM-driven tool selection to intelligently

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""
Weather Agent.

A weather assistant that provides accurate weather information using tool calling.
Uses LLM-driven tool selection to intelligently extract location and format requests.

This agent extends BaseStreamingAgent with weather-specific configuration.
"""

import logging
from typing import List

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    PipelineStep,
    ToolStrategy,
)

logger = logging.getLogger(__name__)


# Weather agent synthesis prompt
WEATHER_SYSTEM_PROMPT = """You are a helpful weather assistant that provides accurate weather information.

Your primary function is to consider how accurate weather details can be used to resolve the user's question. Use the get_weather tool to get the weather details and then use the weather details to resolve the user's question.

**Available Tool:**
- **get_weather(location: str)**: Get current weather for a city. Pass just the city name (e.g., "London", "New York", "Tokyo").

**Your Workflow:**
1. Extract the location from the user's query
2. Call get_weather with the city name
3. Resolve the question in a friendly, informative format, including specific weather details when appropriate.

- If the location isn't clear, make a reasonable guess or ask for clarification

**Example:**
User: "What's the weather like in Seattle?"
→ Call get_weather(location="Seattle")
→ Format the response in a friendly way"""


class WeatherAgent(BaseStreamingAgent):
    """
    A streaming weather agent that:
    1. Uses LLM to extract location from user query
    2. Calls weather tool with extracted location
    3. Presents information in a friendly format
    
    All steps stream their progress to the user in real-time.
    """
    
    def __init__(self):
        config = AgentConfig(
            name="weather-agent",
            display_name="Weather Agent",
            instructions=WEATHER_SYSTEM_PROMPT,
            tools=["get_weather"],
            

*[truncated — see source for full prompt]*