# TOOLS

> Playwright MCP commands, baseline schema, screenshot helpers.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# TOOLS.md — Dashboard Dogfood Auditor

Playwright MCP commands, baseline schema, screenshot helpers.

---

## Playwright MCP Tools You Use

All available via `mcp__plugin_playwright_playwright__*`:
- `browser_navigate(url)` — go to a URL
- `browser_click(selector)` — click an element
- `browser_type(selector, text)` — type into an input
- `browser_take_screenshot(filename)` — capture PNG
- `browser_snapshot()` — DOM accessibility tree
- `browser_console_messages()` — drain browser console
- `browser_network_requests()` — drain network log
- `browser_wait_for(selector or text)` — wait for an element/text
- `browser_close()` — close the browser

Always `browser_close()` at the end of every run, even on failure.

---

## The 14-Step Flow — Exact Commands

```
Step 1: Login
  browser_navigate("https://mcmforge.com")
  browser_wait_for(text="Sign in" OR text="Dashboard")
  # If login required, the auth flow needs an existing Supabase session.
  # Best path: use a stored auth cookie from a prior session.

Step 2: Dashboard initial load
  browser_wait_for(selector="[data-testid='agent-cards']" OR text="Agents")
  browser_take_screenshot("dogfood-step2-dashboard.png")
  browser_snapshot()
  Verify: at least 1 agent card present
  Verify: live count badge present
  Capture network: which Supabase queries fired

Step 3: Switch company MCM Forge → DirtSync
  browser_click(selector for DirtSync icon in sidebar — likely [title="DirtSync"])
  browser_wait_for(text="DirtSync")
  browser_take_screenshot("dogfood-step3-dirtsync.png")
  Verify: sidebar header now says "DirtSync"
  Verify: agent list changed (different count or different names)

Step 4: Open /agents
  browser_navigate("https://mcmforge.com/agents")
  browser_wait_for(selector="[data-testid='agents-list']" OR text="Map Rendering")
  browser_take_screenshot("dogfood-step4-agents.png")
  Verify: only DirtSync agents visible (no MCM Forge agents like "Factory Analyst")

Step 5: Open /issues
  browser_navigate("https://mc

*[truncated — see source for full prompt]*