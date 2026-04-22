# SUMMARY

> ## Files & Roles
- server/app.js: Express app creation, middleware, and route mounting.
- server/index.js: Server entry that binds to a port for manua

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Summary: QTests MERN Demo

## Files & Roles
- server/app.js: Express app creation, middleware, and route mounting.
- server/index.js: Server entry that binds to a port for manual runs.
- server/routes/hello.js: Route `GET /api/hello` calling external service wrapper.
- server/services/externalService.js: Wraps axios call; logs via winston (stubbed in tests).
- client/src/App.jsx: Minimal React component placeholder.
- config/jest.config.mjs: Jest config for demo aligned with qtests runner policies.
- config/jest-require-polyfill.cjs: Ensures `require` is available in ESM contexts.
- config/jest-setup.js: After-env setup; defensive `require` polyfill.
- tests/hello.route.test.js: Integration-ish test against Express route using supertest.
- tests/axios-winston-stubs.test.js: Verifies built-in stubs for axios and winston.

## Request/Response Flows
- Client → Server: (not exercised in CI) would call `/api/hello`.
- Tests → App: supertest issues `GET /api/hello` against in-memory app.
- App → External: `externalService.fetchHello()` calls axios; qtests stubs intercept and return a truthy object.

## Known Side Effects
- Logging via winston is a no-op under qtests, preventing console pollution.
- The axios stub returns `{}`; route checks truthiness only.

## Edge Cases & Caveats
- No bundler is configured for the client; frontend is illustrative only.
- Jest environment is `node`; DOM tests are intentionally omitted to keep dependencies lean.

## AI-Anchors
// 🚩AI: ENTRY_POINT_FOR_QTESTS_DEMO_TESTS
// 🚩AI: MUST_UPDATE_IF_QTESTS_RUNNER_POLICIES_CHANGE