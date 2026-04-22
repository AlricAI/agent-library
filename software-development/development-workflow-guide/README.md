# Development Workflow Guide

> description: globs: alwaysApply: false

## Tags
`typescript` `openai`

## System Prompt
---
description:
globs:
alwaysApply: false
---
# Development Workflow Guide

This project uses pnpm for package management and has a structured set of scripts for different development tasks.

## 🔧 NPM Scripts

### Core Commands
Located in [package.json](mdc:package.json):

```bash
# Build and format agents
pnpm run build          # Build all Agent files
pnpm run format         # Format Agent configurations (triggers translation)

# Validation and testing
pnpm run test           # Run validation tests
pnpm run test:locale    # Test multi-language files
pnpm run type-check     # TypeScript type checking

# Language validation
pnpm run validate:lang              # Validate all translation files
pnpm run validate:lang --delete     # Validate and clean invalid files
pnpm run clean:lang                 # Shorthand for validate with delete

# Maintenance
pnpm run update:awesome             # Update README file
```

### Translation Workflow
The main translation process is triggered by:
```bash
pnpm run format
```

This command:
1. Calls [scripts/commands/format.ts](mdc:scripts/commands/format.ts)
2. Executes `formatAgents()` function
3. Processes each agent through [scripts/formatters/agent-formatter.ts](mdc:scripts/formatters/agent-formatter.ts)
4. Performs incremental translation detection
5. Validates language accuracy
6. Saves formatted and translated files

## 🚀 Development Best Practices

### Before Making Changes
1. Run `pnpm run type-check` to ensure TypeScript correctness
2. Test changes with a small subset of agents first
3. Use incremental translation to avoid unnecessary API calls

### Code Quality Checks
- **TypeScript**: Use strict type checking
- **ESLint**: Follow project linting rules
- **Prettier**: Code formatting is handled automatically

### Testing Translation Changes
```bash
# Test specific language
pnpm run test:locale

# Validate a single file
pnpm run validate:lang path/to/agent.en-US.json

# Clean up invalid translations
pnpm run clean:lang
```

*[truncated — see source for full prompt]*