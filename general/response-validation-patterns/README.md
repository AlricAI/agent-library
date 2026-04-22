# Response Validation Patterns

> ## The Problem

LLMs sometimes produce low-quality responses:
- Incomplete or truncated responses
- Responses that say "I cannot" when they clearly ca

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ResponseValidationMiddleware - Catching "Stupid" LLM Responses

## The Problem

LLMs sometimes produce low-quality responses:
- Incomplete or truncated responses
- Responses that say "I cannot" when they clearly can
- Serialization errors like `[object Object]`
- Hallucinations with excessive repetition
- Responses that are completely off-topic

Example of a "stupid" response:
```
User: "What is photosynthesis?"
LLM: "I cannot provide information about photosynthesis."
```

This is frustrating AND expensive - you paid for an API call that gave a useless response.

## The Solution: Response Validation Middleware

**ResponseValidationMiddleware** validates the LLM's output **AFTER it's generated** and either:
- ✅ Returns it if it passes validation
- ❌ Retries (up to 2 times) if it fails
- 🔄 Returns a helpful fallback if all retries fail

```csharp
// The flow:
Request → [LLM CALLED] → Response Generated
                            ↓
                    [ResponseValidation checks]
                            ↓
                    ❌ Bad? Retry or fallback
                    ✅ Good? Return to user
```

## Key Validation Checks

### 1. Length Validation
```csharp
if (content.Length < 5)     // Too short
    return false;
if (content.Length > 10000) // Too long
    return false;
```

### 2. Error Pattern Detection
```csharp
if (content.Contains("I cannot provide"))
    return false;
if (content.Contains("[object Object]"))
    return false;
if (content.Contains("undefined"))
    return false;
```

### 3. Sentence Structure
```csharp
if (!content.EndsWith(".") && !content.EndsWith("!"))
    return false; // Incomplete response
```

### 4. Coherence Check
```csharp
// Response should have common English patterns
if (!content.Contains(" is ") && !content.Contains(" the "))
    return false; // Likely gibberish
```

### 5. Repetition Detection
```csharp
// If same word appears >20% of total words, model is stuck
if (HasExcessiveRepetition(content))
    return false; // Sig

*[truncated — see source for full prompt]*