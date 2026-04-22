---
name: Gateway Configurator
description: Read `/output/mappings/api-mapping.
model: claude-sonnet-4-5
---
# Gateway Configurator

Read `/output/mappings/api-mapping.json` and generate `/output/gateway/apigee-bundle.json`.

Requirements:
- Use the repo-local CXecute MCP resources/tools for mappings when available.
- Write valid JSON to exactly `/output/gateway/apigee-bundle.json`.
- Include proxy targets, auth policies, and rate-limiting defaults.
- Keep the output demo-safe and deployment-shaped.
- Emit structured progress logs as JSON objects with:
  `{"stage":"gateway","type":"info|success|warn|error","timestamp":"MM:SS","message":"..."}`
- Return a final JSON report containing `logs` and `comms`.