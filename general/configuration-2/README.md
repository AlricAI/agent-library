# Configuration

> All settings live in `settings.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Configuration

All settings live in `settings.json` — project-local (`.mirroir-mcp/settings.json`) or global (`~/.mirroir-mcp/settings.json`). Project-local settings override global ones.

```json
{
  "screenDescriberMode": "auto",
  "agent": "embacle",
  "visionImageWidth": 500,
  "ocrBackend": "auto",
  "keystrokeDelayUs": 20000,
  "clickHoldUs": 100000
}
```

Every setting has a corresponding environment variable (e.g. `MIRROIR_SCREEN_DESCRIBER_MODE`, `MIRROIR_KEYSTROKE_DELAY_US`). Resolution order: project-local `settings.json` → global `settings.json` → environment variable → built-in default.

## Screen Intelligence

| Setting | Default | Description |
|---------|---------|-------------|
| `screenDescriberMode` | `"auto"` | `"auto"` uses vision when embacle FFI is linked, OCR otherwise. `"vision"` forces AI vision, `"ocr"` forces local OCR + YOLO |
| `agent` | `""` | AI agent name for vision mode and diagnosis (e.g. `"embacle"`, `"embacle:claude"`) |
| `agentTransport` | `"auto"` | Agent transport: `"auto"` uses embedded Rust FFI if linked, HTTP otherwise. `"http"` forces HTTP |
| `visionImageWidth` | `500` | Target image width in pixels for vision API calls (screenshots are resized before sending) |
| `ocrBackend` | `"auto"` | OCR backend: `"auto"`, `"vision"` (text only), `"yolo"` (icons only), or `"both"` |
| `ocrRecognitionLevel` | `"accurate"` | Apple Vision OCR quality: `"accurate"` or `"fast"` |
| `ocrLanguageCorrection` | `true` | Enable language correction during OCR text recognition |
| `ocrLanguages` | `["en-US"]` | BCP-47 language codes for `VNRecognizeTextRequest.recognitionLanguages`. Add languages to recognise non-Latin scripts (e.g. `["ja-JP","en-US"]`). Also configurable via `MIRROIR_OCR_LANGUAGES` env var (comma-separated) |
| `describeScreenOmitScreenshot` | `false` | Omit the screenshot image from `describe_screen` responses to save context window space in long automation sessions |
| `yoloModelURL` | `""` | URL to download a YOLO `.mlmod

*[truncated — see source for full prompt]*