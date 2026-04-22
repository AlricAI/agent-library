# SCREENSHOTS

> How to capture screenshots using Puppeteer and add them to the Amber blog.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Screenshot Workflow for Blog Posts

How to capture screenshots using Puppeteer and add them to the Amber blog.

## Quick Reference

```bash
# 1. In Claude Code, navigate and capture:
mcp__puppeteer__puppeteer_navigate(url="https://example.com")
mcp__puppeteer__puppeteer_screenshot(name="my-shot", width=800, height=600, encoded=true)

# 2. Note the temp file path from "Output has been saved to..." message

# 3. Extract and save:
node drawer/scripts/capture-screenshot.js /path/to/mcp-result.txt my-screenshot

# 4. Commit and push:
git add web/public/amber/my-screenshot.png
git commit -m "Add screenshot: my-screenshot"
git push origin main

# 5. Reference in blog:
# /amber/my-screenshot.png
```

## The Problem

Puppeteer MCP can take screenshots, but they're returned inline or as base64. We need to:
1. Get the raw image data
2. Save it to `web/public/amber/`
3. Push to GitHub
4. Reference in blog posts

## The Solution

### Step 1: Take Screenshot with `encoded=true`

When taking a screenshot, use the `encoded` parameter:

```
mcp__puppeteer__puppeteer_screenshot(
  name="my-screenshot",
  width=800,
  height=600,
  encoded=true
)
```

This returns a base64 data URI instead of an inline image. Because it's large, Claude Code saves it to a temp file like:
```
/Users/bartdecrem/.claude/projects/.../tool-results/mcp-puppeteer-...-1234567890.txt
```

### Step 2: Extract and Save

Use the extraction script:
```bash
node drawer/scripts/capture-screenshot.js <temp-file-path> <output-name>
```

This:
- Reads the JSON file
- Extracts the base64 data
- Decodes to PNG
- Saves to `web/public/amber/<output-name>.png`

### Step 3: Git Push

```bash
git add web/public/amber/<output-name>.png
git commit -m "Add screenshot: <output-name>"
git push origin main
```

### Step 4: Reference in Blog

In `web/app/amber/data.json`, use the path `/amber/<output-name>.png`:

```json
{
  "images": [
    {
      "url": "/amber/my-screenshot.png",
      "alt": "Description of the screenshot",
   

*[truncated — see source for full prompt]*