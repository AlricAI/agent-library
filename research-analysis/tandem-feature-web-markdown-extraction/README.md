# Tandem Feature Web Markdown Extraction

> **Owner:** Tandem Engine  
**Status:** Feature request (TODO)  
**Priority:** High (quality + cost + UX win for research/tools)  
**Motivation:** Repl

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Feature Request: Agent-Ready Web Markdown Extraction (Local, Rust)

**Owner:** Tandem Engine  
**Status:** Feature request (TODO)  
**Priority:** High (quality + cost + UX win for research/tools)  
**Motivation:** Replace â€œHTML soupâ€ with clean, structured Markdown for agents, without relying on Cloudflareâ€™s paid Markdown-for-Agents feature.

---

## Problem

When agents fetch web pages today, they often receive:
- heavy HTML (nav, ads, cookie banners, scripts)
- low-signal content that wastes tokens
- inconsistent structure that hurts extraction/summarization

Cloudflare offers â€œMarkdown for Agentsâ€ but itâ€™s gated behind Pro/Business plans. We want the same (or better) capability built into **tandem-engine** as a **proprietary/local-first** feature that works on **any site**.

---

## Current Tandem Reality (Web Fetch)

The existing `webfetch` tool in **tandem-tools** is a thin HTTP GET:
- Direct `reqwest::get(url)` with no custom timeouts, no size caps, no SSRF protections, and no redirect policy.
- No content-type detection or HTML cleanup; it returns raw response text.
- Return shape today: `ToolResult { output: <string>, metadata: { truncated: boolean } }` with **20,000 chars max**.
- No Markdown conversion, no main-content extraction, no metadata (title/canonical/links).

Separately, `websearch` uses an MCP endpoint (Exa), but **webfetch is not MCP-backed** yet.

Implication: the new feature must either (a) replace the current `webfetch` implementation, or (b) add a new tool that returns a structured `WebDocument` and update tool selection and permissions accordingly.

---

## Goals

1. Convert arbitrary HTML pages into clean Markdown suitable for LLM consumption.
2. Extract main content (article/docs) and drop boilerplate (nav/footers/sidebars).
3. Return both:
   - `markdown` (structured: headings, lists, code blocks)
   - `text` (plain, compact fallback)
4. Provide stable metadata for citations and follow-up fetches:
   - title
   - canonical 

*[truncated — see source for full prompt]*