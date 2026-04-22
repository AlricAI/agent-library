# Test Base Agent Adapter

> from typing import Any, Dict, List, Optional

import pytest
from pydantic import BaseModel

from crewai.agent import BaseAgent
from crewai.agents.agen

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from typing import Any, Dict, List, Optional

import pytest
from pydantic import BaseModel

from crewai.agent import BaseAgent
from crewai.agents.agent_adapters.base_agent_adapter import BaseAgentAdapter
from crewai.tools import BaseTool
from crewai.utilities.token_counter_callback import TokenProcess


# Concrete implementation for testing
class ConcreteAgentAdapter(BaseAgentAdapter):
    def configure_tools(
        self, tools: Optional[List[BaseTool]] = None, **kwargs: Any
    ) -> None:
        # Simple implementation for testing
        self.tools = tools or []

    def execute_task(
        self,
        task: Any,
        context: Optional[str] = None,
        tools: Optional[List[Any]] = None,
    ) -> str:
        # Dummy implementation needed due to BaseAgent inheritance
        return "Task executed"

    def create_agent_executor(self, tools: Optional[List[BaseTool]] = None) -> Any:
        # Dummy implementation
        return None

    def get_delegation_tools(
        self, tools: List[BaseTool], tool_map: Optional[Dict[str, BaseTool]]
    ) -> List[BaseTool]:
        # Dummy implementation
        return []

    def _parse_output(self, agent_output: Any, token_process: TokenProcess):
        # Dummy implementation
        pass

    def get_output_converter(self, tools: Optional[List[BaseTool]] = None) -> Any:
        # Dummy implementation
        return None


def test_base_agent_adapter_initialization():
    """Test initialization of the concrete agent adapter."""
    adapter = ConcreteAgentAdapter(
        role="test role", goal="test goal", backstory="test backstory"
    )
    assert isinstance(adapter, BaseAgent)
    assert isinstance(adapter, BaseAgentAdapter)
    assert adapter.role == "test role"
    assert adapter._agent_config is None
    assert adapter.adapted_structured_output is False


def test_base_agent_adapter_initialization_with_config():
    """Test initialization with agent_config."""
    config = {"model": "gpt-4"}
    adapter =

*[truncated — see source for full prompt]*