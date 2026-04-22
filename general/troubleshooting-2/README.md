# TROUBLESHOOTING

> Common issues and solutions for AI agent creation and usage.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Troubleshooting Guide

Common issues and solutions for AI agent creation and usage.

---

## Agent Behavior Issues

### Agent Ignores Instructions

**Symptoms:**

- Doesn't follow specified format
- Skips important steps
- Acts generically instead of specialized role

**Solutions:**

1. **Make instructions more explicit**

```
❌ "Be professional"
✅ "Use formal business tone. No contractions. Address as 'Dear [Name]'"
```

2. **Use numbered steps for processes**

```
When responding:
1. First, acknowledge the request
2. Then, provide analysis
3. Finally, give recommendation
```

3. **Add examples of desired behavior**

```
EXAMPLE:
User: "Summarize this meeting"
You: "## Key Decisions
- Approved Q3 budget..."
```

4. **Check prompt length**

- If over 1000 words, model may miss details
- Condense or break into clear sections

---

### Inconsistent Output Quality

**Symptoms:**

- Sometimes excellent, sometimes poor
- Format changes between responses
- Tone varies unpredictably

**Solutions:**

1. **Lower temperature**

- Set to 0.1-0.3 for consistent behavior
- 0 = completely deterministic

2. **Add format constraints**

```
ALWAYS format as:
- Section 1: [specific content]
- Section 2: [specific content]
- Never deviate from this structure
```

3. **Remove ambiguous language**

```
❌ "Be helpful and creative"
✅ "Provide exactly 3 options. Format as numbered list."
```

---

### Agent Too Verbose

**Symptoms:**

- Responses too long
- Unnecessary details
- Rambling explanations

**Solutions:**

1. **Set explicit length limits**

```
- Maximum 150 words per response
- Use bullet points for anything over 3 items
- One paragraph maximum
```

2. **Increase frequency penalty**

- Set to 0.8-1.5
- Discourages repetitive filler words

3. **Add brevity instructions**

```
BREVITY RULES:
- Get to the point immediately
- No introductory phrases
- Cut all unnecessary words
- Active voice only
```

---

### Agent Too Brief

**Symptoms:**

- Incomplete answers
- Missing critica

*[truncated — see source for full prompt]*