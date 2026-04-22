# Test Base Tool Adapter

> from typing import Any, List
from unittest.mock import Mock

import pytest

from crewai.agents.agent_adapters.base_tool_adapter import BaseToolAdapter

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from typing import Any, List
from unittest.mock import Mock

import pytest

from crewai.agents.agent_adapters.base_tool_adapter import BaseToolAdapter
from crewai.tools.base_tool import BaseTool


class ConcreteToolAdapter(BaseToolAdapter):
    def configure_tools(self, tools: List[BaseTool]) -> None:
        self.converted_tools = [f"converted_{tool.name}" for tool in tools]


@pytest.fixture
def mock_tool_1():
    tool = Mock(spec=BaseTool)
    tool.name = "Mock Tool 1"
    return tool


@pytest.fixture
def mock_tool_2():
    tool = Mock(spec=BaseTool)
    tool.name = "MockTool2"
    return tool


@pytest.fixture
def tools_list(mock_tool_1, mock_tool_2):
    return [mock_tool_1, mock_tool_2]


def test_initialization_with_tools(tools_list):
    adapter = ConcreteToolAdapter(tools=tools_list)
    assert adapter.original_tools == tools_list
    assert adapter.converted_tools == []  # Conversion happens in configure_tools


def test_initialization_without_tools():
    adapter = ConcreteToolAdapter()
    assert adapter.original_tools == []
    assert adapter.converted_tools == []


def test_configure_tools(tools_list):
    adapter = ConcreteToolAdapter()
    adapter.configure_tools(tools_list)
    assert adapter.converted_tools == ["converted_Mock Tool 1", "converted_MockTool2"]
    assert adapter.original_tools == []  # original_tools is only set in init

    adapter_with_init_tools = ConcreteToolAdapter(tools=tools_list)
    adapter_with_init_tools.configure_tools(tools_list)
    assert adapter_with_init_tools.converted_tools == [
        "converted_Mock Tool 1",
        "converted_MockTool2",
    ]
    assert adapter_with_init_tools.original_tools == tools_list


def test_tools_method(tools_list):
    adapter = ConcreteToolAdapter()
    adapter.configure_tools(tools_list)
    assert adapter.tools() == ["converted_Mock Tool 1", "converted_MockTool2"]


def test_tools_method_empty():
    adapter = ConcreteToolAdapter()
    assert adapter.tools() == []


def test_sani

*[truncated — see source for full prompt]*