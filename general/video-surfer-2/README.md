#  Video Surfer

> from typing import Any, Awaitable, Callable, List, Optional

from autogen_agentchat.agents import AssistantAgent
from autogen_core.models import ChatC

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
from typing import Any, Awaitable, Callable, List, Optional

from autogen_agentchat.agents import AssistantAgent
from autogen_core.models import ChatCompletionClient
from autogen_core.tools import BaseTool
from pydantic import BaseModel

from .tools import (
    extract_audio,
    get_screenshot_at,
    get_video_length,
    save_screenshot,
    transcribe_audio_with_timestamps,
    transcribe_video_screenshot,
)


class VideoSurfer(AssistantAgent):
    """
    VideoSurfer is a specialized agent designed to answer questions about a local video file.

    Installation:

    .. code-block:: bash

        pip install "autogen-ext[video-surfer]"

    This agent utilizes various tools to extract information from the video, such as its length, screenshots at specific timestamps, and audio transcriptions. It processes these elements to provide detailed answers to user queries.

    Available tools:

    - :func:`~autogen_ext.agents.video_surfer.tools.extract_audio`
    - :func:`~autogen_ext.agents.video_surfer.tools.get_video_length`
    - :func:`~autogen_ext.agents.video_surfer.tools.transcribe_audio_with_timestamps`
    - :func:`~autogen_ext.agents.video_surfer.tools.get_screenshot_at`
    - :func:`~autogen_ext.agents.video_surfer.tools.save_screenshot`
    - :func:`~autogen_ext.agents.video_surfer.tools.transcribe_video_screenshot`

    Args:
        name (str): The name of the agent.
        model_client (ChatCompletionClient): The model client used for generating responses.
        tools (List[BaseTool[BaseModel, BaseModel]  | Callable[..., Any] | Callable[..., Awaitable[Any]]] | None, optional):
            A list of tools or functions the agent can use. If not provided, defaults to all video tools from the action space.
        description (str, optional): A brief description of the agent. Defaults to "An agent that can answer questions about a local video.".
        system_message (str | None, optional): The system message guiding the agent's behavior. Defaults to 

*[truncated — see source for full prompt]*