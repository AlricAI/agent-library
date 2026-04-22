# Stop Py Integration

> ## Purpose

Add power-steering check to existing stop.py hook orchestrator.

## Current stop.py Structure

Based on investigation, stop.py handles:

1

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Integration: Modifying stop.py

## Purpose

Add power-steering check to existing stop.py hook orchestrator.

## Current stop.py Structure

Based on investigation, stop.py handles:

1. Lock mechanism check
2. Reflection check (if enabled)
3. Neo4j cleanup (if enabled)

## Proposed Modification

Add power-steering as 3rd check, after reflection.

## Exact Changes Required

### Location

`~/.amplihack/.claude/tools/amplihack/hooks/stop.py`

### Change 1: Import PowerSteeringChecker

Add after existing imports:

```python
from .power_steering_checker import PowerSteeringChecker, PowerSteeringResult
```

### Change 2: Add power-steering check in process() method

Find the section after reflection check (around line 150-200), add:

```python
# Power-Steering Check
if self._should_run_power_steering(input_data):
    try:
        ps_checker = PowerSteeringChecker(self.project_root)
        ps_result = ps_checker.check(transcript_path, session_id)

        if ps_result.decision == "block":
            self.log_metric("power_steering_blocked", 1)
            return {
                "decision": "block",
                "reason": "power_steering",
                "continuation_prompt": ps_result.continuation_prompt
            }
        elif ps_result.decision == "approve":
            self.log_metric("power_steering_approved", 1)

            # Display summary if available
            if ps_result.summary:
                print("\n" + "="*80)
                print("SESSION SUMMARY")
                print("="*80)
                print(ps_result.summary)
                print("="*80 + "\n")

    except Exception as e:
        # Log error but don't block on power-steering failures (fail-open)
        self.log_error(f"Power-steering check failed: {e}", exc_info=True)
        self.log_metric("power_steering_error", 1)
        # Continue to approve
```

### Change 3: Add \_should_run_power_steering() helper

Add as new method in StopHookProcessor class:

```python
def _should_run

*[truncated — see source for full prompt]*