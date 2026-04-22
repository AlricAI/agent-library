# Multi Hop Generator Agent

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

import textwrap
from typing import Any

from pydantic import ConfigDict

from camel.agents.programmed_agent_instruction import (
    ProgrammableChatAgent,
    ProgrammedAgentInstructionResult,
    programmable_capability,
)
from camel.datagen.source2synth.models import (
    ContextPrompt,
    MultiHopQA,
)
from camel.messages import BaseMessage


class MultiHopGeneratorAgent(ProgrammableChatAgent):
    r"""An agent specialized in generating multi-hop question-answer pairs.

    This agent is designed to create complex questions that require multiple
    steps of reasoning to answer. It analyzes context to identify related
    facts and generates questions that require connecting these facts
    logically.

    Attributes:
        model_config (ConfigDict): Configuration for model behavior.
        system_message (BaseMessage): System message defining agent's role and
            instructions.
    """

    model_config = ConfigDict(arbitrary_types_allowed=True)

    def __init__(self, **kwargs: Any) -> None:
        r"""Initialize the MultiHopGeneratorAgent.

        Args:
            **kwargs (Any): Additional keyword arguments to pass to parent
                class.
        """
        super().__init__(**kwargs)

        system_text: str = textwrap.dedent(
            """\

*[truncated — see source for full prompt]*