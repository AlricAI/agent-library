# Task Agent

> # Licensed under the Apache License, Version 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ========= Copyright 2023-2026 @ CAMEL-AI.org. All Rights Reserved. =========
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
# ========= Copyright 2023-2026 @ CAMEL-AI.org. All Rights Reserved. =========
from typing import Any, Dict, List, Optional, Union

from camel.agents.chat_agent import ChatAgent
from camel.messages import BaseMessage
from camel.models import BaseModelBackend
from camel.prompts import PromptTemplateGenerator, TextPrompt
from camel.types import RoleType, TaskType
from camel.utils import get_task_list

# AgentOps decorator setting
try:
    import os

    if os.getenv("AGENTOPS_API_KEY") is not None:
        from agentops import track_agent
    else:
        raise ImportError
except (ImportError, AttributeError):
    from camel.utils import track_agent


@track_agent(name="TaskSpecifyAgent")
class TaskSpecifyAgent(ChatAgent):
    r"""An agent that specifies a given task prompt by prompting the user to
    provide more details.

    Attributes:
        DEFAULT_WORD_LIMIT (int): The default word limit for the task prompt.
        task_specify_prompt (TextPrompt): The prompt for specifying the task.

    Args:
        model (BaseModelBackend, optional): The model backend to use for
            generating responses. (default: :obj:`OpenAIModel` with
            `GPT_4O_MINI`)
        task_type (TaskType, optional): The type of task for which to generate
            a prompt. (default: :obj:`TaskType.AI_SOCIETY`)
        task_specify_prompt (Union[str, TextPrompt]

*[truncated — see source for full prompt]*