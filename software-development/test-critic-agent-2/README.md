# Test Critic Agent

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
import pytest

from camel.agents import CriticAgent
from camel.messages import BaseMessage
from camel.types import RoleType


@pytest.fixture
def critic_agent() -> CriticAgent:
    return CriticAgent(
        BaseMessage(
            "critic",
            RoleType.CRITIC,
            None,
            content=(
                "You are a critic who assists in selecting an option "
                "and provides explanations. "
                "Your favorite fruit is Apple. "
                "You always have to choose an option."
            ),
        )
    )


def test_flatten_options(critic_agent: CriticAgent):
    messages = [
        BaseMessage(
            role_name="user",
            role_type=RoleType.USER,
            meta_dict=dict(),
            content="Apple",
        ),
        BaseMessage(
            role_name="user",
            role_type=RoleType.USER,
            meta_dict=dict(),
            content="Banana",
        ),
    ]
    expected_output = (
        f"> Proposals from user ({RoleType.USER!s}). "
        "Please choose an option:\n"
        "Option 1:\nApple\n\n"
        "Option 2:\nBanana\n\n"
        f"Please first enter your choice ([1-{len(messages)}]) "
        "and then your explanation and comparison: "
    )
    assert critic_agent.flatten_opt

*[truncated — see source for full prompt]*