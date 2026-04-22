# RUN TESTS

> ## Quick Start

Run all tests with a single command:

```bash
# From project root
python tests/manual_test_stop_hook_visibility.py
```

Expected outpu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# How to Run Stop Hook Visibility Tests

## Quick Start

Run all tests with a single command:

```bash
# From project root
python tests/manual_test_stop_hook_visibility.py
```

Expected output: "🎉 ALL TESTS PASSED! The visibility fix is working correctly."

## Individual Test Suites

### 1. Unit Tests - Reflection Imports

Tests that reflection module imports work without errors.

```bash
python -m unittest tests.test_reflection_imports -v
```

**What it tests:**

- Reflection module can be imported
- analyze_session_patterns function exists
- process_reflection_analysis function exists
- All exported functions are callable
- Import paths work from different contexts

**Expected:** All tests pass, ~15 tests total

---

### 2. Critical Scenario Tests

Tests the exact bug scenarios that were broken.

```bash
python -m unittest tests.test_stop_hook_critical_scenarios -v
```

**What it tests:**

- CRITICAL: Empty learnings + existing decisions returns message
- CRITICAL: Output dict initialized before decision_summary
- CRITICAL: extract_learnings imports correctly from reflection
- Output dict structure validation (JSON serializable)
- Integration tests for complete flow

**Expected:** All tests pass, ~20 tests total

---

### 3. E2E Visibility Tests

Tests end-to-end user-facing visibility.

```bash
python -m unittest tests.test_stop_hook_e2e_visibility -v
```

**What it tests:**

- Decision records appear in hook output
- Output displays when stopping session
- Hook output serializes to JSON
- Decision file links are clickable
- Real-world user scenarios
- Regression prevention for all three bugs

**Expected:** All tests pass, ~15 tests total

---

### 4. Decision Summary Tests (Existing)

Comprehensive tests for display_decision_summary() method.

```bash
python -m unittest tests.test_stop_hook_decision_summary -v
```

**What it tests:**

- Valid DECISIONS.md file handling
- Empty file scenarios
- Malformed decision records
- File path generation
- Error handling (

*[truncated — see source for full prompt]*