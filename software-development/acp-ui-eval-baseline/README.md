# ACP UI EVAL BASELINE

> This document defines the base guarantees for the shared ACP UI kernel and how they are verified across the three ACP hosts:

- VS Code extension
- br

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ACP UI Canonical Eval Baseline

This document defines the base guarantees for the shared ACP UI kernel and how they are verified across the three ACP hosts:

- VS Code extension
- browser `acp-chat`
- `copilot /agents`

## Scope

The goal is not to prove every host-specific feature in one suite. The goal is to keep one checked-in baseline for:

- shared-kernel guarantees
- host-specific guarantees
- cross-host conformance

## Shared-Kernel Guarantees

These checks validate package-level ACP UI behavior that must stay stable regardless of host:

- tool visibility window shows the latest five regular tools by default
- `Show more` / `Show less` state is explicit and testable
- tool display-name normalization stays deterministic
- ACP host bridge accepts the aggregate host-port contract
- legacy VS Code bridge shape is normalized into the aggregate host-port contract

Command:

```bash
npm run test:webview:unit
```

Current source tests:

- `packages/acp-ui/src/hostBridge.test.ts`
- `packages/acp-ui/src/components/tools/toolListVisibility.test.ts`
- `packages/acp-ui/src/lib/toolTitle.test.ts`

## Shared Runtime / Settings Guarantees

These checks validate shared ACP runtime utilities reused by the extension host and the Copilot ACP backend:

- `agent_servers` / `acp.agents` merge order
- workspace settings override global settings for scalar values
- built-in and custom agents are unioned with deterministic override semantics
- attachment/content block transforms remain stable
- ACP session-update mapping to UI events remains stable

Command:

```bash
npm run test:runtime:unit
```

Current source test:

- `packages/acp-runtime-shared/index.test.js`

## VS Code Host Guarantees

These checks validate the extension-host integration path:

- extension host compiles against the shared package
- webview bundle builds from package consumption
- extension host tests still pass

Commands:

```bash
npm run build:webview
npm test
```

Relevant sources:

- `src/views/webview/src

*[truncated — see source for full prompt]*