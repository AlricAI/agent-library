# BUGFIX START PAUSED

> ## Problem

Demo agents were starting **running** and then immediately being **paused**, causing a race condition:

```jsonl
{"status": "running", "me

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Start Paused - No More Race Conditions! 🏁

## Problem

Demo agents were starting **running** and then immediately being **paused**, causing a race condition:

```jsonl
{"status": "running", "message": "Agent started", "timestamp": "...590440"}
{"status": "paused", "message": "Paused by user", "timestamp": "...590631"}
```

Only 191 microseconds between these events! But in that time:
- The agent thread is running
- Could make an LLM call before seeing the pause signal
- Could perform actions before being paused
- Wasteful to start and immediately pause

## The Fix

### 1. Added `start_paused` Parameter to `AgentRunner`

```python
def __init__(
    self,
    agent_instance: BaseAgent,
    agent_id: str,
    log_file: Path,
    agent_config: Optional[Dict[str, Any]] = None,
    start_paused: bool = False  # <-- NEW!
):
    # ...
    self.running = False
    self.paused = start_paused  # <-- Respects initial state
```

### 2. Updated `start()` to Respect Initial State

**Before:**
```python
def start(self):
    self.running = True
    self.paused = False  # <-- Always unpaused!
    self.thread.start()
```

**After:**
```python
def start(self):
    self.running = True
    # Don't override self.paused - respect start_paused setting
    self.thread.start()
```

### 3. Updated `_run_loop()` to Log Correct Initial Status

```python
def _run_loop(self):
    # Log initial status based on paused state
    if self.paused:
        self._log({'type': 'status', 'status': 'paused', 'message': 'Agent started (paused)'})
    else:
        self._log({'type': 'status', 'status': 'running', 'message': 'Agent started'})
```

### 4. Updated `AgentManager.start_agent()`

```python
def start_agent(
    self,
    agent_id: str,
    agent_type: str,
    log_file: Path,
    wikicontent_path: Path,
    agent_config: Optional[Dict] = None,
    use_real_agent: Optional[bool] = None,
    start_paused: bool = False  # <-- NEW!
):
    # For real agents:
    runner = AgentRunner(
        agent_ins

*[truncated — see source for full prompt]*