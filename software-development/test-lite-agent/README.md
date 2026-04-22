# Test Lite Agent

> import threading
from collections import defaultdict
from typing import cast
from unittest.mock import Mock, patch

from crewai.events.event_bus impor

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# mypy: ignore-errors
import threading
from collections import defaultdict
from typing import cast
from unittest.mock import Mock, patch

from crewai.events.event_bus import crewai_event_bus
from crewai.events.types.agent_events import LiteAgentExecutionStartedEvent
from crewai.events.types.tool_usage_events import ToolUsageStartedEvent
from crewai.lite_agent import LiteAgent
from crewai.lite_agent_output import LiteAgentOutput
from crewai.llms.base_llm import BaseLLM
from pydantic import BaseModel, Field
import pytest

from crewai import LLM, Agent
from crewai.flow import Flow, start
from crewai.tools import BaseTool
from crewai.types.usage_metrics import UsageMetrics


# A simple test tool
class SecretLookupTool(BaseTool):
    name: str = "secret_lookup"
    description: str = "A tool to lookup secrets"

    def _run(self) -> str:
        return "SUPERSECRETPASSWORD123"


# Define Mock Search Tool
class WebSearchTool(BaseTool):
    """Tool for searching the web for information."""

    name: str = "search_web"
    description: str = "Search the web for information about a topic."

    def _run(self, query: str) -> str:
        """Search the web for information about a topic."""
        # This is a mock implementation
        if "tokyo" in query.lower():
            return "Tokyo's population in 2023 was approximately 21 million people in the city proper, and 37 million in the greater metropolitan area."
        if "climate change" in query.lower() and "coral" in query.lower():
            return "Climate change severely impacts coral reefs through: 1) Ocean warming causing coral bleaching, 2) Ocean acidification reducing calcification, 3) Sea level rise affecting light availability, 4) Increased storm frequency damaging reef structures. Sources: NOAA Coral Reef Conservation Program, Global Coral Reef Alliance."
        return f"Found information about {query}: This is a simulated search result for demonstration purposes."


# Define Mock Calculator Tool
class Calc

*[truncated — see source for full prompt]*