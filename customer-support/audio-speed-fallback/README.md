# AUDIO SPEED FALLBACK

> ## Overview

The Cloudflare Workers AI TTS API for `@cf/deepgram/aura-2-en` officially supports the following parameters:
- `text` (required)
- `speak

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Audio Speed Adjustment Fallback

## Overview

The Cloudflare Workers AI TTS API for `@cf/deepgram/aura-2-en` officially supports the following parameters:
- `text` (required)
- `speaker`
- `encoding`
- `container`
- `sample_rate`
- `bit_rate`

**Note:** The `speed` parameter is **NOT** officially supported in the Cloudflare Workers AI schema, though it is supported by Deepgram's native API. If Cloudflare's API gateway rejects requests with the `speed` parameter (HTTP 400 with schema validation errors), you'll need to use the fallback script to adjust audio speed post-download.

## Fallback Script Usage

The `scripts/speed_audio.py` script provides a fallback mechanism to adjust audio playback speed using local utilities.

### Prerequisites

Install either `sox` (preferred) or `ffmpeg`:

```bash
# Option 1: sox (preferred - better quality for speech)
sudo apt-get install sox libsox-fmt-all

# Option 2: ffmpeg (alternative)
sudo apt-get install ffmpeg
```

### Command Line Usage

```bash
# Basic usage
python3 scripts/speed_audio.py <input.mp3> <output.mp3> <speed>

# Example: Speed up audio by 30% (1.3x)
python3 scripts/speed_audio.py /tmp/task_1.mp3 /tmp/task_1_fast.mp3 1.3

# Example: Speed up audio by 20% (1.2x)
python3 scripts/speed_audio.py /tmp/motivation.mp3 /tmp/motivation_fast.mp3 1.2
```

### Programmatic Usage

If you need to modify the code to use the fallback script instead of passing `speed` to the API:

```python
from scripts.speed_audio import adjust_audio_speed

# In ai/speech.py, modify generate_voice():
def generate_voice(
    text: str,
    output_path: str = "output.mp3",
    speaker: str = "luna",
    speed: float = 1.0
) -> Optional[str]:
    try:
        safe_output_path = sanitize_output_path(output_path)
        config = get_config()

        # ... existing code ...

        # Remove 'speed' from payload if Cloudflare rejects it
        payload = {
            "text": text,
            "speaker": speaker
            # "speed": speed  # REMO

*[truncated — see source for full prompt]*