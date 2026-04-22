# Test Weather Agent

> """Integration tests for weather agent with LiteLLM and external API calls.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Integration tests for weather agent with LiteLLM and external API calls."""
import pytest
from unittest.mock import MagicMock, patch

from app.agents.weather_agent import weather_agent, WeatherAgent
from app.tools.weather_tool import get_weather


class TestWeatherTool:
    """Test the weather tool directly."""
    
    @pytest.mark.asyncio
    async def test_get_weather_success(self):
        """Test that weather tool can fetch real weather data."""
        result = await get_weather("London")
        
        assert result.location == "London"
        assert isinstance(result.temperature, float)
        assert isinstance(result.feels_like, float)
        assert isinstance(result.humidity, float)
        assert isinstance(result.wind_speed, float)
        assert isinstance(result.wind_gust, float)
        assert isinstance(result.conditions, str)
        assert result.conditions != "Unknown"
    
    @pytest.mark.asyncio
    async def test_get_weather_invalid_location(self):
        """Test that weather tool raises error for invalid location."""
        with pytest.raises(ValueError, match="not found"):
            await get_weather("XYZ123InvalidCity")


class TestWeatherAgentConfig:
    """Test weather agent configuration."""
    
    def test_agent_has_correct_config(self):
        """Test that weather agent is properly configured."""
        agent = WeatherAgent()
        assert agent.config.name == "weather-agent"
        assert agent.config.display_name == "Weather Agent"
        assert "get_weather" in agent.config.tools
    
    def test_agent_is_streaming_agent(self):
        """Test that weather agent extends BaseStreamingAgent."""
        from app.agents.base_agent import BaseStreamingAgent
        assert isinstance(weather_agent, BaseStreamingAgent)


class TestWeatherAgent:
    """Test the weather agent with LiteLLM integration."""
    
    @pytest.mark.asyncio
    async def test_agent_can_get_weather(self, mock_auth_context):
        """Test that a

*[truncated — see source for full prompt]*