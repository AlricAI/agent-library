# Usage

> ## Generate a Video from a Topic

```bash
videogen generate --topic "5 faits incroyables sur les octopus" --lang fr --voice eric
```

This runs the fu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Usage

## Generate a Video from a Topic

```bash
videogen generate --topic "5 faits incroyables sur les octopus" --lang fr --voice eric
```

This runs the full pipeline:

1. **LLM** generates a scene-by-scene script
2. **ComfyUI** generates portrait images for each scene
3. **TTS** creates narration audio for each scene
4. **STT** extracts word-level timestamps
5. **FFmpeg** assembles everything with Ken Burns effects and karaoke subtitles

Output: `output/<title>.mp4`

## Use Existing Images

Skip ComfyUI and provide your own images:

```bash
videogen generate \
  --topic "les bienfaits du cafe" \
  --images-dir ./my-images/ \
  --lang fr \
  --voice serena
```

Images are matched to scenes in filename order (alphabetical).

## Use a Pre-written Script

Create a JSON script file:

```json
{
  "title": "Les Octopus",
  "scenes": [
    {
      "scene_id": 1,
      "narration": "Saviez-vous que les pieuvres ont trois coeurs?",
      "image_prompt": "closeup octopus underwater, bioluminescent, portrait orientation",
      "duration_hint": 5.0,
      "visual_style": "ken_burns_zoom_in"
    },
    {
      "scene_id": 2,
      "narration": "Leur sang est bleu car il contient du cuivre.",
      "image_prompt": "blue copper blood cells, microscope view, dark background",
      "duration_hint": 4.0,
      "visual_style": "ken_burns_pan_right"
    }
  ]
}
```

Then:

```bash
videogen generate --script script.json --lang fr --voice aiden
```

## List Available Voices

```bash
videogen voices
```

Available voices: `ono_anna`, `serena`, `vivian`, `aiden`, `dylan`, `eric`, `ryan`, `sohee`, `uncle_fu`

## CLI Reference

```
videogen generate [OPTIONS]

Options:
  -t, --topic TEXT        Video topic (used for LLM script generation)
  -s, --script PATH       Pre-written script JSON file
  -i, --images-dir PATH   Directory with images (skip ComfyUI)
  -l, --lang TEXT          Language: fr, en (default: fr)
  -v, --voice TEXT         TTS voice (default: eric)
  -o, --output TEXT   

*[truncated — see source for full prompt]*