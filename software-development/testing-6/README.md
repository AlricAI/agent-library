# Testing

> How iPhone Mirroir MCP achieves reliable CI testing without a physical iPhone.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing

How iPhone Mirroir MCP achieves reliable CI testing without a physical iPhone.

## The Problem

iPhone Mirroir MCP controls a real iPhone through macOS iPhone Mirroring — an app that streams the iPhone display and forwards touch/keyboard input over AirPlay + Bluetooth LE. Every core feature (screenshots, OCR, tap, swipe, menu traversal) depends on a live mirroring session with a physical device.

CI runners have no iPhones. Testing the install-and-run path without hardware requires a different approach.

## The Solution: FakeMirroring

`FakeMirroring` is a lightweight macOS app that stands in for iPhone Mirroring during CI. It provides the same macOS API surface the MCP server depends on:

| API Surface | iPhone Mirroring | FakeMirroring |
|-------------|-----------------|---------------|
| `NSWorkspace.runningApplications` (process discovery) | `com.apple.ScreenContinuity` | `com.jfarcand.FakeMirroring` |
| `AXUIElement` main window | 410×898pt mirrored display | 410×898pt NSWindow |
| `CGWindowListCopyWindowInfo` (window ID) | Continuity compositor window | Standard NSWindow |
| `screencapture -l <windowID>` | iPhone screen pixels | Dark background with text labels |
| Vision OCR (`VNRecognizeTextRequest`) | Real iOS UI text | Rendered labels: "Settings", "Safari", "9:41", etc. |
| AX menu bar traversal | View > Home Screen, Spotlight, App Switcher | View > Home Screen, Spotlight, App Switcher |

FakeMirroring is **not a mock** — it is a real macOS app exercising real macOS APIs. The MCP server calls the same `AXUIElement`, `CGWindowList`, `screencapture`, and Vision APIs it would use against iPhone Mirroring. The only difference is which process those APIs target.

### How Targeting Works

The MCP server discovers the mirroring app by bundle ID and process name. Two environment variables control this:

```
MIRROIR_BUNDLE_ID=com.jfarcand.FakeMirroring
MIRROIR_PROCESS_NAME=FakeMirroring
```

When unset, they default to `com.apple.ScreenContinuity` and `i

*[truncated — see source for full prompt]*