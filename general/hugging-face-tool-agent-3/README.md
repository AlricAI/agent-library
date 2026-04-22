# Hugging Face Tool Agent

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
from typing import Any, Optional

from camel.agents.tool_agents.base import BaseToolAgent


# flake8: noqa :E501
class HuggingFaceToolAgent(BaseToolAgent):
    r"""Tool agent for calling HuggingFace models. This agent is a wrapper
        around agents from the `transformers` library. For more information
        about the available models, please see the `transformers` documentation
        at https://huggingface.co/docs/transformers/transformers_agents.

    Args:
        name (str): The name of the agent.
        *args (Any): Additional positional arguments to pass to the underlying
            Agent class.
        remote (bool, optional): Flag indicating whether to run the agent
            remotely. (default: :obj:`True`)
        **kwargs (Any): Additional keyword arguments to pass to the underlying
            Agent class.
    """

    def __init__(
        self,
        name: str,
        *args: Any,
        remote: bool = True,
        **kwargs: Any,
    ) -> None:
        try:
            # TODO: Support other tool agents
            import transformers
            from packaging import version

            if version.parse(transformers.__version__) < version.parse(
                "4.31.0"
            ):
                raise ValueError(
                    "The versi

*[truncated — see source for full prompt]*