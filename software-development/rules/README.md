# RULES

> These rules govern all development activities within the software development team.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Software Development Team Rules

These rules govern all development activities within the software development team. All team members must adhere to these standards without exception.

## Code Requirements

### Documentation Standards
- All code must have 2 kinds of comments: inline and block comments.
  - Inline comments are for explaining specific lines of code.
  - Block comments are for explaining larger sections of code.
  - Block comments should include DEVNOTES, which describe the functionality of the code from the developer's perspective, so that test-engineers and technical writers can understand the code.
  - Block comments should include BUSINESSCASE, which describe the functionality of the code from the business logic perspective, so that test-engineers and technical writers can understand the code.
  - Code that will be Public Facing should be tagged with the inline comment `PUBLICFACING`.

### Testing Requirements
- All code should be tested following Test-Driven Development (TDD) principles.
  - Functions defined in the code should be 100% covered.
  - Branches defined in the code should be 60% covered.
  - Statements defined in the code should be 60% covered.
  - Code that you believe qualifies as untestable should have an inline comment added with the tag `UNTESTABLE`.
  - Code that you believe qualifies as needing a mock should have an inline comment added with the tag `MOCKTHIS`.

### Version Control Standards
- All code should be branch separated.
  - When starting new work, create a branch following BRANCH_PATTERN.
  - Then checkout the branch.
  - Commits must be atomic (one logical change per commit).
  - Follow conventional commit standards for all commit messages.
  - Include detailed commit body with learning notes and challenges.

### Function Development Process
Creating a new function should follow the following steps:
  1. Define the function signature.
  2. Write a static function body, that includes the DEVNOTES and BUSINESSCASE as 

*[truncated — see source for full prompt]*