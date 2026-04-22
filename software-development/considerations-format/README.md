# Considerations Format

> ## Purpose

Define structure for 21 considerations used by power-steering.

## Phase 1: Hardcoded

In MVP, considerations are hardcoded in `power_stee

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Considerations Format

## Purpose

Define structure for 21 considerations used by power-steering.

## Phase 1: Hardcoded

In MVP, considerations are hardcoded in `power_steering_checker.py`:

```python
CONSIDERATIONS = [
    {
        "id": "autonomous_question",
        "category": "Session Completion & Progress",
        "question": "Is agent stopping to ask question that could be answered autonomously?",
        "severity": "blocker",
        "checker": "_check_autonomous_question"
    },
    # ... 20 more
]
```

## Phase 2: External File

Move to `~/.amplihack/.claude/tools/amplihack/considerations/default.json`:

```json
{
  "version": "1.0",
  "considerations": [
    {
      "id": "autonomous_question",
      "category": "Session Completion & Progress",
      "order": 1,
      "question": "Is agent stopping to ask question that could be answered autonomously?",
      "description": "Check if agent is asking user for information that could be obtained by reading files, checking docs, running tests, or searching the web.",
      "severity": "blocker",
      "checker": "_check_autonomous_question",
      "hints": [
        "Look for question marks in last assistant message",
        "Check if answer could be in existing files",
        "Verify if documentation exists for question"
      ]
    },
    {
      "id": "objective_complete",
      "category": "Session Completion & Progress",
      "order": 2,
      "question": "Did session complete user's objective?",
      "description": "Compare original user request with what was actually done.",
      "severity": "blocker",
      "checker": "_check_objective_complete",
      "hints": [
        "Extract objective from first user message",
        "Check for completion indicators in last message",
        "Verify all requested files were created/modified"
      ]
    },
    {
      "id": "todos_complete",
      "category": "Session Completion & Progress",
      "order": 3,
      "question": "Were all TODO items comp

*[truncated — see source for full prompt]*