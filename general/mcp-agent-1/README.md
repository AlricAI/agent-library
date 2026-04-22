# Mcp Agent

> # Licensed under the Apache License, Version 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ========= Copyright 2023-2024 @ CAMEL-AI.org. All Rights Reserved. =========
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# ========= Copyright 2023-2024 @ CAMEL-AI.org. All Rights Reserved. =========

import asyncio
import json
import platform
import re
from typing import Any, Callable, Dict, List, Optional, Union, cast

from camel.agents import ChatAgent
from camel.logger import get_logger
from camel.messages import BaseMessage
from camel.models import BaseModelBackend, ModelFactory
from camel.prompts import TextPrompt
from camel.responses import ChatAgentResponse
from camel.toolkits import FunctionTool, MCPToolkit
from camel.types import (
    BaseMCPRegistryConfig,
    MCPRegistryType,
    ModelPlatformType,
    ModelType,
    RoleType,
)

# AgentOps decorator setting
try:
    import os

    if os.getenv("AGENTOPS_API_KEY") is not None:
        from agentops import track_agent
    else:
        raise ImportError
except (ImportError, AttributeError):
    from camel.utils import track_agent

logger = get_logger(__name__)


SYS_MSG_CONTENT = """
You are a helpful assistant, and you prefer to use tools provided by the user 
to solve problems.
Using a tool, you will tell the user `server_idx`, `tool_name` and 
`tool_args` formatted in JSON as following:
```json
{
    "server_idx": idx,
    "tool_name": "tool_name",
    "tool_args": {
        "arg1": value1,
        "arg2": value2,
        ...
    }
}
```
For example:
```json
{
    "server_idx": 0,
    "tool_name": "multiply",

*[truncated — see source for full prompt]*