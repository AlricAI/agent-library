# HOOKS COMPARISON

> **Last Updated**: 2026-01-16 **Testing**: Both platforms tested in production
**Sources**: Official documentation + empirical testing

## Hook Types C

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Claude Code Hooks vs GitHub Copilot CLI Hooks - Complete Comparison

**Last Updated**: 2026-01-16 **Testing**: Both platforms tested in production
**Sources**: Official documentation + empirical testing

## Hook Types Comparison

| Hook Type         | Claude Code          | Copilot CLI            | Notes                           |
| ----------------- | -------------------- | ---------------------- | ------------------------------- |
| **Session Start** | ✅ SessionStart      | ✅ sessionStart        | Both fire at session begin      |
| **Session End**   | ✅ Stop              | ✅ sessionEnd          | Both fire at session end        |
| **Subagent End**  | ✅ SubagentStop      | ❌ Not available       | Claude Code only                |
| **User Prompt**   | ✅ UserPromptSubmit  | ✅ userPromptSubmitted | Both fire on prompt submit      |
| **Pre-Tool**      | ✅ PreToolUse        | ✅ preToolUse          | Both fire before tool execution |
| **Post-Tool**     | ✅ PostToolUse       | ✅ postToolUse         | Both fire after tool execution  |
| **Permission**    | ✅ PermissionRequest | ❌ Not available       | Claude Code only                |
| **Error**         | ❌ Not available     | ✅ errorOccurred       | Copilot CLI only                |
| **Notification**  | ✅ Notification      | ❌ Not available       | Claude Code only                |
| **Pre-Compact**   | ✅ PreCompact        | ❌ Not available       | Claude Code only                |
| **TOTAL**         | 10 hooks             | 6 hooks                | Claude Code more comprehensive  |

---

## Capabilities Comparison

### Context Injection (Adding Information to AI)

| Hook                 | Claude Code                            | Copilot CLI                      | Tested                |
| -------------------- | -------------------------------------- | -------------------------------- | --------------------- |
| **SessionStart**     | ✅ YES - `additionalContext` or stdout | ❌ NO - Output ignored           | ✅ C

*[truncated — see source for full prompt]*