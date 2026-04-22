# Specs

> ---

  Test Coverage Implementation Task - Strategic Path to 48-50% Coverage

  Initial Setup and Context

  Please begin by reading these critical so

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
---

  Test Coverage Implementation Task - Strategic Path to 48-50% Coverage

  Initial Setup and Context

  Please begin by reading these critical sources of information in order:
  1. COVERAGE_REQUIREMENTS - Read the "TEST COVERAGE - Organization Requirements"
  2. RULES - Read the "FORBIDDEN_PATHS" section

  After reading these files, confirm your understanding of:
  - Current coverage statistics
  - Coverage Target percentage
  - The critical formula: Overall Impact = (Module Statements ÷ Total Statements) × Coverage Gain

  Critical Rules You MUST Follow

  🚫 FORBIDDEN ACTIONS - NEVER DO THESE:
  1. NEVER modify ANY file listed in the FORBIDDEN_PATHS section of RULES
  2. NEVER add # pragma: no cover comments anywhere
  3. NEVER mock Python standard library (json, csv, open, etc.) - use real operations with tempfile
  4. NEVER skip the RED phase of TDD - Every test MUST fail first
  5. NEVER test implementation details - Test behavior and outcomes only
  6. NEVER create new mock patterns - Use existing factories in tests/mocks/
  7. NEVER try to fix failing tests by changing source code - Work around issues in tests
  8. NEVER waste time on small modules (<300 statements) - Focus on Azure, Entra ID, M365 only


  Special Instructions

  1. in order to add `# pragma: no cover` comments anywhere, you must ask for permission from the team lead, and the target MUST meet the EXCLUDABLE_REQUIREMENTS definition in COVERAGE_REQUIREMENTS

  Implementation Instructions

  Think carefully and step by step as you implement each day's tasks. For each test you write:

  1. Before writing any test, think step by step about:
    - What behavior am I testing?
    - What should the expected output be?
    - How can I test this without mocking standard library?
  2. Show your TDD process explicitly:
  STEP 1 (RED): Writing test for [method_name]
  [Show test code]
  Running test... EXPECTED: FAIL
  [Show failure output]

  STEP 2 (GREEN): Making test pass
  [Show minimal change

*[truncated — see source for full prompt]*