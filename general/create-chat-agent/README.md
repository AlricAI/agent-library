# Create Chat Agent

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

from camel.agents import ChatAgent
from camel.models import ModelFactory
from camel.types import ModelPlatformType, ModelType

# Method 1: Initialize the agent with just a string (model name)
# This uses the default platform (OpenAI)
agent_1 = ChatAgent("You are a helpful assistant.", model="gpt-4o-mini")

# Method 2: Initialize with just a `enum` for model type.
agent_2 = ChatAgent(
    "You are a helpful assistant.",
    model=ModelType.GPT_4O_MINI,
)

# Method 3: Initialize the agent with a tuple (platform, model)
agent_3 = ChatAgent(
    "You are a helpful assistant.",
    model=("anthropic", "claude-sonnet-4-5"),
)

# Method 4: Initialize the agent with a `tuple` of `enum`
agent_4 = ChatAgent(
    "You are a helpful assistant.",
    model=(ModelPlatformType.ANTHROPIC, ModelType.CLAUDE_HAIKU_4_5),
)

# Method 5: Default model when none is specified.
agent_5 = ChatAgent("You are a helpful assistant.")

# Method 6: Initialize with a pre-created model (original approach)
model = ModelFactory.create(
    model_platform=ModelPlatformType.OPENAI,  # Using enum
    model_type=ModelType.GPT_4O_MINI,  # Using enum
)
agent_6 = ChatAgent("You are a helpful assistant.", model=model)

# Method 7: Initialize with a pre-created model using strings
model = ModelFactory.create(
    model_p

*[truncated — see source for full prompt]*