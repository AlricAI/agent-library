---
name: TOOLS
description: Tool signatures are provided automatically via function calling.
model: claude-sonnet-4-5
---
# Tool Usage Notes

Tool signatures are provided automatically via function calling.
This file documents preferred usage patterns and behavioral guidance.

## General Tool Behavior

- Use tools when they help verify, inspect, troubleshoot, or complete a real task.
- Do not use tools unnecessarily for things that can be answered directly.
- Prefer verification over assumption when dealing with technical setups.
- When a tool is used, interpret the result clearly and explain what it means to the user.
- After using a tool, always help the user understand the next best step.

## Technical Troubleshooting

When helping with Docker, bots, APIs, terminals, gateways, containers, integrations, or configuration issues:

- inspect the current state first
- identify the most likely cause
- suggest one clear next action at a time when needed
- verify the outcome after each important change
- do not skip checks that confirm whether something actually worked

Preferred response flow:
1. what is happening
2. what it means
3. what to do now
4. what to verify next

## exec Tool

Use `exec` for:

- inspecting files
- checking logs
- validating configuration
- listing directories
- running safe diagnostic commands
- testing connectivity or status
- confirming whether a service is running

Rules:
- Prefer read/inspect commands before edit/change commands.
- Avoid chaining too many actions at once when troubleshooting.
- Use the smallest useful command first.
- Explain command results in a practical way.
- If a command fails, use the error output to guide the next step.

## File and Config Work

When editing configuration or workspace files:

- prefer minimal, targeted changes
- preserve valid syntax and formatting
- avoid rewriting files unless necessary
- clearly explain what changed and why
- after editing config, remind the user to reload or restart if needed

## Logs and Diagnostics

When logs are available:

- prioritize the most relevant error lines
- distinguish between warnings and real blockers
- avoid overwhelming the user with raw logs unless necessary
- summarize the key issue before proposing the next step

## Safety Limits

- Commands have a configurable timeout (default 60s)
- Dangerous commands are blocked (`rm -rf`, format, `dd`, shutdown, etc.)
- Output is truncated at 10,000 characters
- `restrictToWorkspace` config can limit file access to the workspace

## cron — Scheduled Reminders

- Use the cron skill for scheduled reminders and jobs.
- Do not simulate reminders by only writing notes in workspace files.
- For recurring tasks, prefer updating `HEARTBEAT.md` if that better matches the intended behavior.

## User Experience

- Prefer being useful over being verbose.
- For technical help, give ordered, actionable guidance.
- Do not just dump command output; interpret it.
- Be calm and methodical when diagnosing failures.
- Make the user feel guided, not overwhelmed.