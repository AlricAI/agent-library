# Dependencies

> Videogen orchestrates several external services.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Dependencies

Videogen orchestrates several external services. All run locally on the homelab.

## System Requirements

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| GPU | NVIDIA with 8GB VRAM | RTX 3070 or better |
| CUDA | 12.x+ | 13.1 |
| RAM | 16GB | 32GB |
| Disk | 20GB free | 50GB free (models + output) |
| OS | Linux (Ubuntu 22.04+) | Linux Mint / Ubuntu |

## Python Dependencies

Installed via `uv sync` from `pyproject.toml`:

| Package | Version | Purpose |
|---------|---------|---------|
| `httpx` | >=0.27 | Async HTTP client for GPU Gateway + ComfyUI APIs |
| `pydantic` | >=2.0 | Data models (Scene, Script, WordTimestamp) |
| `pydantic-settings` | >=2.0 | Environment variable configuration |
| `typer` | >=0.12 | CLI framework |
| `rich` | >=13.0 | Terminal progress bars and formatting |
| `websockets` | >=13.0 | ComfyUI WebSocket communication |

### Dev dependencies

| Package | Purpose |
|---------|---------|
| `ruff` | Linting + formatting |
| `mypy` | Type checking |
| `pytest` | Unit tests |

## External Services

### GPU Gateway

**Repository**: Local service at `~/projects/gpu-gateway/`
**Service**: `systemctl --user status gpu-gateway`
**URL**: `http://localhost:8090`

Provides three models via FastAPI:

| Model | Type | VRAM | Endpoint |
|-------|------|------|----------|
| Qwen3.5-9b | LLM | ~7.7GB | `POST /v1/chat/completions` |
| Qwen3-TTS 1.7B | TTS | ~1.7GB | `POST /v1/audio/speech` |
| Faster-Whisper Medium | STT | ~1.5GB | `POST /v1/audio/transcriptions` |

Models are loaded on-demand and auto-unloaded after 5 minutes idle.

**Setup**:
```bash
cd ~/projects/gpu-gateway
systemctl --user enable gpu-gateway
systemctl --user start gpu-gateway
```

### ComfyUI

**Location**: `~/ComfyUI/`
**URL**: `http://localhost:8188` (started by videogen on demand)

Image generation via Stable Diffusion XL.

**Required checkpoint**:

| File | Size | Location |
|------|------|----------|
| `sd_xl_base_1.0.safetensors` | 6.5GB

*[truncated — see source for full prompt]*