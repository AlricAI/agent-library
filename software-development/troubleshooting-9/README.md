# Troubleshooting

> ## Debug Mode

Pass `--debug` to enable verbose logging:

```bash
npx -y mirroir-mcp --debug
```

Logs are written to both stderr and `~/.mirroir-mcp/

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Troubleshooting

## Debug Mode

Pass `--debug` to enable verbose logging:

```bash
npx -y mirroir-mcp --debug
```

Logs are written to both stderr and `~/.mirroir-mcp/debug.log` (truncated on each startup). Logged events include permission checks, tap coordinates, focus state, and window geometry.

Even without `--debug`, the server always writes startup information to `~/.mirroir-mcp/debug.log` — permission mode, denied tools, and hidden tools. Check this file first when debugging permission issues.

Tail the log in a separate terminal:

```bash
tail -f ~/.mirroir-mcp/debug.log
```

Combine with permission bypass for full-access debugging:

```bash
npx -y mirroir-mcp --debug --yolo
```

## Modifier State Corruption (Alternating Caps)

If you see alternating uppercase/lowercase when typing through iPhone Mirroring (e.g., "LiKe ThIs"), this is a known Apple bug with modifier state tracking in the iPhone Mirroring compositor.

**Workarounds:** Toggle Caps Lock, disconnect and reconnect iPhone Mirroring, or reboot the Mac. See [Apple Community thread](https://discussions.apple.com/thread/254551671).

## Doctor

Run `mirroir doctor` to check all prerequisites at once. Each failed check includes a fix hint:

```bash
mirroir doctor
```

Use `--json` for machine-readable output or `--no-color` to disable ANSI colors.

## Development Watch Mode

During development, use `mirroir-watch.sh` to automatically rebuild and restart the server when source files change:

```bash
./mirroir-watch.sh --debug --dangerously-skip-permissions
```

The script uses `fswatch` to monitor `Sources/` for `.swift` file changes, rebuilds via `swift build`, and restarts the server process. Install fswatch with `brew install fswatch` if needed. The MCP client will need to reconnect after each restart.

## Common Issues

**Typing goes to the wrong app instead of iPhone** — The MCP server activates iPhone Mirroring via AppleScript before every input call. If keystrokes still land in the wrong app, ch

*[truncated — see source for full prompt]*