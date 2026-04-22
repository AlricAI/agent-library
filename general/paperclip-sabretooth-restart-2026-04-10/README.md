# PAPERCLIP SABRETOOTH RESTART 2026 04 10

> Date: April 10, 2026
Authority: Joshua Coleman
Scope: Sabretooth local restart behavior for the isolated `E:` PaperClip lane

## Current Target

- Pub

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# PAPERCLIP SABRETOOTH RESTART STATE

Date: April 10, 2026
Authority: Joshua Coleman
Scope: Sabretooth local restart behavior for the isolated `E:` PaperClip lane

## Current Target

- Public PaperClip URL: `https://paperclip.youandinotai.com`
- Local PaperClip home: `E:\trollz-sandbox\paperclip-antigravity`
- Local PaperClip runtime source: `E:\trollz-sandbox\dao-patches`
- Local API health: `http://127.0.0.1:3100/api/health`
- Public auth origin: `https://paperclip.youandinotai.com`

## Current User-Level Restart Path

Configured under `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`:

- `PaperclipServer`
  - `pwsh -WindowStyle Hidden -Command "& 'E:\trollz-sandbox\paperclip-antigravity\scripts\run-paperclip-antigravity.ps1'"`
- `PaperclipTunnel`
  - `"C:\cloudflared\cloudflared.exe" --config "C:\Users\joshl\.cloudflared\paperclip-direct.yml" tunnel run`

These are the intended user-level restart entries for Sabretooth.

## Startup Folder Cleanup

The following prior user startup items were removed from the live Startup folder and moved to:

- `C:\Users\joshl\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\disabled-2026-04-10`

Moved items:

- `antigravity-mcp-autostart.bat`
- `OpenClaw Gateway.cmd`
- `start-brain-mcp.bat`
- `START-DAO.bat`
- `start-tunnel-on-logon.cmd`
- `Paperclip.lnk`
- `Ollama.lnk`

Goal: prevent duplicate MCP, OpenClaw, BRAIN, DAO, and Chrome-app launches on Sabretooth logon.

## Tunnel Configuration

Dedicated PaperClip tunnel config:

- `C:\Users\joshl\.cloudflared\paperclip-direct.yml`

Current ingress:

- `paperclip.youandinotai.com` -> `http://127.0.0.1:3100`

This is the clean user-owned PaperClip tunnel path.

## Known Admin-Owned Residuals

These were not fully removable from the current non-elevated session:

- Windows service `Cloudflared` remains auto-start and still points at the old LocalSystem config path
- Windows service `PaperclipAgent` still exists in service config
- Scheduled tasks `OpenClaw_AutoStart`, `

*[truncated — see source for full prompt]*