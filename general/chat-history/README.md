# Chat History

> CycoD provides functionality to save and load chat histories, allowing you to maintain context across sessions and refer back to previous conversations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Chat History

CycoD provides functionality to save and load chat histories, allowing you to maintain context across sessions and refer back to previous conversations. It also supports saving conversations in a human-readable trajectory format.

## Understanding Chat History Files

Chat histories in CycoD are stored in JSONL (JSON Lines) format, where each line contains a JSON object representing a message in the conversation. This format makes it easy to append new messages to the history file and to parse individual messages without loading the entire file.

## Saving Chat History

### Automatic Saving

By default, CycoD automatically saves your chat history and trajectory files to the `history` directory under your user profile:

- Windows: `%USERPROFILE%\.cycod\history\`
- Mac/Linux: `~/.cycod/history/`

Files are saved with default names in the format:
- Chat history: `chat-history-{time}.jsonl`
- Trajectory: `trajectory-{time}.jsonl`

You can disable this feature using the config commands:

```bash
cycod config set App.AutoSaveChatHistory false
cycod config set App.AutoSaveTrajectory false
```

To re-enable automatic saving:

```bash
cycod config set App.AutoSaveChatHistory true
cycod config set App.AutoSaveTrajectory true
```

### Manual Saving with CLI Options

You can also explicitly specify where to save your chat history using the `--output-chat-history` option:

```bash
cycod --output-chat-history "my-project-chat.jsonl"
```

If no filename is specified, CycoD uses a default template: `chat-history-{time}.jsonl`, where `{time}` is replaced with the current date and time.

When you explicitly provide an output path with the CLI option, it takes precedence over the automatic saving setting.

### Filename Templates

You can use the following placeholders in your output filename:

- `{fileName}` or `{filename}`: Full file name
- `{filePath}` or `{filepath}`: Directory path
- `{fileBase}` or `{filebase}`: File name without extension
- `{fileExt}` or `{fileex

*[truncated — see source for full prompt]*