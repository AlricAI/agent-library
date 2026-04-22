# Subagent Driven Development

> Execute plan using subagent-driven development

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Execute Plan

**User Input:** $ARGUMENTS

**Instructions:**
1.  **Target:** I want to execute the implementation plan specified in "$ARGUMENTS".
2.  **Action:** Please **invoke/use the `subagent-driven-development` skill** immediately.
3.  Ensure that the implementation strictly follows **TDD** (Test-Driven Development).