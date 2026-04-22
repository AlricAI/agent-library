# Image Agent

> """Image Agent.

Specialized assistant for generating images from text prompts.

Uses a predefined pipeline strategy (not LLM-driven) because:
1. The 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
"""Image Agent.

Specialized assistant for generating images from text prompts.

Uses a predefined pipeline strategy (not LLM-driven) because:
1. The generate_image tool uses a dedicated image model (e.g. gpt-image-1, FLUX)
   via the LiteLLM /images/generations endpoint - not through chat completions.
2. We don't need the chat LLM to decide *whether* to call the tool - if the user
   is talking to the Image Agent, they want an image generated.
3. The synthesis step formats the result as a markdown image so the UI renders it.
"""

import asyncio
import logging
from typing import List

from app.agents.base_agent import (
    AgentConfig,
    AgentContext,
    BaseStreamingAgent,
    ExecutionMode,
    PipelineStep,
    ToolStrategy,
)
from app.agents.streaming_agent import StreamCallback
from app.schemas.streaming import content

logger = logging.getLogger(__name__)


IMAGE_SYSTEM_PROMPT = """You are an image generation assistant.

When the user asks you to create or generate an image, use the generate_image tool.

CRITICAL: When the tool returns successfully with an image_url, you MUST respond with
a markdown image tag so the UI can display it. Use this exact format:

![Generated Image](THE_IMAGE_URL)

Optionally add a brief description below the image.

If the tool fails, explain what went wrong and suggest how to fix the prompt."""


IMAGE_SYNTHESIS_PROMPT = """You are an image generation assistant presenting results.

You will receive tool results from an image generation. Your job is to present them
to the user in a clear way.

CRITICAL RULES:
- If the tool returned an image_url, you MUST include it as a markdown image:
  ![Generated Image](THE_IMAGE_URL)
- If there is a revised_prompt, mention what was changed.
- If the tool failed, explain the error and suggest improvements.
- Keep your text brief - the image is the star."""


class ImageAgent(BaseStreamingAgent):
    """Agent specialized in text-to-image workflows.
    
    Uses PREDEFINED_PIPELINE strategy t

*[truncated — see source for full prompt]*