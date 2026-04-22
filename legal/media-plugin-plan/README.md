# MEDIA PLUGIN PLAN

> ## Problem
OpenClaw agents generate images and audio (TTS). These files land on disk at `~/.openclaw/media/`. WebSocket clients (Discord, WhatsApp, Te

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Claudio Media Plugin Plan

## Problem
OpenClaw agents generate images and audio (TTS). These files land on disk at `~/.openclaw/media/`. WebSocket clients (Discord, WhatsApp, Telegram) get media delivered through channel-specific delivery pipelines. But HTTP/WS direct clients like Claudio get only `MEDIA:/tmp/openclaw/tts-xxx/voice.mp3` text — no actual file delivery.

## Solution: `claudio-media` OpenClaw Plugin

A proper OpenClaw plugin (not a gateway patch). Survives `npm update openclaw`.

### Piece 1: HTTP Route — serve media files

Use `api.registerHttpRoute` to add a `/media/*` endpoint to the gateway.

```
GET /media/{relative-path}
Authorization: Bearer {gateway-token}
```

- Maps `/media/foo.jpg` → `~/.openclaw/media/foo.jpg`
- Streams file back with correct `Content-Type` (image/png, audio/mpeg, etc.)
- Auth: `"gateway"` — requires the same bearer token as chat completions
- Match: `"prefix"` — catches all paths under `/media/`

### Piece 2: `message_sending` hook — rewrite MEDIA: paths

Use `api.on("message_sending", ...)` to intercept outbound messages before delivery.

- Scan `event.content` for `MEDIA:/path/to/file` patterns
- Replace with `https://{publicUrl}/media/{relative-path}`
- Return `{ content: transformedContent }`

### Plugin Config

```json
{
  "id": "claudio-media",
  "configSchema": {
    "publicUrl": {
      "type": "string",
      "description": "Public HTTPS URL for the gateway (e.g. https://theaf-web.ngrok.io)"
    }
  }
}
```

The `publicUrl` is needed so the plugin knows what URL prefix to use when rewriting paths. For our setup: `https://theaf-web.ngrok.io`.

### File Structure

```
~/.openclaw/plugins/claudio-media/
  openclaw.plugin.json    # manifest with id + configSchema
  index.ts                # plugin entry point
```

### What Claudio Needs (client-side)

Nothing new. The rewritten URLs are standard HTTPS links. Claudio already handles image URLs. For audio, it fetches the mp3 URL and plays with AVAudioPlayer.

### Hook

*[truncated — see source for full prompt]*