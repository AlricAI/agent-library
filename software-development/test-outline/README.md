# Test Outline

> description: Professional test outline system for test files globs: - "**/test_*.py"

## Tags
`typescript` `javascript` `python`

## System Prompt
---
description: Professional test outline system for test files
globs:
  - "**/test_*.py"
  - "**/*.test.ts"
  - "**/*.test.tsx"
  - "**/*.spec.ts"
  - "**/*.spec.tsx"
  - "**/__tests__/**/*.ts"
  - "**/__tests__/**/*.tsx"
alwaysApply: false
---
## Format - Professional Test Outline System

All test implementations must adhere to this comprehensive structural framework to ensure consistency, maintainability, and professional-grade documentation across your testing suite.

### **Test File Structure Template**

#### **File Header Block**
Every test file must begin with this standardized header:

``
/**
 * ============================================================================
 * TEST SUITE: [Descriptive Suite Name]
 * ============================================================================
 * 
 * MODULE UNDER TEST: [target_module_name]
 * TEST TYPE: [Unit/Integration/E2E/Performance]
 * FRAMEWORK: [Jest/Mocha/PyTest/etc.]
 * 
 * AUTHOR: [Developer Name] <[email]>
 * CREATED: [YYYY-MM-DD]
 * LAST MODIFIED: [YYYY-MM-DD]
 * VERSION: [semantic version]
 * 
 * DESCRIPTION:
 * [Comprehensive description of what functionality this test suite validates]
 * 
 * DEPENDENCIES:
 * - [dependency_1]: [version] - [purpose]
 * - [dependency_2]: [version] - [purpose]
 * 
 * COVERAGE SCOPE:
 * ✓ [functionality_1]
 * ✓ [functionality_2]
 * ✗ [excluded_functionality] - [reason for exclusion]
 * 
 * EXECUTION REQUIREMENTS:
 * - Environment: [development/staging/production]
 * - Prerequisites: [database setup, API keys, etc.]
 * - Runtime: [estimated execution time]
 * 
 * ============================================================================
 */
``

#### **Import and Setup Section**
``
// EXTERNAL DEPENDENCIES
import [framework] from '[testing-framework]';
import [assertion] from '[assertion-library]';

// MODULE UNDER TEST  
import [targetModule] from '[module-path]';

// TEST UTILITIES AND MOCKS
import [testHelper] from '[helper-path]';
import [mockData] from '[mock-data

*[truncated — see source for full prompt]*