# REFERENCES

> **Lazy Loading Principle**: Only read files that are relevant to your current task.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Reference Guide - When to Load Which Files

**Lazy Loading Principle**: Only read files that are relevant to your current task. Don't load entire framework upfront.

## 🎯 Always Start Here

**[main.md](./main.md)** - Entry point
- Load: Always (defines agent behavior and general guidelines)
- ~100 lines, quick read

**`~/.config/deft/USER.md`** - User preferences
- Load: Always (highest precedence, overrides everything)
- Check for custom rules and preferences
- Override path via `DEFT_USER_PATH` env var

**[core/glossary.md](./core/glossary.md)** - Term definitions
- Load: When encountering unfamiliar terms (release, feature, demo sentence, context rot, etc.)
- Contains: work decomposition hierarchy, GSD → Deft term mapping

## 📋 Task-Based Loading

### When Writing Code

1. **[coding/coding.md](./coding/coding.md)** - General coding guidelines
   - Load: For any software development task
   - Contains: modularity, contracts, error handling, change management

2. **Language file** - Load based on language:
   - [languages/python.md](./languages/python.md) - When writing Python
   - [languages/go.md](./languages/go.md) - When writing Go
   - [languages/typescript.md](./languages/typescript.md) - When writing TypeScript/JavaScript
   - [languages/cpp.md](./languages/cpp.md) - When writing C++

3. **[PROJECT.md](./PROJECT.md)** - Project-specific rules
   - Load: When unsure about project standards
   - Contains: project tech stack, coverage requirements, telemetry config

### When Building Interfaces

Load based on interface type:

- **[interfaces/cli.md](./interfaces/cli.md)** - Building command-line tools
- **[interfaces/rest.md](./interfaces/rest.md)** - Designing/implementing REST APIs
- **[interfaces/tui.md](./interfaces/tui.md)** - Building terminal UIs (Textual, ink)
- **[interfaces/web.md](./interfaces/web.md)** - Building web UIs (React, etc.)

### When Working with Deployment Platforms

Load when working on platform-specific deployment guidance:

- **[d

*[truncated — see source for full prompt]*