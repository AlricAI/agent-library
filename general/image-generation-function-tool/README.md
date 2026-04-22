# Image Generation Function Tool

> ## Overview

Add `GenerateImages` as an AI function tool to enable natural language image generation during chat sessions, complementing the existing 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Image Generation as AI Function Tool

## Overview

Add `GenerateImages` as an AI function tool to enable natural language image generation during chat sessions, complementing the existing `cycod imagine` CLI command.

## Current State

- `cycod imagine "prompt"` - CLI command for explicit image generation
- `--image FILE` / `/image FILE` - Add existing images to conversation (input)
- No way to generate images naturally during chat without exiting

## Proposed Solution

Implement `GenerateImages` as a function tool that AI can invoke during conversation.

### User Experience

**Instead of:**
```bash
# Exit chat or use complex slash command
cycod imagine "weather app icon" --count 3 --size 1024x1024
```

**Natural conversation:**
```
User: Can you create me three weather app icons? Make them minimalist and blue.

AI: I'll generate three weather app icons for you.
[Function call: GenerateImages approved]
✓ Generated weather-icon-20250113-143022-1.png
✓ Generated weather-icon-20250113-143022-2.png  
✓ Generated weather-icon-20250113-143022-3.png

I've created three minimalist blue weather app icons...
```

## Benefits

1. **More Natural** - Users describe intent, AI handles implementation
2. **Better Iteration** - Conversational refinement workflow
   - "Create a logo" → "Make it more vintage" → "Add warm colors"
3. **AI Value-Add** - Prompt engineering, smart defaults, context awareness
4. **Consistent** - Matches existing function tool patterns
5. **Flexible** - CLI command remains for scripting/batch operations

## Function Tool Design

### Schema

```typescript
{
  name: "GenerateImages",
  description: "Generate images from text descriptions using AI (DALL-E)",
  parameters: {
    prompt: {
      type: "string",
      description: "Detailed image description. Be specific about style, colors, composition.",
      required: true
    },
    count: {
      type: "integer", 
      description: "Number of variations (1-10)",
      default: 1
    },
    size: {
      t

*[truncated — see source for full prompt]*