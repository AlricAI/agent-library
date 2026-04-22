# TESTING PHILOSOPHY

> This document captures the testing approach and learnings from building robust, self-validating development tools.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OOS Testing Philosophy - Continuous Autonomous Validation

This document captures the testing approach and learnings from building robust, self-validating development tools.

## 🎯 Core Philosophy: Manual Testing is Unsustainable

**The Problem**: Every change required manual validation - "Hey, can you check this?" This doesn't scale and introduces human error.

**The Solution**: Comprehensive automated testing that validates everything systematically and runs continuously.

## 🏗️ Testing Architecture

### **Multi-Layer Testing Strategy**
```
┌─────────────────────────────────────┐
│ End-to-End Tests                    │ ← Full user workflows
├─────────────────────────────────────┤
│ Integration Tests                   │ ← Component integration
├─────────────────────────────────────┤
│ Unit Tests                          │ ← Individual functions
├─────────────────────────────────────┤
│ Security Tests                      │ ← Vulnerability scanning
└─────────────────────────────────────┘
```

### **Continuous Validation Pipeline**
- **On Every Commit**: Full test suite runs automatically via GitHub Actions
- **Daily Health Checks**: Scheduled tests catch configuration drift
- **Matrix Testing**: Multi-environment compatibility validation
- **Coverage Tracking**: Identifies untested code paths

## 🔍 Key Testing Insights

### **What Works Well**
1. **Simple Assertion Libraries**: Bash test libraries with clear pass/fail indicators
2. **Behavioral Testing**: Test what users experience, not implementation details
3. **Graceful Degradation**: Systems should handle missing dependencies elegantly
4. **Realistic Test Data**: Use actual usage patterns, not generic test strings

### **Critical Testing Discoveries**

#### **Environment Compatibility Issues**
```bash
# PROBLEM: Scripts fail in different environments
./script.sh   # Works on dev machine
              # Fails in CI with missing dependencies

# SOLUTION: Mock dependencies in CI
cat << 'EOF' | sudo tee /usr/loc

*[truncated — see source for full prompt]*