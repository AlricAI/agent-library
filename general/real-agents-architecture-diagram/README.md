# Real Agents Architecture Diagram

> ## System Overview

```
┌──────────────────────────────────────────────────────────────────┐
│                          MECHAWIKI UI                  

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Real Agents Architecture Diagram

## System Overview

```
┌──────────────────────────────────────────────────────────────────┐
│                          MECHAWIKI UI                            │
│  ┌────────────────┐              ┌──────────────────────┐       │
│  │ Agents Pane    │              │ Files Pane           │       │
│  │ - Command Ctr  │◄────SSE──────┤ - Files Feed         │       │
│  │ - Agent View   │              │ - File Viewer        │       │
│  └────────────────┘              └──────────────────────┘       │
└────────────────────┬─────────────────────────────────────────────┘
                     │ REST API
                     │
┌────────────────────▼─────────────────────────────────────────────┐
│                       FLASK BACKEND                              │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │ AgentManager (Singleton)                                 │   │
│  │  - start_agent(id, type, log_file, session_config)      │   │
│  │  - stop_agent(id)                                        │   │
│  │  - Agent Registry: {agent_id: AgentRunner}              │   │
│  └──────────────────┬───────────────────────────────────────┘   │
│                     │                                            │
│  ┌──────────────────▼───────────────────────────────────────┐   │
│  │ LogManager + FileWatcher (watchdog)                      │   │
│  │  - Watches: data/sessions/dev_session/logs/*.jsonl      │   │
│  │  - Streams via SSE to frontend                           │   │
│  └──────────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│                    AGENT LAYER (Background Threads)              │
│                                                                  │
│  ┌────────────────────────────────────────────────────────┐     │
│  │ AgentRunner (Wrapper)               

*[truncated — see source for full prompt]*