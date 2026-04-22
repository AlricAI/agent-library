# Updating Existing Tests

> ## Overview
After migrating agents to use the Claude Agent SDK, existing tests need minor updates to continue working. This document explains the requ

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Updating Existing Tests for SDK Migration

## Overview
After migrating agents to use the Claude Agent SDK, existing tests need minor updates to continue working. This document explains the required changes.

## Why Tests Are Failing

The migrated `BackendWorkerAgent` now defaults to `use_sdk=True`, which means:

1. Files are written by the SDK's Write tool, not directly by `apply_file_changes()`
2. Code generation uses SDK message passing, not direct Anthropic API calls
3. The SDK client needs to be mocked or disabled for unit tests

## Solution: Set use_sdk=False for Unit Tests

### Before Migration
```python
def test_apply_file_changes_creates_new_file(tmp_path):
    agent = BackendWorkerAgent(
        project_id=1,
        db=mock_db,
        codebase_index=mock_index,
        project_root=tmp_path  # Path object
    )

    files = [{"path": "src/example.py", "action": "create", "content": "..."}]
    agent.apply_file_changes(files)

    assert (tmp_path / "src" / "example.py").exists()
```

### After Migration
```python
def test_apply_file_changes_creates_new_file(tmp_path):
    agent = BackendWorkerAgent(
        project_id=1,
        db=mock_db,
        codebase_index=mock_index,
        project_root=str(tmp_path),  # String path (SDK compatibility)
        use_sdk=False  # Disable SDK for direct file operation testing
    )

    files = [{"path": "src/example.py", "action": "create", "content": "..."}]
    agent.apply_file_changes(files)

    assert (tmp_path / "src" / "example.py").exists()
```

## Required Changes

### 1. Constructor Updates

**Change Required:**
- Convert `project_root` from Path to str
- Add `use_sdk=False` parameter

**Example:**
```python
# BEFORE
agent = BackendWorkerAgent(
    project_id=1,
    db=db,
    codebase_index=index,
    project_root=tmp_path
)

# AFTER
agent = BackendWorkerAgent(
    project_id=1,
    db=db,
    codebase_index=index,
    project_root=str(tmp_path),
    use_sdk=False
)
```

### 2. Code Generation Tests

Te

*[truncated — see source for full prompt]*