# City Launch Deep Research Harness 2026 04 11

> Date: 2026-04-11

Status: Active

## Purpose

Use Gemini Deep Research as the required upstream planning engine for city-launch planning work in `Blue

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# City Launch Deep Research Harness

Date: 2026-04-11

Status: Active

## Purpose

Use Gemini Deep Research as the required upstream planning engine for city-launch planning work in `Blueprint-WebApp`.

This harness exists because city launch planning for Blueprint is not a lightweight memo-writing task. It requires:

- long-form comparative research
- city-specific supply and demand analysis
- critique of weak analogies or unsupported assumptions
- synthesis into an operator-ready playbook that humans and agents can execute

## Current Google API Rules

This design follows Google's current docs:

- Gemini Deep Research is available only through the Interactions API and not `generateContent`
- Deep Research is powered by Gemini 3.1 Pro
- Deep Research must run with `background=true`
- follow-up questions should use `previous_interaction_id`
- Deep Research currently does not support custom function-calling tools or structured outputs

Those constraints mean the correct Blueprint pattern is:

1. Deep Research pass for broad evidence gathering
2. Gemini 3.1 Pro critique pass for gap finding
3. Deep Research follow-up pass to resolve critique gaps
4. Gemini 3.1 Pro synthesis pass for the final playbook

## Command

Run a full city playbook pass:

```bash
npm run city-launch:plan -- --city "Austin, TX"
```

Useful flags:

- `--critique-rounds 2`
- `--region "Texas"`
- `--similar-companies "Uber,DoorDash,Instacart,Airbnb,Lime"`
- `--file-search-store "fileSearchStores/blueprint-city-launch"`
- `--poll-interval-ms 10000`
- `--timeout-ms 1200000`

Optional internal grounding:

- By default Deep Research uses public-web tools only.
- To add a small curated Blueprint document store, pass `--file-search-store`.
- The value may be a single File Search store name or a comma-separated list of store names.
- Keep this narrow and curated. Do not index the whole repo by default.
- You can also set `BLUEPRINT_CITY_LAUNCH_FILE_SEARCH_STORE` to make a default store automatic for `city

*[truncated — see source for full prompt]*