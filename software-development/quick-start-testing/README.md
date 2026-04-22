# QUICK START TESTING

> ## TL;DR

This is a comprehensive TDD test suite for the Auto Mode Interactive UI feature. **All tests currently FAIL** - this is intentional and corr

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quick Start Guide: Auto Mode UI Testing

## TL;DR

This is a comprehensive TDD test suite for the Auto Mode Interactive UI feature. **All tests currently FAIL** - this is intentional and correct. The tests serve as specifications for implementation.

## Files Location

```
tests/
├── unit/
│   ├── test_auto_mode_ui.py           # UI components (40+ tests)
│   ├── test_ui_threading.py           # Threading/concurrency (25+ tests)
│   ├── test_ui_sdk_integration.py     # Claude SDK integration (30+ tests)
│   └── README_AUTO_MODE_UI_TESTS.md   # Detailed documentation
├── integration/
│   └── test_auto_mode_ui_integration.py  # E2E workflows (20+ tests)
└── AUTO_MODE_UI_TEST_SUITE_SUMMARY.md    # Executive summary
```

**Total**: 115+ test cases across 4 files

## Quick Test Commands

### Run One Test (Verify Setup)

```bash
pytest tests/unit/test_auto_mode_ui.py::TestAutoModeUIInitialization::test_ui_mode_creates_ui_instance -v
```

**Expected**: FAIL with AttributeError (this is correct!)

### Run by Phase

```bash
# Phase 1: UI Foundation
pytest tests/unit/test_auto_mode_ui.py::TestAutoModeUIInitialization -v

# Phase 2: Threading
pytest tests/unit/test_ui_threading.py::TestAutoModeBackgroundThread -v

# Phase 3: SDK Integration
pytest tests/unit/test_ui_sdk_integration.py::TestTitleGenerationViaSDK -v

# Phase 4: User Interactions
pytest tests/unit/test_auto_mode_ui.py::TestKeyboardCommands -v

# Phase 5: E2E Workflows
pytest tests/integration/test_auto_mode_ui_integration.py::TestFullUIWorkflow -v
```

### Run All Tests

```bash
pytest tests/unit/test_auto_mode_ui.py \
       tests/unit/test_ui_threading.py \
       tests/unit/test_ui_sdk_integration.py \
       tests/integration/test_auto_mode_ui_integration.py -v
```

### With Coverage Report

```bash
pytest tests/unit/test_auto_mode_ui.py \
       tests/unit/test_ui_threading.py \
       tests/unit/test_ui_sdk_integration.py \
       tests/integration/test_auto_mode_ui_integration.py \
       --cov=amplihack

*[truncated — see source for full prompt]*