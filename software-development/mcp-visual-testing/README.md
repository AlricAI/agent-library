# MCP VISUAL TESTING

> ## Overview

This project uses the **Playwright MCP Server** instead of traditional Playwright test files for visual verification. This allows AI agen

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Visual Testing with Playwright MCP Server

## Overview

This project uses the **Playwright MCP Server** instead of traditional Playwright test files for visual verification. This allows AI agents (like Claude Code) to directly interact with and verify the running application.

## Why MCP Over Test Files?

**Traditional Playwright Tests:**
- Static test files that need to be written and maintained
- Run in CI/CD pipelines
- Require updates when UI changes
- Limited to predefined test scenarios

**Playwright MCP Server:**
- **Dynamic interaction**: AI agents can explore and verify UI on-the-fly
- **Real-time feedback**: See what you're building as you build it
- **Flexible verification**: No need to write test files for every scenario
- **Faster development**: Verify UI immediately after code changes
- **Better debugging**: Take screenshots and inspect elements interactively

## Setup

The Playwright MCP server is already configured for this project:

```bash
# Configuration was added with:
claude mcp add playwright npx @playwright/mcp@latest
```

No additional setup needed - it's ready to use!

## How to Use

### 1. Start the Development Server

```bash
npm run dev
```

The app runs on http://localhost:5173 (fixed port).

### 2. Use MCP Commands

AI agents can now use Playwright tools directly:

**Navigate to the app:**
```typescript
await browser_navigate({ url: "http://localhost:5173" });
```

**Take screenshots:**
```typescript
await browser_take_screenshot({ filename: "homepage.png" });
```

**Get page structure:**
```typescript
await browser_snapshot();
```

**Interact with elements:**
```typescript
await browser_click({ element: "FAB menu button", ref: "..." });
await browser_type({ element: "Input field", ref: "...", text: "Hello" });
```

**Verify touch targets:**
```typescript
await browser_evaluate({
  function: `() => {
    const button = document.querySelector('.new-button');
    const rect = button.getBoundingClientRect();
    return { width: rect.widt

*[truncated — see source for full prompt]*