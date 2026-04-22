# Specs

> - jj > git
- cargo.toml or similiar should be version bumped before git tag is run
- version bump minor number on each feature release, and reset patc

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
- jj > git
- cargo.toml or similiar should be version bumped before git tag is run
- version bump minor number on each feature release, and reset patch number to 0
- version bump patch number on each bug fix, and each time a commit is made that passes all tests, checks, and doc updates.
---

  Test Coverage Implementation Task - Strategic Path to 48-50% Coverage

  Initial Setup and Context

  Please begin by reading these three critical documentation files in order:
  1. PLAN - Contains the PLAN you should follow
  2. CONVENTIONS - Contains all conventions to follow (git branching strategy, commit message format, code style guidelines, etc)
  3. CHALLENGES - Contains all your challenges and solutions and lessons learned for each day

  After reading these files, confirm your understanding of:
  - Current coverage is 41.7% (1,519/3,369 statements)
  - Target is 48-50% coverage (98-166 additional statements needed)
  - The critical formula: Overall Impact = (Module Statements ÷ 3369) × Coverage Gain
  - Azure module (817 statements, 24.3% of codebase) MUST be fixed first

  Critical Rules You MUST Follow

  🚫 FORBIDDEN ACTIONS - NEVER DO THESE:
  1. NEVER modify ANY file in the goosey/ directory - Only create/modify test files
  2. NEVER add `# pragma: no cover` comments anywhere
  3. NEVER mock anything - Put a `# pragma: no cover; NEEDSMOCK ` tag as an inline comment where you believe the mock is necessary
  4. NEVER skip the RED phase of TDD - Every test MUST fail first
  5. NEVER test implementation details - Test behavior and outcomes only
  6. NEVER create new mock patterns

  REQUIRE ACTIONS - ALWAYS DO THESE:
  1. ALWAYS ensure pre-commit is configured correctly at the beginning of each day's work
  2. ALWAYS log the challenges, solutions, and lessons learned to CHALLENGES as soon as you have hall passing tests again and before you make a commit
  3. ALWAYS commit your changes as soon as you have updated CHALLENGES

  Implementation Instructions

  Think car

*[truncated — see source for full prompt]*