# AUTO MODE TRANSPARENCY DESIGNS

> ## Problem Statement

Auto mode currently operates as a "black box" - users see turn transitions but lack insight into:

- Which turn they're on (out 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Auto Mode Transparency Design

## Problem Statement

Auto mode currently operates as a "black box" - users see turn transitions but lack insight into:

- Which turn they're on (out of max turns)
- What phase of the turn is executing
- How long the session has been running

This creates uncertainty and makes it difficult to gauge progress or estimate completion time.

## Design Goals

1. **Minimal Friction**: Add transparency without cluttering output
2. **Actionable Information**: Show data that helps users make decisions
3. **Backward Compatible**: No breaking changes to existing functionality
4. **Clean Implementation**: ~60 LOC addition, maintainable code

## Approach 1: Minimal Progress Indicators (SELECTED)

### Overview

Add lightweight progress indicators to existing turn logging statements.

### Features

1. **Turn Counter**: `[Turn 2/10]` - Shows current turn and max turns
2. **Phase Indicators**: `[Clarifying]`, `[Planning]`, `[Executing]`, `[Evaluating]`, `[Summarizing]`
3. **Elapsed Time**: `[1m 23s]` or `[45s]` - Time since session start

### Output Format

```
[Turn 1/10 | Clarifying | 3s]
[Turn 2/10 | Planning | 45s]
[Turn 3/10 | Executing | 1m 23s]
[Turn 3/10 | Evaluating | 1m 45s]
[Turn 10/10 | Summarizing | 5m 12s]
```

### Integration Points

Current file: `src/amplihack/launcher/auto_mode.py`

#### 1. Track Start Time (Line ~283)

```python
def run(self) -> int:
    """Execute agentic loop."""
    self.start_time = time.time()  # ADD THIS LINE
    self.log(f"Starting auto mode (max {self.max_turns} turns)")
```

#### 2. Add Helper Methods

```python
def _format_elapsed(self, seconds: float) -> str:
    """Format elapsed time as Xm Ys or Xs."""
    if seconds < 60:
        return f"{int(seconds)}s"
    minutes = int(seconds // 60)
    remaining_seconds = int(seconds % 60)
    return f"{minutes}m {remaining_seconds}s"

def _progress_str(self, phase: str) -> str:
    """Build progress indicator string."""
    elapsed = time.time() - self.start_tim

*[truncated — see source for full prompt]*