# Tools

> import base64
from typing import Any, Dict, List, Tuple

import cv2
import ffmpeg
import numpy as np
import whisper
from autogen_core import Image as 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
import base64
from typing import Any, Dict, List, Tuple

import cv2
import ffmpeg
import numpy as np
import whisper
from autogen_core import Image as AGImage
from autogen_core.models import (
    ChatCompletionClient,
    UserMessage,
)


def extract_audio(video_path: str, audio_output_path: str) -> str:
    """
    Extracts audio from a video file and saves it as an MP3 file.

    :param video_path: Path to the video file (must be a local file path, not a URL).
    :param audio_output_path: Path to save the extracted audio file (must end with .mp3).
    :return: Confirmation message with the path to the saved audio file.
    """
    import os
    import re

    # Reject URLs to prevent SSRF via ffmpeg
    if re.match(r"^[a-zA-Z][a-zA-Z0-9+\-.]*://", video_path):
        raise ValueError("video_path must be a local file path, not a URL.")

    # Enforce .mp3 extension to prevent writing arbitrary file types
    if not audio_output_path.lower().endswith(".mp3"):
        raise ValueError("audio_output_path must end with .mp3.")

    # Prevent path traversal — output must stay within the current working directory
    cwd = os.path.realpath(os.getcwd())
    output_real = os.path.realpath(audio_output_path)
    if not output_real.startswith(cwd + os.sep) and output_real != cwd:
        raise ValueError("audio_output_path must be within the current working directory.")

    (ffmpeg.input(video_path).output(audio_output_path, format="mp3").run(quiet=True, overwrite_output=True))  # type: ignore
    return f"Audio extracted and saved to {audio_output_path}."


def transcribe_audio_with_timestamps(audio_path: str) -> str:
    """
    Transcribes the audio file with timestamps using the Whisper model.

    :param audio_path: Path to the audio file.
    :return: Transcription with timestamps.
    """
    model = whisper.load_model("base")  # type: ignore
    result: Dict[str, Any] = model.transcribe(audio_path, task="transcribe", language="en", verbose=False)  # type: ignore



*[truncated — see source for full prompt]*