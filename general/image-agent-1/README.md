# Image Agent

> import base64
import io
import os.path
import tempfile

import PIL.Image
import httpx
import openai
import tiktoken

import cortex.exceptions
import c

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import base64
import io
import os.path
import tempfile

import PIL.Image
import httpx
import openai
import tiktoken

import cortex.exceptions
import cortex.llm.openai.model


class ImageAgent(cortex.llm.openai.agent.Agent):
    image_model: cortex.llm.openai.model.ImageModel

    def __init__(
        self,
        model: cortex.llm.openai.model.CompletionModel,
        encoder: tiktoken.Encoding,
        image_model: cortex.llm.openai.model.ImageModel,
    ):
        self.model = model
        self.encoder = encoder
        self.image_model = image_model
        self.functions = {
            "explain_image": cortex.llm.openai.agent.FunctionDefinition(
                func=self.explain_image,
                cache=cortex.llm.openai.agent.FunctionCache(
                    enabled=True, similarity_threshold=1.0
                ),
                direct_return=True,
                description="Explains an image given a content.",
                parameters={
                    "type": "object",
                    "properties": {
                        "content": {
                            "type": "string",
                            "description": "What image you need to explain. e.g. 'https://files.slack.com/files-pri/T12345-F0S43P1CZ/image.png content', 'screenshotted image'",
                        },
                    },
                    "required": ["content"],
                },
            ),
            "generate_image": cortex.llm.openai.agent.FunctionDefinition(
                func=self.generate_image,
                direct_return=True,
                description="Creates an image given a prompt.",
                parameters={
                    "type": "object",
                    "properties": {
                        "prompt": {
                            "type": "string",
                            "description": "A text description of the desired image(s). The maximum length is 1000 characters.",
                        },
       

*[truncated — see source for full prompt]*