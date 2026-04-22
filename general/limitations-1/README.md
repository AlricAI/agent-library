# Limitations

> ## Focus Stealing

Every input tool (`tap`, `type_text`, `press_key`, `swipe`, `drag`, `long_press`, `double_tap`) must make iPhone Mirroring the fron

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Known Limitations

## Focus Stealing

Every input tool (`tap`, `type_text`, `press_key`, `swipe`, `drag`, `long_press`, `double_tap`) must make iPhone Mirroring the frontmost app before sending input events. This means the tool will steal keyboard focus from whatever app you are currently using.

### Why

CGEvent input is routed by macOS to the frontmost application. There is no API to direct input events to a background window.

### What This Means in Practice

If you are typing in a terminal or editor and an MCP tool fires, iPhone Mirroring will become frontmost and your terminal loses focus. After the tool completes, iPhone Mirroring retains focus — the server intentionally does not switch back to avoid per-call Space jitter.

Read-only tools (`screenshot`, `describe_screen`, `start_recording`, `stop_recording`, `status`, `get_orientation`, `check_health`, `list_skills`, `get_skill`, `list_targets`, `calibrate_component`) use the Accessibility API and do **not** steal focus.

### Mitigations

| Strategy | How It Helps |
|----------|-------------|
| **Separate macOS Space** | Put iPhone Mirroring in its own Space. The activation triggers a Space switch, so your cursor position and text selection in the other Space are preserved. |
| **Skill runner** | Chain multiple steps in a single skill (SKILL.md or YAML). Focus is acquired once at the start rather than stolen between each individual tool call. |
| **Batch your MCP work** | Run a sequence of phone interactions together, then return to your other work. Interleaving phone commands with terminal typing will cause repeated focus switches. |

### Alternatives That Don't Work

| Approach | Why It Fails |
|----------|-------------|
| Accessibility API actions | AX actions can trigger menu items (Home, App Switcher) but cannot simulate touch input on the mirrored display. |
| Clipboard paste (`Cmd+V`) | iPhone Mirroring does not bridge the Mac clipboard when paste is triggered programmatically. Tested with HID, Apple

*[truncated — see source for full prompt]*