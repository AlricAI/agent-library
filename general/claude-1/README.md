# CLAUDE

> ## Project Structure & Scope

This project is a collection of context documents for "teams" of agents, with critical organizational principles:

### D

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Agent Context Guidelines

## Project Structure & Scope

This project is a collection of context documents for "teams" of agents, with critical organizational principles:

### Directory-Based Team Organization
- Agent teams and groups are organized by directory
- Each directory represents a distinct team or functional group
- Directories contain context documents specific to that team's responsibilities

### Work Scope Rules
**PRIMARY RULE**: Any work performed by Claude in this project MUST be scoped to a single non-recursive directory unless explicitly stated otherwise.

**Rationale**: This ensures:
- Clear boundaries between agent teams
- Prevents unintended cross-contamination of contexts
- Maintains separation of concerns
- Allows for focused, targeted improvements

**Exception**: Some agents are designed to interact with agents in other groups or teams. These cross-team agents are the minority and will have explicit instructions in their context allowing multi-directory operations.

## Operational Constraints

These constraints govern ALL agent operations within this project and supersede any conflicting instructions:

### Execution Boundaries
**FUNDAMENTAL RULE**: Do what has been asked; nothing more, nothing less.
- Execute only the specific task requested
- Avoid scope creep or additional "helpful" actions not requested
- If unclear about scope, ask for clarification before proceeding

### File Management Rules
1. **NEVER create files unless they're absolutely necessary** for achieving the stated goal
2. **ALWAYS prefer editing an existing file** to creating a new one
3. **NEVER proactively create documentation files** (*.md) or README files
4. **Only create documentation files if explicitly requested** by the user

### Decision Framework
When considering any action, ask yourself step by step:
1. Was this specific action explicitly requested?
2. Is this action absolutely necessary to complete the request?
3. Can the goal be achieved by editing existing fil

*[truncated — see source for full prompt]*