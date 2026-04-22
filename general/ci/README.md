# Ci

> The CI runs on every push to `main` and every pull request.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# CI Pipeline

The CI runs on every push to `main` and every pull request. It uses smart scoping to skip expensive jobs when only unrelated areas changed.

## Job Overview

| Job                      | Purpose                                                                                  | When it runs                        |
| ------------------------ | ---------------------------------------------------------------------------------------- | ----------------------------------- |
| `preflight`              | Detect docs-only changes, changed scopes, changed extensions, and build the CI manifest  | Always on non-draft pushes and PRs  |
| `security-fast`          | Private key detection, workflow audit via `zizmor`, production dependency audit          | Always on non-draft pushes and PRs  |
| `build-artifacts`        | Build `dist/` and the Control UI once, upload reusable artifacts for downstream jobs     | Node-relevant changes               |
| `checks-fast-core`       | Fast Linux correctness lanes such as bundled/plugin-contract/protocol checks             | Node-relevant changes               |
| `checks-fast-extensions` | Aggregate the extension shard lanes after `checks-fast-extensions-shard` completes       | Node-relevant changes               |
| `extension-fast`         | Focused tests for only the changed bundled plugins                                       | When extension changes are detected |
| `check`                  | Main local gate in CI: `pnpm check` plus `pnpm build:strict-smoke`                       | Node-relevant changes               |
| `check-additional`       | Architecture and boundary guards plus the gateway watch regression harness               | Node-relevant changes               |
| `build-smoke`            | Built-CLI smoke tests and startup-memory smoke                                           | Node-relevant changes               |
| `checks`                 | Heavier Linux Node lanes: full tests, channel tests, and pus

*[truncated — see source for full prompt]*