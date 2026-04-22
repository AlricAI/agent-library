# AGENTS

> This guide covers writing and running tests for the Keyteki codebase.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Testing Guide

This guide covers writing and running tests for the Keyteki codebase.

## Commands

-   Run all tests: `DEBUG_TEST=1 npm test`
-   Run specific test file: `DEBUG_TEST=1 npm test -- test/server/cards/<Set>/<CardName>.spec.js`
-   Run multiple test files: `DEBUG_TEST=1 npm test -- test/server/cards/<Set1>/<CardName1>.spec.js test/server/cards/<set2>/<CardName2>.spec.js`
-   Run tests matching a pattern: `DEBUG_TEST=1 npm test -- --testNamePattern '<pattern>'`

## Viewing Test Output

**Quick pass/fail check:**

```bash
npm test -- test/server/cards/<Set>/<CardName>.spec.js 2>&1 | tail -5
```

**When tests fail**, don't pipe through `grep` or `tail` - vitest output formatting often breaks when piped. Instead:

-   Run the test without piping to see full output
-   Use `--testNamePattern '<pattern>'` to run only the failing test
-   If output is truncated with "Large tool result written to file", use `read_file` on the output file to see the full results

**DEBUG_TEST=1** produces verbose game logs. Only use it when you need to trace game state, not for checking pass/fail.

## Writing Card Tests

-   Tests should be added to a new `<CardName>.spec.js` file for the card under `test/server/cards/<Set>/<CardName>.spec.js` that corresponds to the card being tested.
    -   Example: [BadOmen.spec.js](server/cards/12-PV/BadOmen.spec.js).
-   New tests should follow the patterns of existing tests, e.g. no imports.
-   Tests should be auto-run after being written, to ensure they pass.
-   If more log data is needed to debug a test, you can set `DEBUG_TEST=1` in the environment before running the test.

## Test Setup Guidelines

-   Test setup in `beforeEach` functions should have a minimal configuration - don't set player aember if its not needed and don't add extra cards that aren't used by tests.
-   When adding cards for tests, be careful that the card's abilities don't interfere with the card being tested. In particular, be aware of elusive, taunt, and abil

*[truncated — see source for full prompt]*