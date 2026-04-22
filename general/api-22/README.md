# Api

> ## CLI Commands

### `videogen generate`

Generate a short video from a topic or script.

```bash
videogen generate [OPTIONS]
```

| Option | Type | D

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Reference

## CLI Commands

### `videogen generate`

Generate a short video from a topic or script.

```bash
videogen generate [OPTIONS]
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--topic`, `-t` | TEXT | *required* | Video topic (or use --script) |
| `--script`, `-s` | PATH | - | Pre-written script JSON file |
| `--images-dir`, `-i` | PATH | - | Use existing images (skip ComfyUI) |
| `--lang`, `-l` | TEXT | `fr` | Narration language (`fr`, `en`) |
| `--voice`, `-v` | TEXT | `eric` | TTS voice name |
| `--output`, `-o` | TEXT | `output` | Output directory |

### `videogen voices`

List available TTS voices from the GPU Gateway.

## Data Models

### Script JSON Format

```json
{
  "title": "Video Title",
  "scenes": [
    {
      "scene_id": 1,
      "narration": "Voiceover text for this scene",
      "image_prompt": "SDXL prompt describing the visual",
      "duration_hint": 5.0,
      "visual_style": "ken_burns_zoom_in"
    }
  ]
}
```

### Scene Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `scene_id` | int | yes | Unique scene number (1-based) |
| `narration` | string | yes | Text spoken by TTS |
| `image_prompt` | string | yes | SDXL image generation prompt |
| `duration_hint` | float | no | Suggested duration in seconds (default: 5.0) |
| `visual_style` | string | no | Ken Burns effect (default: `ken_burns_zoom_in`) |

### Visual Styles

- `ken_burns_zoom_in` — Slow zoom into center
- `ken_burns_zoom_out` — Slow zoom out from center
- `ken_burns_pan_left` — Horizontal pan left
- `ken_burns_pan_right` — Horizontal pan right

## GPU Gateway Endpoints Used

### POST `/v1/chat/completions`

OpenAI-compatible chat completion for script generation.

### POST `/v1/audio/speech`

OpenAI-compatible TTS. Returns WAV audio.

```bash
curl -X POST http://localhost:8090/v1/audio/speech \
  -H "Content-Type: application/json" \
  -d '{"input": "Bonjour!", "voice": "eric", "la

*[truncated — see source for full prompt]*