# MIGRATION GUIDE TEMPLATE

> > **Version**: [New Version]
> **Release Date**: [Date]
> **Migration Deadline**: [Deadline]
> **Difficulty**: [Easy/Medium/Hard]

## Overview

Brief 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Migration Guide: [Old Version] → [New Version]

> **Version**: [New Version]
> **Release Date**: [Date]
> **Migration Deadline**: [Deadline]
> **Difficulty**: [Easy/Medium/Hard]

## Overview

Brief description of this migration and why it's needed.

## Breaking Changes Summary

| Change | Impact | Required Action |
|--------|--------|-----------------|
| [Change 1] | [Impact description] | [Action required] |
| [Change 2] | [Impact description] | [Action required] |

## Prerequisites

Before starting this migration:

- [ ] Backup your data/configuration
- [ ] Review the [CHANGELOG](../CHANGELOG.md) for all changes
- [ ] Ensure you're running version [minimum version]
- [ ] Test in a staging environment first

## Migration Steps

### Step 1: [Step Title]

**Description**: What this step accomplishes.

**Before** (old code/config):
```go
// Old implementation
func OldFunction(ctx context.Context, req *OldRequest) (*OldResponse, error) {
    // ...
}
```

**After** (new code/config):
```go
// New implementation
func NewFunction(ctx context.Context, req *NewRequest) (*NewResponse, error) {
    // ...
}
```

**Verification**:
```bash
# Command to verify step completed successfully
virtengine query [module] [command]
```

### Step 2: [Step Title]

**Description**: What this step accomplishes.

**Actions**:
1. [Action 1]
2. [Action 2]
3. [Action 3]

**Verification**:
```bash
# Verification command
```

### Step 3: Update Client Dependencies

**For Go clients**:
```bash
go get github.com/virtengine/virtengine@[new-version]
go mod tidy
```

**For TypeScript clients**:
```bash
npm install @virtengine/sdk@[new-version]
```

### Step 4: Update Configuration

**Old configuration** (`config.yaml`):
```yaml
old_setting: value
deprecated_field: true
```

**New configuration** (`config.yaml`):
```yaml
new_setting: value
# deprecated_field removed - now uses new_replacement_field
new_replacement_field: true
```

## API Changes

### Renamed Endpoints

| Old Endpoint | New Endpoint |

*[truncated — see source for full prompt]*