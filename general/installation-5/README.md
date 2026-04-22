# Installation

> ## Prerequisites

Before installing videogen, ensure all dependencies are running on your homelab.

### 1. GPU Gateway

The GPU Gateway must be runnin

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Installation

## Prerequisites

Before installing videogen, ensure all dependencies are running on your homelab.

### 1. GPU Gateway

The GPU Gateway must be running with TTS, STT, and LLM endpoints.

```bash
# Check health
curl http://localhost:8090/health

# Verify endpoints
curl http://localhost:8090/v1/audio/voices
```

See [Dependencies](dependencies.md) for setup details.

### 2. ComfyUI + SDXL Checkpoint

```bash
# ComfyUI should be installed at ~/ComfyUI/
ls ~/ComfyUI/main.py

# SDXL checkpoint must be present
ls ~/ComfyUI/models/checkpoints/sd_xl_base_1.0.safetensors

# If missing, download it:
huggingface-cli download stabilityai/stable-diffusion-xl-base-1.0 \
  sd_xl_base_1.0.safetensors \
  --local-dir ~/ComfyUI/models/checkpoints/ \
  --local-dir-use-symlinks False
```

### 3. FFmpeg

```bash
# Must support libx264 and libass
ffmpeg -version | head -1
ffmpeg -filters 2>/dev/null | grep -E "zoompan|ass"
```

### 4. Montserrat Font (for subtitles)

```bash
# Install Montserrat for ASS subtitle rendering
sudo apt install fonts-montserrat
# Or download from Google Fonts
```

## Install Videogen

```bash
cd ~/projects/videogen

# Create venv and install
uv sync

# Verify
videogen --help
videogen voices
```

## Configuration

Copy the example env file and adjust:

```bash
cp .env.example .env
```

| Variable | Default | Description |
|----------|---------|-------------|
| `GPU_GATEWAY_URL` | `http://localhost:8090` | GPU Gateway base URL |
| `COMFYUI_URL` | `http://localhost:8188` | ComfyUI API URL |
| `DEFAULT_LANGUAGE` | `fr` | Default narration language |
| `DEFAULT_VOICE` | `eric` | Default TTS voice |
| `DEFAULT_MODEL` | `qwen3.5-9b` | Default LLM model |
| `COMFYUI_CHECKPOINT` | `sd_xl_base_1.0.safetensors` | SDXL checkpoint name |