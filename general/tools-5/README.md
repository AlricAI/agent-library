# Tools

> All 32 tools exposed by the MCP server.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tools Reference

All 32 tools exposed by the MCP server. Mutating tools require [permission](permissions.md) to appear in `tools/list`.

## Tool List

| Tool | Parameters | Description |
|------|-----------|-------------|
| `screenshot` | — | Capture the iPhone screen as base64 PNG |
| `describe_screen` | `scroll`?, `omit_screenshot`? | Analyze the screen and return UI elements with tap coordinates plus a grid-overlaid screenshot. Uses local OCR or AI vision depending on `screenDescriberMode`. `scroll: true` does a full-page scroll to capture all elements. `omit_screenshot: true` returns text only (no image). |
| `start_recording` | `output_path`? | Start video recording of the mirrored screen |
| `stop_recording` | — | Stop recording and return the .mov file path |
| `tap` | `x`, `y`, `cursor_mode`? | Tap at coordinates (relative to mirroring window) |
| `double_tap` | `x`, `y`, `cursor_mode`? | Two rapid taps for zoom/text selection |
| `long_press` | `x`, `y`, `duration_ms`?, `cursor_mode`? | Hold tap for context menus (default 500ms) |
| `swipe` | `from_x`, `from_y`, `to_x`, `to_y`, `duration_ms`?, `cursor_mode`? | Swipe between two points (default 300ms) |
| `drag` | `from_x`, `from_y`, `to_x`, `to_y`, `duration_ms`?, `cursor_mode`? | Slow sustained drag for icons, sliders (default 1000ms) |
| `type_text` | `text` | Type text — activates iPhone Mirroring and sends keystrokes |
| `press_key` | `key`, `modifiers`? | Send a special key (return, escape, tab, delete, space, arrows) with optional modifiers (command, shift, option, control) |
| `shake` | — | Trigger shake gesture (Ctrl+Cmd+Z) for undo/dev menus |
| `launch_app` | `name` | Open app by name via Spotlight search |
| `open_url` | `url` | Open URL in Safari |
| `press_home` | — | Go to home screen |
| `press_app_switcher` | — | Open app switcher |
| `spotlight` | — | Open Spotlight search |
| `scroll_to` | `label`, `direction`?, `max_scrolls`? | Scroll until a text element becomes visible via OCR |
| `re

*[truncated — see source for full prompt]*