# AGENTS

> This file provides guidance for AI assistants working on the oh-my-kimi project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# AGENTS.md - Project Guidance

This file provides guidance for AI assistants working on the oh-my-kimi project.

## Project Overview

**oh-my-kimi** is a workflow orchestration layer for Kimi Code CLI that brings structured workflows, agent teams, and persistent execution capabilities.

- **Purpose**: Enhance Kimi CLI with workflow management
- **Language**: TypeScript/JavaScript (Node.js 20+)
- **Architecture**: Hook-based integration with state management

## Development Guidelines

### Code Organization

```
src/
├── cli/        # User-facing commands
├── hooks/      # Kimi lifecycle hooks
├── state/      # State persistence
└── utils/      # Shared utilities
```

### Key Principles

1. **Minimal Intrusion**: OMK should enhance, not replace, Kimi CLI
2. **State Durability**: All workflow state persists to `.omk/`
3. **Hook Safety**: Hooks must be fast (<100ms) and reliable
4. **Skill Clarity**: Each skill has a single, well-defined purpose

### When Working on OMK

#### Adding Features

- Prefer extending existing skills over creating new ones
- Always update state schemas when adding new state fields
- Test hook performance with large prompts

#### Fixing Bugs

- Check `.omk/state/` for corrupted state files
- Verify hook output format matches Kimi's expectations
- Test across different Node.js versions

#### Refactoring

- Maintain backward compatibility for state files
- Keep CLI interface stable
- Document any breaking changes in CHANGELOG.md

## Common Tasks

### Adding a New CLI Command

1. Add command handler in `src/cli/`
2. Register in `src/cli/index.ts`
3. Update `--help` output
4. Add tests

### Modifying Hook Behavior

1. Update `src/hooks/handler.ts`
2. Ensure JSON output format is correct
3. Test with `scripts/test-hook.js`
4. Update documentation

### Adding State Management

1. Define interface in `src/state/manager.ts`
2. Add path constant in `src/state/paths.ts`
3. Implement read/write methods
4. Add validation

## Testing Strategy

### Unit Te

*[truncated — see source for full prompt]*