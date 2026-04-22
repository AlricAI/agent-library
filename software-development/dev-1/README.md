# Dev

> ## Continuous Autonomous Testing Philosophy

### The Problem We Solved
**Manual Testing is Unsustainable**: Previously, every change required manual v

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# 🔧 Atlas Development Notes

## Continuous Autonomous Testing Philosophy

### The Problem We Solved
**Manual Testing is Unsustainable**: Previously, every change required manual validation with requests like "Hey, can you check this, test this?" This doesn't scale and introduces human error and inconsistency.

**Solution**: Comprehensive automated testing that validates everything systematically and runs continuously.

### Testing Framework Architecture

#### 1. **Multi-Layer Testing Strategy**
```
┌─────────────────────────────────────┐
│ End-to-End Tests (test_e2e.py)     │ ← Full user workflows
├─────────────────────────────────────┤
│ Integration Tests (test_web_*)      │ ← Component integration
├─────────────────────────────────────┤
│ Unit Tests (test_cognitive_*)       │ ← Individual components
├─────────────────────────────────────┤
│ Security Tests (Bandit/Safety)     │ ← Vulnerability scanning
└─────────────────────────────────────┘
```

#### 2. **Continuous Validation Pipeline**
- **On Every Commit**: Full test suite runs automatically
- **Daily Health Checks**: Scheduled tests at 2 AM UTC catch drift
- **Matrix Testing**: Python 3.9, 3.10, 3.11 compatibility
- **Coverage Tracking**: Identifies untested code paths

### Key Learnings & Insights

#### ✅ **What Works Well**
1. **FastAPI TestClient**: Seamless integration testing of web endpoints
2. **Cognitive Feature Wrappers**: Simple compatibility layers fix complex integration issues
3. **Pytest Fixtures**: Reusable test infrastructure reduces duplication
4. **GitHub Actions Matrix**: Multi-version testing catches compatibility issues early

#### 🔍 **Critical Discoveries**

**Cognitive Feature Integration Issues**:
```python
# PROBLEM: Inconsistent initialization patterns
ProactiveSurfacer(config)         # Expected dict
ProactiveSurfacer(metadata_manager) # Got object

# SOLUTION: Adaptive constructor
def __init__(self, metadata_manager_or_config = None):
    if hasattr(metadata_manager_or_config, 'co

*[truncated — see source for full prompt]*