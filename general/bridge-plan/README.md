# BRIDGE PLAN

> ## Goal
Connect EVI (voice layer) to the real Amber agent (Claude with drawer context + tools), so talking to Amber on the phone feels like talking to

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Amber Voice Bridge Plan

## Goal
Connect EVI (voice layer) to the real Amber agent (Claude with drawer context + tools), so talking to Amber on the phone feels like talking to the evolving digital person from Claude Code.

## Architecture

```
Phone browser → /voice-chat/amber
    ↓
EVI (speech-to-text)
    ↓
/api/amber-voice (our bridge)
    ↓
Claude API (Opus) + drawer context + tools
    ↓
Response text (streamed)
    ↓
EVI (text-to-speech)
    ↓
You hear Amber
```

## Components to Build

### 1. `/api/amber-voice` endpoint (~150-200 lines)

**Input**: User's transcribed text from EVI
**Output**: Amber's response (streamed)

```typescript
// Core flow:
1. Load drawer context (PERSONA.md, MEMORY.md, LOG.md)
2. Build system prompt with Amber's identity
3. Call Claude API with:
   - System prompt + context
   - Tool definitions
   - User message
   - Conversation history (if multi-turn)
4. Handle tool calls in a loop (Twitter, web search, etc.)
5. Stream final response back to EVI
```

### 2. Tool Definitions

Which tools should Amber have?
- [ ] **Twitter/X API** — fetch and explain posts
- [ ] **Web search** — research topics
- [ ] **File read** — access drawer files, codebase
- [ ] **Code execution** — run scripts (careful with this)

### 3. EVI Configuration

- Create new EVI config that points to our webhook
- Or modify existing SUNDAY config to use custom backend
- Need to check Hume docs for exact webhook setup

### 4. Update `/voice-chat/amber` page

- Use new config ID that routes to our backend
- May need different connection setup for webhook mode

### 5. Session Management (~40 lines)

- Track conversation history within a voice session
- Pass history to each Claude call for multi-turn coherence
- Optionally persist notable exchanges to LOG.md

## Complexity Breakdown

| Component | Lines | Difficulty |
|-----------|-------|------------|
| Basic bridge (no tools) | ~80 | Easy |
| Tool support | +70-120 | Medium |
| Streaming responses | +30 | Easy |
| 

*[truncated — see source for full prompt]*