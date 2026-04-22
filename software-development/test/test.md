---
name: Test
description: Run tests and fix failures
model: claude-sonnet-4-5
---
Use the test-runner agent to execute tests $ARGUMENTS. If no arguments provided, run all tests. Automatically detect the test framework, analyze any failures, and implement fixes while preserving test intent.