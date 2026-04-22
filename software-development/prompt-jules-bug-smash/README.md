# Prompt Jules Bug Smash

> Please open a new branch named jules-bug-smash and commit all the current code 

then open a session with jules using your mcp tool with a prompt grou

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Please open a new branch named jules-bug-smash and commit all the current code 

then open a session with jules using your mcp tool with a prompt grouping all of the tsc --noEmit and ide problems tab by type and provide instructions for jules to fix 

@current_problems 

backend/src/ai/agents/base/BaseAgent.ts(26,3): error TS2578: Unused '@ts-expect-error' directive.
backend/src/ai/agents/base/BaseAgent.ts(87,24): error TS2722: Cannot invoke an object which is possibly 'undefined'.
backend/src/ai/agents/base/BaseAgent.ts(87,25): error TS2352: Conversion of type 'TEnv' to type 'Record<string, { get?: (() => Promise<string>) | undefined; }>' may be a mistake because neither type sufficiently overlaps with the other. If this was intentional, convert the expression to 'unknown' first.
  Type 'Env' is not comparable to type 'Record<string, { get?: (() => Promise<string>) | undefined; }>'.
    Index signature for type 'string' is missing in type 'Env'.
backend/src/ai/agents/base/BaseAgent.ts(90,24): error TS2722: Cannot invoke an object which is possibly 'undefined'.
backend/src/ai/agents/base/BaseAgent.ts(90,25): error TS2352: Conversion of type 'TEnv' to type 'Record<string, { get?: (() => Promise<string>) | undefined; }>' may be a mistake because neither type sufficiently overlaps with the other. If this was intentional, convert the expression to 'unknown' first.
  Type 'Env' is not comparable to type 'Record<string, { get?: (() => Promise<string>) | undefined; }>'.
    Index signature for type 'string' is missing in type 'Env'.
backend/src/ai/agents/base/BaseAgent.ts(93,24): error TS2722: Cannot invoke an object which is possibly 'undefined'.
backend/src/ai/agents/base/BaseAgent.ts(93,25): error TS2352: Conversion of type 'TEnv' to type 'Record<string, { get?: (() => Promise<string>) | undefined; }>' may be a mistake because neither type sufficiently overlaps with the other. If this was intentional, convert the expression to 'unknown' first.
  Type 'Env' is not compar

*[truncated — see source for full prompt]*