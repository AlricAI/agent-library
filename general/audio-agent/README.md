# Audio Agent

> import io
import os
import shutil
import tempfile

import httpx
import openai
import tiktoken

import cortex.exceptions
import cortex.llm.openai.model

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import io
import os
import shutil
import tempfile

import httpx
import openai
import tiktoken

import cortex.exceptions
import cortex.llm.openai.model


class AudioAgent(cortex.llm.openai.agent.Agent):
    audio_model: cortex.llm.openai.model.AudioModel

    def __init__(
        self,
        model: cortex.llm.openai.model.CompletionModel,
        encoder: tiktoken.Encoding,
        audio_model: cortex.llm.openai.model.AudioModel,
    ):
        self.model = model
        self.encoder = encoder
        self.audio_model = audio_model
        self.functions = {
            "transcribe": cortex.llm.openai.agent.FunctionDefinition(
                func=self.transcribe,
                cache=cortex.llm.openai.agent.FunctionCache(
                    enabled=True, similarity_threshold=1.0
                ),
                direct_return=True,
                description="Transcribe an audio file.",
                parameters={
                    "type": "object",
                    "properties": {
                        "content": {
                            "type": "string",
                            "description": "What file you need to transcribe. e.g. 'https://files.slack.com/files-pri/T12345-F0S43P1CZ/audio.mp4 content', 'downloaded audio file'",
                        },
                    },
                    "required": ["content"],
                },
            ),
            "text_to_speech": cortex.llm.openai.agent.FunctionDefinition(
                func=self.text_to_speech,
                cache=cortex.llm.openai.agent.FunctionCache(
                    enabled=True, similarity_threshold=1.0
                ),
                direct_return=True,
                description="Convert a text to speech.",
                parameters={
                    "type": "object",
                    "properties": {
                        "content": {
                            "type": "string",
                            "description": "What text you need 

*[truncated — see source for full prompt]*