# Function Calling

> One of the most powerful features of CycoD is the ability for the AI assistant to call functions that can interact with your system.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Function Calling

One of the most powerful features of CycoD is the ability for the AI assistant to call functions that can interact with your system. This document explains how function calling works in CycoD and the available functions.

## Available Functions

CycoD provides three main categories of functions that the AI assistant can use:

### Shell Command Functions

These functions allow the AI to execute commands in different shell environments:

| Function | Description |
|----------|-------------|
| `RunBashCommand` | Run commands in a bash shell with persistent session |
| `RunCmdCommand` | Run commands in a cmd shell (Windows) with persistent session |
| `RunPowershellCommand` | Run commands in a PowerShell shell with persistent session |

Key features of shell command functions:

- Each function maintains a persistent session, so state (like environment variables) is maintained across multiple commands
- Sessions are automatically reset if a command times out (default timeout: 60 seconds)
- You can specify a custom timeout in milliseconds for long-running commands
- Error codes are captured and returned with output
- UTF-8 encoding is automatically set where possible

Example usage with timeout:
```
RunBashCommand("find / -name '*.log'", 120000)  // 2 minute timeout
```

### File Operation Functions

These functions allow the AI to interact with the file system:

| Function | Description |
|----------|-------------|
| `ListFiles` | List files and directories in a specified path (up to 2 levels deep) |
| `ViewFile` | View the contents of a file, optionally with line numbers and line range |
| `CreateFile` | Create a new file with specified content |
| `ReplaceOneInFile` | Replace text in a file (only replaces unique occurrences) |
| `Insert` | Insert text at a specific line in a file |
| `UndoEdit` | Revert the last edit made to a file |

Key features of file operation functions:

- `ViewFile` supports viewing specific line ranges and adding line number

*[truncated — see source for full prompt]*