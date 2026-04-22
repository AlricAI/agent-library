# Faq

> ## Is this safe? Can the AI access my banking apps?

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# FAQ

## Is this safe? Can the AI access my banking apps?

This tool gives an AI agent full control of your iPhone screen — it can tap anything, type anything, and open any app. That includes banking apps, messages, and payments.

To limit exposure:

- **Fail-closed permissions**: Without a config file, only read-only tools (screenshot, describe_screen, status) are exposed. Mutating tools are hidden entirely.
- **`blockedApps`**: Add sensitive apps to the deny list in `~/.mirroir-mcp/permissions.json`:
  ```json
  { "allow": ["tap", "swipe", "type_text"], "blockedApps": ["Wallet", "Banking"] }
  ```
- **Kill switch**: Closing the iPhone Mirroring window or locking the phone kills all input immediately. No persistent background access is possible.

See [Security](security.md) for the full threat model and recommendations.

## Why does my cursor jump when the AI is working?

Every input tool (`tap`, `type_text`, `swipe`, etc.) must make iPhone Mirroring the frontmost app before sending input. macOS routes CGEvent input to the frontmost application — there is no API to direct input to a background window.

**Mitigations:**

- **Separate macOS Space** — Put iPhone Mirroring in its own Space. Your cursor position and text selection in the other Space are preserved.
- **Batch interactions** — Run a sequence of phone commands together rather than interleaving with terminal work.
- **Skills** — Chain multiple steps in a skill (SKILL.md or YAML). Focus is acquired once rather than per-tool-call.

Read-only tools (`screenshot`, `describe_screen`, `start_recording`, `stop_recording`, `status`, `get_orientation`, `check_health`, `list_skills`, `get_skill`, `list_targets`, `calibrate_component`) do **not** steal focus.

See [Known Limitations](limitations.md#focus-stealing) for details.

## Does it work with any iPhone app?

Yes. The MCP server operates at the screen level through macOS iPhone Mirroring — it taps, swipes, and types as if a human were interacting with the phone.

*[truncated — see source for full prompt]*