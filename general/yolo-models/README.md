# Yolo Models

> Text-only OCR misses non-text UI elements — buttons, toggles, tab bar icons, activity rings.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# YOLO Icon Detection

Text-only OCR misses non-text UI elements — buttons, toggles, tab bar icons, activity rings. mirroir-mcp integrates YOLO CoreML models to detect these elements and merge them with Vision OCR results.

## Recommended Model: OmniParser v2.0

We recommend [Microsoft OmniParser v2.0](https://huggingface.co/microsoft/OmniParser-v2.0), a YOLOv8 model trained on UI screenshots to detect interactive elements. It outputs a single `icon` class with bounding boxes for clickable regions.

### Install via Hugging Face

```bash
pip install huggingface_hub
huggingface-cli download microsoft/OmniParser-v2.0 \
  --include "icon_detect/*" \
  --local-dir ~/.mirroir-mcp/models/icon_detect_download
```

### Convert to CoreML

Use [coremltools](https://github.com/apple/coremltools) to convert the PyTorch weights, or [Ultralytics](https://docs.ultralytics.com/modes/export/) which has built-in CoreML export:

```bash
pip install ultralytics coremltools
```

```python
from ultralytics import YOLO

model = YOLO("~/.mirroir-mcp/models/icon_detect_download/icon_detect/model.pt")
model.export(format="coreml", imgsz=640)
```

This produces a `.mlpackage`. Compile it to `.mlmodelc`:

```bash
xcrun coremlcompiler compile model.mlpackage ~/.mirroir-mcp/models/icon_detect.mlmodelc
```

### Verify

Restart mirroir-mcp and check the debug log:

```bash
grep "YOLO" ~/.mirroir-mcp/debug.log
# Should show: OCR: auto-detected YOLO model, using Vision + YOLO
```

Or run `mirroir doctor` — it reports whether a YOLO model is loaded.

## Configuration

```json
// .mirroir-mcp/settings.json
{
  "ocrBackend": "auto",
  "yoloConfidenceThreshold": 0.3
}
```

| Setting | Default | Description |
|---------|---------|-------------|
| `ocrBackend` | `"auto"` | `"auto"` merges Vision + YOLO when a model is present. `"yolo"` for icons only, `"both"` to always merge |
| `yoloModelURL` | `""` | URL to download a `.mlmodel` on first use (auto-compiles) |
| `yoloModelPath` | `""` | Local path to a p

*[truncated — see source for full prompt]*