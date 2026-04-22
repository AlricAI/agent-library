# Mcp Agent Using Registry

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

import asyncio
import logging
import os

from camel.agents import MCPAgent
from camel.models import ModelFactory
from camel.types import (
    ACIRegistryConfig,
    BaseMCPRegistryConfig,
    ModelPlatformType,
    ModelType,
    # SmitheryRegistryConfig,
)

# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
)
logger = logging.getLogger('camel')
logger.setLevel(logging.DEBUG)


async def example_with_registry_config(
    message: str, registry_config: BaseMCPRegistryConfig
):
    r"""Example using MCPAgent with registry configurations."""

    # Create a model
    model = ModelFactory.create(
        model_platform=ModelPlatformType.OPENAI,
        model_type=ModelType.GPT_4O,
    )

    # Create MCPAgent with registry configurations
    agent = MCPAgent(
        model=model,
        registry_configs=[registry_config],
    )

    # Use agent with async context manager
    async with agent:
        response = await agent.astep(message)
        print(f"\nResponse from {message}:")
        print(response.msgs[0].content)


async def main():
    r"""Run examples."""
    # smithery_config = SmitheryRegistryConfig(
    #     api_key=os.getenv("SMITHERY_API_KEY"),
    #     profile=os.getenv("SMITHERY_P

*[truncated — see source for full prompt]*