# Testing Guide

> This guide shows how AI agents (and developers) can programmatically test and debug changes in this project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Programmatic Testing & Debugging Guide

This guide shows how AI agents (and developers) can programmatically test and debug changes in this project.

## Available Testing Methods

### 1. **Next.js MCP Tools** (Recommended for Next.js projects)

The project has Next.js MCP (Model Context Protocol) tools enabled. These can be used to:

- **Check for errors**: `nextjs_call` with `get_errors` tool
- **List routes**: `nextjs_call` with `get_routes` tool  
- **Get page metadata**: `nextjs_call` with `get_page_metadata` tool
- **Check logs**: `nextjs_call` with `get_logs` tool

**Example Usage:**
```typescript
// Check for compilation/runtime errors
mcp_next-devtools_nextjs_call({
  port: "3000",
  toolName: "get_errors"
})

// List all routes
mcp_next-devtools_nextjs_call({
  port: "3000", 
  toolName: "get_routes"
})
```

### 2. **API Testing via Terminal Commands**

Test API endpoints directly using `curl` or `fetch`:

```bash
# Test sync endpoint
curl -X POST http://localhost:3000/api/crm/sync \
  -H "Content-Type: application/json" \
  -w "\nHTTP Status: %{http_code}\n"

# Test with authentication (if needed)
curl -X POST http://localhost:3000/api/crm/sync \
  -H "Content-Type: application/json" \
  -H "Cookie: your-session-cookie" \
  -w "\nHTTP Status: %{http_code}\n"
```

**Or use the test script:**
```bash
bun scripts/test-sync-api.ts
```

### 3. **Browser Automation** (UI Testing)

Use Playwright browser automation to test UI interactions:

```typescript
// Start browser
mcp_next-devtools_browser_eval({
  action: "start",
  headless: true
})

// Navigate to page
mcp_next-devtools_browser_eval({
  action: "navigate",
  url: "http://localhost:3000/dashboard/crm/contacts"
})

// Click sync button
mcp_next-devtools_browser_eval({
  action: "click",
  element: "Sync Now button",
  ref: "button-ref-from-snapshot"
})

// Check console messages
mcp_next-devtools_browser_eval({
  action: "console_messages",
  errorsOnly: true
})
```

**Note**: Requires Playwright instal

*[truncated — see source for full prompt]*