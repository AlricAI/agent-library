# Visual Bug Fix

> ## Purpose
Take a screenshot of a UI issue, analyze it, find the relevant code, fix it, and verify the fix.

## When to Use
- User sends a screenshot 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Visual Bug Fix

## Purpose
Take a screenshot of a UI issue, analyze it, find the relevant code, fix it, and verify the fix.

## When to Use
- User sends a screenshot via Telegram showing a visual/UI issue
- CSS problems, layout issues, missing elements, wrong colors, broken responsive design
- Anything that can be verified visually before and after the fix
- Misaligned components, overflow text, broken images, wrong fonts

## Pre-Task Context Loading
1. Load company profile from vault (e.g., [[companies/dirtsync.md]]) to understand tech stack
2. Load relevant architecture section (key files, component structure, CSS framework)
3. Load known issues list to check if this is already documented
4. Check recent PRs for related UI changes that may have caused the regression

## Required Capabilities
- **Vision** -- must be able to analyze screenshots (rules out Codex)
- **Code editing** -- must be able to read/write files and create PRs
- **Context awareness** -- should load [[agents/skills/codebase-aware.md]] first

## Execution Steps

### Step 1: Analyze Screenshot
- Describe what is visually wrong in the screenshot
- Describe what the expected/correct behavior should be
- Identify the specific UI component(s) affected
- Note the viewport size/device if visible (mobile vs desktop)

### Step 2: Identify Files
- Use architecture knowledge from company profile to find relevant files
- For React/Next.js: look for component files (.tsx), style files (.css/.scss/.module.css), layout files
- For Shopify: look for liquid templates, CSS/SCSS files, theme settings
- Search codebase for component names, class names, or text visible in screenshot

### Step 3: Read the Code
- Read the full component file(s) before making any changes
- Understand the current implementation, styling approach, and any conditional rendering
- Check if the issue is in the component, its parent layout, or a shared style
- Look for recent changes (git log) that might have introduced the bug

### S

*[truncated — see source for full prompt]*