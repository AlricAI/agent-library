# Search Agent

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
from typing import Optional

from camel.agents.chat_agent import ChatAgent
from camel.messages import BaseMessage
from camel.models import BaseModelBackend
from camel.prompts import TextPrompt
from camel.types import RoleType
from camel.utils import create_chunks

# AgentOps decorator setting
try:
    import os

    if os.getenv("AGENTOPS_API_KEY") is not None:
        from agentops import track_agent
    else:
        raise ImportError
except (ImportError, AttributeError):
    from camel.utils import track_agent


@track_agent(name="SearchAgent")
class SearchAgent(ChatAgent):
    r"""An agent that summarizes text based on a query and evaluates the
    relevance of an answer.

    Args:
        model (BaseModelBackend, optional): The model backend to use for
            generating responses. (default: :obj:`OpenAIModel` with
            `GPT_4O_MINI`)
    """

    def __init__(
        self,
        model: Optional[BaseModelBackend] = None,
    ) -> None:
        system_message = BaseMessage(
            role_name="Assistant",
            role_type=RoleType.ASSISTANT,
            meta_dict=None,
            content="You are a helpful assistant.",
        )
        super().__init__(system_message, model=model)

    def summarize_text(self, text: str, query: str) -> str:
        

*[truncated — see source for full prompt]*