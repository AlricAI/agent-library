# TESTING STRATEGY

> This document outlines the testing philosophy, guidelines, and best practices for the CodeFRAME project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing Strategy for CodeFRAME

This document outlines the testing philosophy, guidelines, and best practices for the CodeFRAME project.

## Testing Philosophy

### Core Principles

1. **Real Implementations Over Mocks**: Prefer testing with real components when possible. Mocking should only be used for external services that are impractical to use in tests.

2. **Mock Boundaries, Not Internals**: Only mock at system boundaries (external APIs, network calls). Never mock internal methods or classes to make tests pass.

3. **Tests Should Fail When Code Breaks**: If removing a function or breaking logic doesn't cause a test to fail, the test is not valuable.

4. **Integration Tests for Workflows**: Test complete workflows with real database and file operations. Unit tests should focus on pure logic.

## Test Categories

### Unit Tests
- **Purpose**: Test individual functions and classes in isolation
- **Mock Policy**: Mock only external I/O (network, external APIs)
- **Location**: `tests/` directory (excluding `tests/integration/`)
- **Run Command**: `pytest -m "not integration"`

**Good Unit Test Example**:
```python
def test_sanitize_prompt_removes_special_chars():
    """Test pure logic - no mocking needed."""
    result = sanitize_prompt_input("Hello <script>alert()</script>")
    assert "<script>" not in result
```

**Bad Unit Test Example**:
```python
@patch("module.execute_task")  # ❌ Mocking the method being tested!
def test_execute_task(mock_execute):
    mock_execute.return_value = {"status": "completed"}
    result = execute_task(task)  # This tests nothing!
    assert result["status"] == "completed"
```

### Integration Tests
- **Purpose**: Test component interactions with real implementations
- **Mock Policy**: Mock only external services (Anthropic API, OpenAI, GitHub)
- **Location**: `tests/integration/`
- **Run Command**: `pytest -m integration`

**Good Integration Test Example**:
```python
@pytest.mark.integration
async def test_token_usage_recorded_

*[truncated — see source for full prompt]*