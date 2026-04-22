# Summary

> ## 12 个 Session 回顾

| Session | 主题 | 一句话总结 |
|---------|------|------------|
| [s01](./sessions/s01-the-agent-loop.md) | The Agent Loop | **One loop &

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 总结

## 12 个 Session 回顾

| Session | 主题 | 一句话总结 |
|---------|------|------------|
| [s01](./sessions/s01-the-agent-loop.md) | The Agent Loop | **One loop & Bash is all you need** |
| [s02](./sessions/s02-tool-use.md) | Tool Use | **Adding a tool means adding one handler** |
| [s03](./sessions/s03-todo-write.md) | TodoWrite | **An agent without a plan drifts** |
| [s04](./sessions/s04-subagents.md) | Subagents | **Break big tasks down; each subtask gets a clean context** |
| [s05](./sessions/s05-skills.md) | Skills | **Load knowledge when you need it, not upfront** |
| [s06](./sessions/s06-context-compact.md) | Context Compact | **Context will fill up; you need a way to make room** |
| [s07](./sessions/s07-task-system.md) | Task System | **Break big goals into small tasks, order them, persist to disk** |
| [s08](./sessions/s08-background-tasks.md) | Background Tasks | **Run slow operations in the background; the agent keeps thinking** |
| [s09](./sessions/s09-agent-teams.md) | Agent Teams | **When the task is too big for one, delegate to teammates** |
| [s10](./sessions/s10-team-protocols.md) | Team Protocols | **Teammates need shared communication rules** |
| [s11](./sessions/s11-autonomous-agents.md) | Autonomous Agents | **Teammates scan the board and claim tasks themselves** |
| [s12](./sessions/s12-worktree-isolation.md) | Worktree Isolation | **Each works in its own directory, no interference** |

## 四个阶段

```
Phase 1: THE LOOP                    Phase 2: PLANNING & KNOWLEDGE
==================                   ==============================
s01  The Agent Loop                  s03  TodoWrite
     while + stop_reason                  TodoManager + nag reminder
     |                                    |
     +-> s02  Tool Use                  s04  Subagents
              dispatch map                   fresh messages[]
                                              |
                                         s05  Skills
                                          

*[truncated — see source for full prompt]*