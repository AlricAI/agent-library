# TODO Meta Debugging Self Analysis Techniques

> ## Log File Analysis and Self-Debugging Techniques

### Finding Your Current Session Log
When you need to debug or analyze your own function calls:

1

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TODO: Meta-Debugging and Self-Analysis Instructions for AGENTS.md

## Log File Analysis and Self-Debugging Techniques

### Finding Your Current Session Log
When you need to debug or analyze your own function calls:

1. **Identify your current log file**: Look for the most recent `log-cycod-*.log` file in the current directory
2. **Verify it's yours**: Search the log for text from your current conversation to confirm it's your active session
3. **Use recursive verification**: You can grep your own log file for the commands you're currently running
4. **Expect rapid growth**: Even short sessions can generate large log files (1MB+) due to verbose logging
5. **Understand session types**: Determine if you're in a fresh session or continuing from loaded chat history

### Chat History and Session Continuity
- **Chat history location**: Stored in `C:\Users\{user}\.cycod\history\chat-history-{timestamp}.jsonl`
- **Current logs**: Stored in current working directory as `log-cycod-{timestamp}.log`
- **Meta-debugging**: You can examine your own previous function calls by viewing the chat history that was loaded into your current session
- **Log file growth**: Logs grow very rapidly (can reach 1MB+ quickly) due to detailed API request/response logging, function call traces, and verbose internal logging
- **New session = new log**: Each restart creates a fresh log file with a new timestamp, even if continuing from chat history
- **Session continuity vs. fresh start**: Distinguish between loading previous chat history (session continuation) vs. truly fresh restart

### Function Call Testing and Validation Techniques

#### Before Writing Tests
1. **Test functions manually first**: Use the actual functions to understand their real behavior
2. **Document unexpected behavior**: Log discrepancies between expected and actual function outputs
3. **Don't trust documentation alone**: Always verify function behavior through direct experimentation

#### Test Design Principles
1. **Prevent 

*[truncated — see source for full prompt]*