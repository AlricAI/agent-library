#  Tool Definitions

> from typing import Any, Dict

from autogen_core.tools._base import ParametersSchema, ToolSchema


def _load_tool(tooldef: Dict[str, Any]) -> ToolSchem

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from typing import Any, Dict

from autogen_core.tools._base import ParametersSchema, ToolSchema


def _load_tool(tooldef: Dict[str, Any]) -> ToolSchema:
    return ToolSchema(
        name=tooldef["function"]["name"],
        description=tooldef["function"]["description"],
        parameters=ParametersSchema(
            type="object",
            properties=tooldef["function"]["parameters"]["properties"],
            required=tooldef["function"]["parameters"]["required"],
        ),
    )


REASONING_TOOL_PROMPT = (
    "A short description of the action to be performed and reason for doing so, do not mention the user."
)

TOOL_VISIT_URL: ToolSchema = _load_tool(
    {
        "type": "function",
        "function": {
            "name": "visit_url",
            "description": "Navigate directly to a provided URL using the browser's address bar. Prefer this tool over other navigation techniques in cases where the user provides a fully-qualified URL (e.g., choose it over clicking links, or inputing queries into search boxes).",
            "parameters": {
                "type": "object",
                "properties": {
                    "reasoning": {
                        "type": "string",
                        "description": REASONING_TOOL_PROMPT,
                    },
                    "url": {
                        "type": "string",
                        "description": "The URL to visit in the browser.",
                    },
                },
                "required": ["reasoning", "url"],
            },
        },
    }
)

TOOL_WEB_SEARCH: ToolSchema = _load_tool(
    {
        "type": "function",
        "function": {
            "name": "web_search",
            "description": "Performs a web search on Bing.com with the given query.",
            "parameters": {
                "type": "object",
                "properties": {
                    "reasoning": {
                        "type": "string",
                        "description":

*[truncated — see source for full prompt]*