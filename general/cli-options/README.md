# Cli Options

> CycoD provides a variety of command line options to customize its behavior.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Command Line Options

CycoD provides a variety of command line options to customize its behavior. This document provides a comprehensive overview of all available options.

## Basic Usage

```
cycod [options]
```

## Commands

CycoD supports the following commands:

| Command | Description |
|---------|-------------|
| `chat` | Start a chat session (default) |
| `config` | Manage configuration settings |
| `github login` | Authenticate with GitHub Copilot |
| `alias list` | List all available aliases |
| `alias get <name>` | View the content of a specific alias |
| `alias add <name> <content>` | Add a new raw alias without syntax validation |
| `alias delete <name>` | Delete an alias |
| `version` | Display version information |
| `help` | Display help information |

## Global Options

These options apply to the overall behavior of CycoD:

| Option | Description |
|--------|-------------|
| `--debug` | Enable debug output |
| `--verbose` | Enable verbose output |
| `--quiet` | Suppress non-essential output |
| `--interactive <true/false>` | Control whether to enter interactive mode (default: true) |
| `--no-templates` | Disable template processing in input |
| `--save-alias <n>` | Save the current command options as a named alias in the local scope |
| `--save-local-alias <n>` | Same as `--save-alias`, saves in the local scope |
| `--save-user-alias <n>` | Save the current command options as a named alias in the user scope |
| `--save-global-alias <n>` | Save the current command options as a named alias in the global scope |
| `--help` | Display help information |

## Chat Options

These options control the chat interaction:

| Option | Description |
|--------|-------------|
| `--system-prompt <prompt>` | Set a custom system prompt for the AI |
| `--add-system-prompt <text>` | Add text to the system prompt (can be used multiple times) |
| `--add-user-prompt <text>` | Add a user prompt that gets inserted when chat history is cleared (can be used multiple times) |
|

*[truncated — see source for full prompt]*