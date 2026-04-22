# Summary

> ## Files
- utils/customStubs.ts: Layered Module._load hook allowing ad‑hoc, in‑memory module stubs without modifying core setup. Exports `registerModu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Summary: utils

## Files
- utils/customStubs.ts: Layered Module._load hook allowing ad‑hoc, in‑memory module stubs without modifying core setup. Exports `registerModuleStub`, `unregisterModuleStub`, `listModuleStubs`, `clearAllModuleStubs`.

- utils/stubMethod.ts: Core method stubbing functionality with restoration capabilities. Provides advanced stubbing scenarios including context preservation, performance measurement, and chained calls.

- utils/mockConsole.ts: Console mocking with Jest-compatible spies and fallback for vanilla Node.js. Supports multiple console methods and call tracking.

- utils/httpTest.ts: HTTP testing utilities providing Express app mocking and supertest-like interface. Minimal dependency implementation with `.send()` support and request body handling.

- utils/runTestSuite.ts: Lightweight test runner for executing test suites without external dependencies. Provides assertion methods and test result reporting.

- utils/testHelpers.js: Comprehensive test utilities including environment management, mock creation, and test isolation helpers.

## Testing Subdirectories

### testing/
- Performance testing utilities and benchmarks
- Scalability testing frameworks
- Load testing patterns and reporting

### testEnv/
- Environment variable management for tests
- Test isolation and cleanup utilities
- Configuration management for different test scenarios

### helpers/
- Validation utilities for test data
- Environment management helpers
- Module reloading and cleanup functions
- Error handling and logging utilities

## Request/Response Flows
- Tests import `setup.js` first to activate core axios/winston stubs.
- Tests import `utils/customStubs.js` and call `registerModuleStub(id, exports|factory)`.
- When `require(id)` is called, the layered loader returns the provided exports object; otherwise, it delegates to the previous loader (preserving core behavior).

## Known Side Effects
- Patches `Module._load` once; additive to the core patch done by `se

*[truncated — see source for full prompt]*