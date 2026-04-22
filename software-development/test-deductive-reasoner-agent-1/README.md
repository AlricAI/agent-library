# Test Deductive Reasoner Agent

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
from mock import patch

from camel.agents import ChatAgent
from camel.agents.deductive_reasoner_agent import DeductiveReasonerAgent
from camel.messages import BaseMessage
from camel.responses import ChatAgentResponse
from camel.types import RoleType


@patch.object(ChatAgent, 'step')
def test_deductive_reasoner_agent(mock_step):
    mock_content = generate_mock_content()
    mock_msg = BaseMessage(
        role_name="Deductive Reasoner",
        role_type=RoleType.ASSISTANT,
        meta_dict=None,
        content=mock_content,
    )

    # Mock the step function
    mock_step.return_value = ChatAgentResponse(
        msgs=[mock_msg], terminated=False, info={}
    )

    starting_state = "I was walking down the street in New York with a Anna."
    target_state = "I remind Anna to pay attention to personal safety."

    # Construct deductive reasoner agent
    deductive_reasoner_agent = DeductiveReasonerAgent()

    # Generate the conditions and quality dictionary based on the mock step
    # function
    conditions_and_quality = (
        deductive_reasoner_agent.deduce_conditions_and_quality(
            starting_state=starting_state, target_state=target_state
        )
    )

    expected_dict = generate_expected_content()

    assert conditions_and_quality == expected_dict



*[truncated — see source for full prompt]*