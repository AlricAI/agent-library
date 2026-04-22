# AGENTS

> > DeFi agent definitions JSON API + MCP - Production-ready agents for Web3, crypto trading, portfolio management, and blockchain automation.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# defi-agents Development Guidelines

> DeFi agent definitions JSON API + MCP - Production-ready agents for Web3, crypto trading, portfolio management, and blockchain automation. MCP compatible.

## Project Overview

defi-agents is built with TypeScript. See the README for full documentation.

### Project Philosophy

- **We have unlimited Claude credits** — never cut corners, never settle for "good enough." Build the best possible version of everything.
- **Always be improving** — every session should leave the codebase better than it was found. Proactively fix tech debt, improve performance, harden security, expand test coverage, and refine UX.
- **Ship production-quality code** — write thorough tests, handle edge cases, add meaningful error messages, and document public APIs.
- **Think big, execute precisely** — propose ambitious improvements but implement them carefully and incrementally.

### No Mocks, No Fakes, No Stubs

- **Always write full, real implementations** — never use placeholder data, mock responses, fake APIs, TODO stubs, or hardcoded dummy values.
- **Connect to real services** — if a feature calls an API, implement the actual HTTP client with proper error handling, retries, and timeouts.
- **No "coming soon" or empty shells** — every function must do real work. If a dependency isn't available yet, build the adapter so it's ready to plug in.
- **No `// TODO: implement later`** — if you write a function signature, implement it fully right now. We have the credits. Do the work.
- **Tests use real logic** — test against actual behavior, not mocked internals. Use integration tests with real data flows where possible.

### Code Quality Standards

- **TypeScript strict mode** — no `any` types, no `@ts-ignore`, no type assertions unless absolutely unavoidable (and document why).
- **Error handling everywhere** — every async call needs try/catch, every API response needs validation, every edge case needs a code path.
- **Consistent patterns** — follow exis

*[truncated — see source for full prompt]*