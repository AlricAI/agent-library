# Codeact Agent

> import inspect
import re
import uuid
from typing import Awaitable, Callable, List, Sequence, Union, Optional, Tuple

from llama_index.core.agent.workf

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import inspect
import re
import uuid
from typing import Awaitable, Callable, List, Sequence, Union, Optional, Tuple

from llama_index.core.agent.workflow.agent_context import AgentContext
from llama_index.core.agent.workflow.base_agent import BaseWorkflowAgent
from llama_index.core.agent.workflow.workflow_events import (
    AgentInput,
    AgentOutput,
    AgentStream,
    ToolCallResult,
)
from llama_index.core.base.llms.types import ChatResponse
from llama_index.core.bridge.pydantic import BaseModel, Field
from llama_index.core.llms import ChatMessage
from llama_index.core.llms.llm import ToolSelection, LLM
from llama_index.core.llms.function_calling import FunctionCallingLLM
from llama_index.core.memory import BaseMemory
from llama_index.core.objects import ObjectRetriever
from llama_index.core.prompts import BasePromptTemplate, PromptTemplate
from llama_index.core.tools import BaseTool, FunctionTool
from llama_index.core.workflow import Context

DEFAULT_CODE_ACT_PROMPT = """You are a helpful AI assistant that can write and execute Python code to solve problems.

You will be given a task to perform. You should output:
- Python code wrapped in <execute>...</execute> tags that provides the solution to the task, or a step towards the solution. Any output you want to extract from the code should be printed to the console.
- Text to be shown directly to the user, if you want to ask for more information or provide the final answer.
- If the previous code execution can be used to respond to the user, then respond directly (typically you want to avoid mentioning anything related to the code execution in your response).

## Response Format:
Example of proper code format:
<execute>
import math

def calculate_area(radius):
    return math.pi * radius**2

# Calculate the area for radius = 5
area = calculate_area(5)
print(f"The area of the circle is {area:.2f} square units")
</execute>

In addition to the Python Standard Library and any functions you have already written, yo

*[truncated — see source for full prompt]*