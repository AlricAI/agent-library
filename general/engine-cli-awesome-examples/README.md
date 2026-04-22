# ENGINE CLI AWESOME EXAMPLES

> This companion guide to ENGINE_CLI.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Tandem Engine Awesome Examples

This companion guide to ENGINE_CLI.md focuses on advanced, real-world workflows that showcase tools, streaming, skills, MCP, multi-agent swarms, and planning. All examples assume the engine is running locally.

## Start the Engine

```bash
tandem-engine serve --hostname 127.0.0.1 --port 39731
```

## Tool Discovery (HTTP)

```bash
API="http://127.0.0.1:39731"
curl -s "$API/tool/ids"
curl -s "$API/tool"
```

## Agent and Skill Inventory (HTTP)

```bash
API="http://127.0.0.1:39731"
curl -s "$API/agent"
curl -s "$API/skills"
```

## Example Webpage Chat (HTML + SSE)

Create a local HTML file and serve it with any static server. This page sends messages to the engine and streams SSE events.

```bash
cat > chat.html << 'HTML'
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Tandem Engine Chat</title>
    <style>
      body { font-family: system-ui, sans-serif; margin: 24px; }
      #log { white-space: pre-wrap; border: 1px solid #ddd; padding: 12px; height: 320px; overflow: auto; }
      #row { display: flex; gap: 8px; margin-top: 12px; }
      input { flex: 1; padding: 8px; }
      button { padding: 8px 12px; }
    </style>
  </head>
  <body>
    <h1>Tandem Engine Chat</h1>
    <div id="log"></div>
    <div id="row">
      <input id="prompt" placeholder="Say something..." />
      <button id="send">Send</button>
    </div>
    <script>
      const API = "http://127.0.0.1:39731";
      const log = document.getElementById("log");
      const promptInput = document.getElementById("prompt");
      const sendBtn = document.getElementById("send");

      function append(text) {
        log.textContent += text + "\n";
        log.scrollTop = log.scrollHeight;
      }

      async function createSession() {
        const res = await fetch(API + "/session", {
          method: "POST",
          headers: { "content-type": "application/json"

*[truncated — see source for full prompt]*