---
name: Real Agents Architecture Diagram
description: ## System Overview

```
┌──────────────────────────────────────────────────────────────────┐
│                          MECHAWIKI UI                  
model: claude-sonnet-4-5
---
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
│  │ AgentRunner (Wrapper)                                  │     │
│  │  - Wraps BaseAgent subclass                            │     │
│  │  - Intercepts print() → logs                           │     │
│  │  - Intercepts tool calls → logs                        │     │
│  │  - Checks log file for control signals (pause/resume)  │     │
│  │  - Runs in background thread                           │     │
│  └────────────┬───────────────────────────────────────────┘     │
│               │                                                  │
│  ┌────────────▼───────────────────────────────────────────┐     │
│  │ BaseAgent (base_agent/base_agent.py)                   │     │
│  │  - litellm.completion() - LLM calls                    │     │
│  │  - Streaming token handling                            │     │
│  │  - Tool execution via _execute_tool()                  │     │
│  │  - Conversation history management                     │     │
│  │  - Memory dict for agent state                         │     │
│  └────────────┬───────────────────────────────────────────┘     │
│               │ Inheritance                                      │
│  ┌────────────┴───────────────┬─────────────┬──────────────┐    │
│  │                            │             │              │    │
│  │ ReaderAgent               WriterAgent   Interactive     │    │
│  │  + StoryWindow             Agent        Agent           │    │
│  │  + advance()               + write()    + send_prose()  │    │
│  │  + get_status()            + edit()     + request_input │    │
│  └────────────────────────────┴─────────────┴──────────────┘    │
└──────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│                         TOOLS LAYER                              │
│  ┌──────────────────┐  ┌──────────────────┐  ┌────────────────┐ │
│  │ articles.py      │  │ search.py        │  │ images.py      │ │
│  │ - read_article() │  │ - find_articles()│  │ - create_image │ │
│  │ - write_article()│  │ - find_images()  │  │                │ │
│  └──────────────────┘  └──────────────────┘  └────────────────┘ │
│                                                                  │
│  ┌──────────────────┐  ┌──────────────────┐                     │
│  │ story.py (NEW)   │  │ interactive.py   │                     │
│  │ - write_story()  │  │ (NEW)            │                     │
│  │ - edit_story()   │  │ - send_prose()   │                     │
│  │ - get_status()   │  │ - request_input()│                     │
│  └──────────────────┘  └──────────────────┘                     │
└──────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│                      DATA/STORAGE LAYER                          │
│                                                                  │
│  data/sessions/dev_session/                                      │
│  ├── config.yaml          ← Git branch, session settings        │
│  ├── agents.json          ← Agent definitions                   │
│  └── logs/                                                       │
│      ├── agent_reader-001.jsonl  ← All reader activity          │
│      ├── agent_writer-001.jsonl  ← All writer activity          │
│      └── agent_interactive-001.jsonl                             │
│                                                                  │
│  ~/Dev/wikicontent/       ← Wiki articles (git-managed)         │
│  └── articles/*.md                                               │
└──────────────────────────────────────────────────────────────────┘
```

---

## Data Flow: Creating and Running an Agent

```
1. USER clicks "+ New Agent" in UI
   ↓
2. UI sends POST /api/agents/create
   {
     "name": "Reader Agent 1",
     "type": "ReaderAgent", 
     "config": {"description": "...", "story": "tales_of_wonder"}
   }
   ↓
3. FLASK creates agent in session_config.agents.json
   ↓
4. FLASK creates empty log file: data/sessions/dev_session/logs/agent_reader-001.jsonl
   ↓
5. FLASK tells LogManager to watch the log file
   ↓
6. FLASK tells AgentManager to start the agent
   ↓
7. AGENTMANAGER creates AgentRunner(ReaderAgent, ...)
   ↓
8. AGENTRUNNER starts background thread
   ↓
9. AGENTRUNNER writes {"type": "status", "status": "running", ...} to log
   ↓
10. LOGMANAGER detects log change, streams to UI via SSE
   ↓
11. UI shows agent as ● running
   ↓
12. AGENTRUNNER calls agent.run_forever(max_turns=1)
    ↓
13. BASEAGENT calls litellm.completion() with tools
    ↓
14. LLM responds with tool call: advance(num_words=500)
    ↓
15. BASEAGENT executes tool via _execute_tool()
    ↓
16. AGENTRUNNER intercepts and logs:
    {"type": "tool_call", "tool": "advance", "args": {...}}
    {"type": "tool_result", "tool": "advance", "result": "..."}
    ↓
17. LOGMANAGER streams to UI
    ↓
18. UI updates "Last Action: advance to word 500"
    ↓
19. Loop continues...
```

---

## Control Flow: Pausing an Agent

```
1. USER clicks "Pause" button on agent
   ↓
2. UI sends POST /api/agents/{id}/pause
   ↓
3. FLASK writes to log:
   {"type": "status", "status": "paused", "message": "Paused by user"}
   ↓
4. LOGMANAGER detects change, streams to UI
   ↓
5. UI shows agent as ◐ paused
   ↓
   (Meanwhile, in background thread...)
   ↓
6. AGENTRUNNER._check_control_signals() reads log file
   ↓
7. AGENTRUNNER sees "status": "paused" entry
   ↓
8. AGENTRUNNER sets self.paused = True
   ↓
9. In _run_loop(), agent skips turn:
   if self.paused:
       time.sleep(0.5)
       continue
   ↓
10. Agent stops taking actions but thread stays alive
```

---

## Key Insight: Log-Based Architecture

**Why logs are the source of truth:**

```
┌─────────────────────────────────────────────────────────────────┐
│ Traditional Approach (Shared State)                            │
│                                                                 │
│  Flask Thread ────► shared_dict["agent_id"] = "paused"         │
│                     ▲                                           │
│                     │ Race conditions!                          │
│                     │ Lost on restart!                          │
│  Agent Thread ─────┘                                            │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│ MechaWiki Approach (Log-Based)                                 │
│                                                                 │
│  Flask Thread ────► write_to_log("status": "paused")           │
│                                         │                       │
│                                         │ File system           │
│                                         │ Persistent!           │
│                                         ▼                       │
│  Agent Thread ────► read_log() ──► sees "paused" ──► pauses    │
│                                                                 │
│  Benefits:                                                      │
│  ✓ No shared state / race conditions                           │
│  ✓ Survives restarts (replay from log)                         │
│  ✓ Complete audit trail                                        │
│  ✓ Works for both threads AND processes                        │
│  ✓ UI gets same data (LogManager watches same file)            │
└─────────────────────────────────────────────────────────────────┘
```

---

## Tool Execution Flow

```
LLM says: "Let me read the London article"
   ↓
LLM makes tool call: read_article(article_name="london")
   ↓
┌──────────────────────────────────────────────────────────┐
│ AGENTRUNNER intercepts                                   │
│   1. Logs: {"type": "tool_call", ...}                    │
│   2. Calls original _execute_tool()                      │
│      ↓                                                    │
│   ┌──────────────────────────────────────────────────┐   │
│   │ BASEAGENT._execute_tool()                        │   │
│   │   - Finds tool in self.tools                     │   │
│   │   - Gets actual function: read_article()         │   │
│   │   - Calls it with args                           │   │
│   │      ↓                                            │   │
│   │   ┌────────────────────────────────────────────┐ │   │
│   │   │ TOOL: read_article()                       │ │   │
│   │   │   - Opens ~/Dev/wikicontent/articles/      │ │   │
│   │   │   - Reads london.md                        │ │   │
│   │   │   - Returns content string                 │ │   │
│   │   └────────────────────────────────────────────┘ │   │
│   │      ↓                                            │   │
│   │   Returns result to BASEAGENT                    │   │
│   └──────────────────────────────────────────────────┘   │
│      ↓                                                    │
│   3. Logs: {"type": "tool_result", "result": "# London\n..."}
└──────────────────────────────────────────────────────────┘
   ↓
BASEAGENT adds tool result to conversation
   ↓
BASEAGENT calls LLM again with result
   ↓
LLM: "The London article describes a mythical city..."
```

---

## Memory Management

```
┌─────────────────────────────────────────────────────────┐
│ ReaderAgent Memory                                      │
│                                                         │
│  self.memory = {                                        │
│    "story_name": "tales_of_wonder",                     │
│    "story_path": "/path/to/story.txt",                  │
│    "current_position": 1500,                            │
│    "total_words": 50000,                                │
│    "progress_percent": 3.0,                             │
│    "is_complete": False,                                │
│    "articles_created": ["london", "wizard-merlin"],     │
│    "images_created": ["london-skyline.png"]             │
│  }                                                       │
│                                                         │
│  Accessed via:                                          │
│    self.get_memory("current_position")                  │
│    self.set_memory("articles_created", [...])           │
│    self.update_memory({"current_position": 2000})       │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Conversation History (BaseAgent.messages)               │
│                                                         │
│  [                                                      │
│    {"role": "system", "content": "You are a reader..."} │
│    {"role": "user", "content": "Start reading"}        │
│    {"role": "assistant", "content": "...",              │
│     "tool_calls": [...]},                               │
│    {"role": "tool", "tool_call_id": "...",              │
│     "content": "Advanced to word 500"},                 │
│    {"role": "user", "content": "Story chunk:\n\n..."},  │
│    {"role": "assistant", "content": "This scene..."}    │
│  ]                                                      │
│                                                         │
│  Context Management (advance_content):                  │
│    - Keeps last N story chunks active                   │
│    - Archives older chunks to prevent bloat             │
│    - Tagged with _advance_content flag                  │
└─────────────────────────────────────────────────────────┘
```

---

**This architecture is elegant, scalable, and already half-built!** 🏰⚔️