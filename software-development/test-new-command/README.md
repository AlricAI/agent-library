# Test New Command

> Test command to verify auto-detection and registry updates work correctly

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Test New Command

This is a test command created to verify that the auto-detection system works.

## Usage

```bash
/test-new-command
```

## Features

- Auto-detected by the system
- Automatically added to registry
- Validates the build system works

## Testing

This file should be:
1. Detected by `auto-detect-components.sh`
2. Added to registry.json automatically
3. Validated by `validate-registry.sh`