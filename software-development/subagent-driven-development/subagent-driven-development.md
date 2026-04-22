---
name: Subagent Driven Development
description: Execute plan using subagent-driven development
model: claude-sonnet-4-5
---
# Execute Plan

**User Input:** $ARGUMENTS

**Instructions:**
1.  **Target:** I want to execute the implementation plan specified in "$ARGUMENTS".
2.  **Action:** Please **invoke/use the `subagent-driven-development` skill** immediately.
3.  Ensure that the implementation strictly follows **TDD** (Test-Driven Development).